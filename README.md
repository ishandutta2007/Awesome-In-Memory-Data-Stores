# Awesome-In-Memory-Data-Stores

## Top In-Memory Data Stores Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Distributed Caching, Data Grids & Self-Hosted Key-Value Stores*  

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **In-Memory Data Stores**. These systems keep data in RAM rather than on disk, delivering microsecond-to-millisecond latency for caching, session storage, real-time analytics, and high-throughput applications where disk I/O would be the bottleneck.



**Examples** include Redis, Memcached, Hazelcast, Apache Ignite, Oracle Coherence, and Aerospike (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, avoiding managed-service premiums, and retaining full control over data residency and eviction behavior. The open-source landscape is anchored by **Redis** (the data structure server standard, now under a tri-license model), **Memcached** (the minimalist multi-threaded cache), **Hazelcast** (the JVM data grid with embedded mode), **Apache Ignite** (the in-memory database with SQL and persistence), and **Oracle Coherence** (the enterprise grid now with a Community Edition), with **Valkey** emerging as the BSD-licensed Redis fork and **Aerospike** serving high-throughput use cases.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [Sector Overview & Market Dynamics](#sector-overview--market-dynamics)
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)



## Sector Overview & Market Dynamics

The global in-memory database and computing market is estimated at approximately $7.6B to $10B+ in 2024 and projected to reach $30B to $48B+ by the early 2030s (growing at a ~14%–19% CAGR). The market is moderately fragmented overall—anchored at the top by enterprise incumbents (AWS, SAP, Oracle, Microsoft) who capture massive workloads through cloud and ERP bundling, while remaining dynamically fragmented across specialized low-latency caching vendors, in-memory data grids, and open-source ecosystems (Redis, Valkey, Hazelcast, Apache Ignite/GridGain).



## SaaS/Hosted Platforms

| Platform | Company Size (Valuation / Revenue) | Pricing (Starting Tier) | Free Tier Limits | Key Highlights |
| :--- | :--- | :--- | :--- | :--- |
| **[Amazon ElastiCache](https://aws.amazon.com/elasticache/)** | **~$2.3T+ Market Cap** (Amazon) / AWS ~$108B annual revenue (2024) | Starts at **$0.017/hour** (~$12.41/month) for `cache.t3.micro` on-demand (Valkey/Redis/Memcached); Serverless from ~$0.006/GB-hour | **12-Month Free Tier**: 750 hours/month of `cache.t3.micro` or `cache.t2.micro` node usage + 15 GiB data transfer out (for accounts created before July 15, 2025) OR **$100 AWS Free Tier credits** (for newer accounts, applicable to Serverless/instances). | Fully managed Redis, Valkey, and Memcached service natively integrated into AWS VPCs with automatic failover and serverless auto-scaling. |
| **[Redis Enterprise (Redis Cloud)](https://redis.io/cloud/)** | **~$2.0B Valuation** / ~$200M+ ARR | **Essentials plan starts at $5/month** (250 MB storage, 1,000 ops/sec, 256 connections); Dedicated Pro starts at $200/month | **Forever Free Plan**: 1 database, up to **30 MB memory**, 100 ops/sec max throughput, 30 concurrent connections, and 5 GB/month total network bandwidth (no HA/clustering). | Fully managed Redis with Active-Active geo-distribution, 99.999% SLA uptime, Redis Stack data models, and enterprise support. |
| **[Hazelcast Cloud](https://cloud.hazelcast.com/)** | **~$100M–$250M Valuation** (~$66.7M total funding) / ~$10M–$50M ARR | **Pay-as-you-go Serverless** starting per GiB-hour consumed (~$0.10/GiB-hour meter); Dedicated clusters via custom commitments | **Free-for-life Sandbox**: Development cluster capped at **0.5 GiB (512 MiB) storage**, 1 single member (no HA/persistence/backups, cluster auto-pauses after inactivity), plus a **14-day fully featured Cloud trial**. | Managed in-memory computing and distributed streaming platform (Jet engine + IMDG) for low-latency compute and near-cache JVM applications. |
| **[GridGain (Nebula)](https://www.gridgain.com/)** | **~$25M–$50M Historical Valuation** (~$33M–$55M total funding; acquired by MariaDB in 2026) / ~$10M–$50M ARR | **Managed Clusters start at $1.98/hour** (Size S: AWS `r5.xlarge`, 4 vCPU, 30.5 GB RAM, 16 GB off-heap, 400 GB SSD); Attached monitoring starts at $0.11/node/hour | **30-Day Free Trial**: Fully functional evaluation license key for GridGain Enterprise/Nebula platform features (no permanent free cloud tier). | Commercial in-memory data grid and database powered by Apache Ignite, featuring ANSI-99 SQL, distributed ACID transactions, and continuous replication. |



## Open-Source GitHub Projects



- **[Redis](https://github.com/redis/redis)**  

  **The data structure server standard.** Not just a cache—strings, lists, sets, sorted sets, hashes, streams, bitmaps, and HyperLogLog . **Licensing caveat**: Redis 8 is dual/tri-licensed under RSALv2, SSPLv1, and AGPLv3—not OSI-approved open-source. **Valkey** is the BSD-licensed Linux Foundation fork of Redis 7.2 for those requiring true open-source licensing . **Strengths**: richest data model, persistence options (RDB/AOF), replication, Sentinel/Cluster, and clients in every language. **Trade-offs**: single-threaded command execution (though I/O threading helps); memory-bound. Best for caching, sessions, queues, leaderboards, and any workload needing more than simple key-value.



- **[Memcached](https://github.com/memcached/memcached)**  

  **The minimalist multi-threaded cache.** Deliberately simple: key-value storage, eviction, and protocol handling—nothing more . **Architecture**: multi-threaded (scales with CPU cores), client-side sharding (servers don't coordinate), no persistence, no replication . **Performance**: slightly faster than Redis for simple GET/SET due to multi-threading; sub-millisecond latency . **Trade-offs**: no data structures beyond strings/blobs, no persistence, no built-in HA—clients handle failover and sharding. Best for pure caching where simplicity and raw throughput matter more than features.



- **[Hazelcast](https://github.com/hazelcast/hazelcast)**  

  **The JVM data grid.** **Two topologies**: embedded (each app instance starts a member, clustering automatically) or client/server . **Data partitioned across 271 partitions** by default, with backups for resilience . **Features**: distributed Map, Near Cache (client-side subset), Set, MultiMap, Queue, Topic, FlakeIdGenerator, PNCounter, and CP Subsystem (FencedLock, Semaphore, AtomicLong) . **Jet engine** adds stream processing and SQL over maps . **Licensing**: Community Edition under Apache 2.0 + Hazelcast Community License; Enterprise adds disk persistence and WAN replication. **Note**: from 5.4, patch releases go only to Enterprise customers . Best for JVM applications that want computation next to data (entry processors, jobs) without network hops.



- **[Apache Ignite](https://github.com/apache/ignite)**  

  **The in-memory database, not just a cache.** **Apache 2.0** throughout . **Features**: distributed ACID transactions (Serializable isolation), ANSI-99 SQL via JDBC/ODBC, Compute API for running JVM code across the cluster, schema-driven architecture, and pluggable storage engines (in-memory and RocksDB) . **Persistence**: optional native persistence keeps all data on disk while serving from memory. **Trade-offs**: heavier and more complex than Hazelcast or Redis; JVM-based. Best for applications that need a database-like experience (SQL, transactions, persistence) with in-memory speed.



- **[Valkey](https://github.com/valkey-io/valkey)**  

  **The BSD-licensed Redis fork.** Linux Foundation-backed fork of Redis 7.2, created after Redis changed its license. **BSD-3-Clause** licensed . API-compatible with Redis 7.2; drop-in replacement for most workloads. Best for teams that want Redis compatibility with OSI-approved open-source licensing.



- **[Oracle Coherence Community Edition](https://github.com/oracle/coherence)**  

  **The enterprise grid, now with a free edition.** **UPL v1.0** licensed. Features: distributed Maps, persistent maps (local file system persistence), distributed state snapshots, lossy redundancy, single management view via JMX/REST, non-cluster access via proxies for C++/Go/JavaScript/.NET/Python, and Kubernetes operator . Best for Java enterprises that want a proven data grid with Oracle backing and a free community tier.



### Additional Strong Open-Source Options



- **Aerospike Community Edition** — High-throughput key-value store with indexes in memory and data on disk (hybrid architecture). Used at scale for UTXO sets and similar workloads . Best for extreme throughput with larger-than-memory datasets.

- **GigaSpaces XAP** — Distributed in-memory data grid with space-based architecture . Best for Java environments needing a mature grid with commercial support options.

- **Frameworks for building custom systems**: Use **Redis/Valkey** as the default for caching, sessions, and data structures. Use **Memcached** when you need pure multi-threaded caching with minimal features. Choose **Hazelcast** for JVM apps wanting embedded data grid with computation near data. Choose **Apache Ignite** when you need SQL, ACID transactions, and optional persistence alongside in-memory speed. Choose **Coherence** for Oracle-aligned enterprises. For extreme throughput, evaluate **Aerospike**.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- **"Open-source" is nuanced in this category**: Redis 8 is under RSALv2/SSPLv1/AGPLv3 (not OSI-approved); Valkey is BSD. Hazelcast Community is Apache 2.0 + Hazelcast Community License with patch releases gated to Enterprise. Apache Ignite and Coherence CE are fully permissive . Verify licensing before committing.

- **Memcached is not a database**: no persistence, no replication, no built-in HA—clients handle sharding and failover . Do not use it for data you cannot afford to lose.

- **Data grid vs cache distinction**: Hazelcast and Ignite are data grids (computation + storage + clustering); Memcached and Redis are primarily caches (with Redis adding persistence and data structures). Match the tool to your architecture, not just latency requirements.



---



**Made for backend engineers, platform teams, and architects building low-latency systems.**  

Let's make in-memory data stores more open, appropriately licensed, and understandable.
