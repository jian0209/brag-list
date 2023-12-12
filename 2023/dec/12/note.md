# China Launches World's 'Most Advanced' Nuclear Reactor That's Cooled By Gas, Not Water

[Reference from tldr](https://www.independent.co.uk/tech/china-nuclear-reactor-gas-water-b2459952.html)

- Unlike conventional power plants that use pressurised water.
- The power plant build in China Shandong province generates from two high-temperature reactors that are cooled by gas rather than water.
- Nuclear fission reactors typically generate power by breaking atoms and using the energy released to produce steam that runs turbines.
- Gas cooled reactors are more efficient and cost effective electricity than water cooled reactors.

# 9 Steps To Platform Engineering Hell

[Reference from tldr](https://platformengineering.org/blog/9-steps-to-platform-engineering-hell)

- Step 1: You rename your (Dev)Ops team to platform team but still do TicketOps
  - Build an IDP(Internal Developer Platform).
  - [Gartner's hype cycle platform](https://www.gartner.com/en)
  - Flooded with tickets and Slack messages.
- Step 2: No mindset shift to platform as a product(paap)
  - Platform team works with a DevOps mindset, continues write ci/cd pipelines and automation for individual product teams.
  - Too many requests from developers. (Not enough time to process all requests)
- Step 3: Your platform team build a platform for Ops, NOT FOR DEVELOPERS
  - Think hard about the biggest Ops issues.
  - Start designing a platform to fix all those annoying issues.
  - Developers don't care about Ops issues.
  - The annoying issues only solve the problems for Ops, not for developers.
- Step 4: You replace old tech with new stuff for no reason
  - Platform engineer start building and leveraging all the latest tech.
  - Replace Jenkins with Github Actions, existing VMs with Kubernates, introduce Terraform, and later replace it with Crossplane.
  - The platform team will keep the cost rising, and productivity continues to suffer.
- Step 5: You think your setup needs to be special
  - Every team has unique needs, custom workflows.
  - At the end, the platform deploying to a highly customized, self-managed.
- Step 6: You build a portal developers never asked for
  - Someone in the platform team head that developer self-service and portals are the new hotness to solve the problem.
  - Devices to put a portal on top of your existing infrastructure mess, without discussing with developers.
  - "Build it, and they will come" attitude.
- Step 7: New platform engineering silos pop up everywhere
  - Get all the things become worse.
  - End up with five platforms for five teams, most of which dont work well.
- Step 8: You try to hide sunk costs
  - Business leaders and unit heads are getting nervous with lots of sunken costs and nowhere to hide.
  - The truth at this stage is that most of the platform(s) are not working well.
  - Is does not scale, and simply not working.
- Step 9: You get fired
  - Do know is that none of these options are a great way top end.

## !!! Avoid those steps

# Starting The Platform Engineering Journey with Backstage

[Reference from tldr](https://www.cncf.io/blog/2023/12/07/starting-the-platform-engineering-journey-with-backstage)

- Backstage aims to enhance the developer experience significantly by providing a central place for developers to discover and use services.
- What is an internal developer portal(IDP)?
  - Is a website or web application that provides information and tools to developers.
  - Platform engineering focuses on empowering developers to build or deploy software faster.
  - IDPs are essential tools for achieving the platform engineering goal.
  - Provide a single place for developers to access all of the resources they need.
- The need for internal developer portals
  - Developments usually face problems with traditional IT processes.
    - Lack of documentation.
    - Lack of navigating to multiple dashboards.
    - etc...
  - Lack of centralized tool lead to confusion, wasted time, and a higher chance of errors.
  - IDPs help to solve the problem with streamline process, providing acentralized place.
  - Bridge the gaps between developers and technology, reducing friction and enhancing overall efficiency.
  - Streamlined accessibility
    - As the number of APIs, services increases, developers need a centralized place to access all of them.
    - Searchable, easily accessible, and well-organized.
  - Effective documentation
    - Clear and concise documentation is essential for developers to understand how to use a service.
    - API integration, product development, etc...
  - Enhanced collaboration
  - Accelerated development
- What is Backstage?
  - An open-source platform that aims to serve as an IDP and streamline the developer experience.
  - Key features
    - Software Catalog
      - One of the foundational features of Backstage.
      - Acts as a centralized repository with comprehensive overview of all the services.
    - Software Templates
    - CI/CD Integration
    - Document Management
    - Analytics and Metrics

### Backstage is the IDP

# Github Upgrading to MySQL8.0 Blog

[Reference from tldr](https://github.blog/2023-12-07-upgrading-github-com-to-mysql-8-0)

### This is the story of how github upgraded fleet of 1200+ MySQL hosts to 8.0.

#### Motivation for upgrading

- MySQL 5.7 nearing end of life.
- Github team wanted to get a latest version that gets latest security patches, bug fixed, and performance.
- New features from 8.0, such as Instant DDLs, invisible indexes, and compressed bin logs.

#### Github's MySQL infrastructure

- Github fleet consists of 1200+ hosts.
- 300+ TB of data and serve 5.5 million queries per second across 50+ database clusters.
- Each cluster is configured for high availability with a privary plus replicas cluster setup.
- Data is partitioned.
- Github's team leverage both horizontal and vertical to scale MySQL clusters.
- MySQL clusters that store data for specific product-domain arears.
- Large ecosystem of tools.

#### Preparing the journey

- Must be able to upgrade each MySQL database while adhering to Service Level Objectives(SLOs) and Service Level Agreements(SLAs).
- Unable to account for all failure modes in their testing and validation stages. They needed to be able to roll back to the previous version of MySQL without a disruptioin of service if needed.
- To reduce risk, they needed to upgrade each database cluster atomically and schedule around other major changes.

Preparation for the upgrade started in July 2022.

#### Prepare infrastructure for upgrade

- Determine appropriate default values for MySQL 8.0 and perform some baseline performance testing is needed.
- Operate 2 versions of MySQL, their tooling and automation needed to be able to handle both versions.
- The different, or deprecated syntax between MySQL 5.7 and 8.0.

#### Ensure application compatibility

- Added MySQL 8.0 to CI for all applications using MySQL.
- Ran different version of MySQL side-by-side in CI to ensure that there were no regressions during the prolonged upgrade process.
- Detected a variety of bugs and incompatibilities in CI, this helped them remove any unsupported configurations or features and escape any new reserved keywords.
- To help application developer transition towards MySQL 8.0, they enabled an option to select 8.0 prebuilt container in GitHub Codespaces for debugging.
- Provided 8.0 development clusters for additional pre-prod testing.

#### Upgrading plan

- Step 1: Rolling replica upgrades
  - Started with upgrading a single replica and monitoring while the replica was offline to ensure basic function was stable.
  - Enabled production traffic and continued to monitor for query latency, system metrics and application metrics.
  - Brought 8.0 replicas online until we upgraded an entire data center and then iterated through other data centers.
  - Left enough 5.7 replicas online in order to rollback.
  - Disabled production traffic to start serving all read traffic through 8.0 servers.
  - (Replica upgrade)
    - In-place upgrade one replica
    - Enable one replica for traffic
    - Provision more 8.0 replicas
    - Enable all 8.0 replicas for traffic (in same Data Center)
    - Disable all 5.7 replicas (in same Data Center)
    - Add 8.0 replica and disable 5.7 in rest of Data Centers
  - The Replica upgrade strategy involved gradual rollouts in each data center.
- Step 2: Update replication topology
  - Once all the read-only traffic was being served via 8.0 replicas, they adjusted the replication topology:
    - 8.0 primary candidate was configured to replicate directly under the current 5.7 primary.
    - Two replication chains were created downstream of that 8.0 replica:
      - A set of 5.7 replicas (not serving traffic, but ready in case of rollback).
      - A set of 8.0 replicas (serving traffic).
    - The topology was only in this state for a short period of time (hours at most) until they moved to the next step.
    - ![topology image](https://github.blog/wp-content/uploads/2023/12/image3-1.png?w=928&resize=928%2C752)
    - To facilitate the upgrade, the topology was updated to have 2 replication chains.
- Step 3: Promote MySQL 8.0 host to primary
  - Not to do direct upgrades on the primary database host.
  - Instead, they would promote a 8.0 replica to primary through a graceful failover performed with [Orchestrator](https://github.com/openark/orchestrator).
  - Replication topology consisted of an 8.0 primary with two replication chains attached to it: an offline set of 5.7 replicas in case of rollback and a serving set of 8.0 replicas.
  - ![Primary Upgrade](https://github.blog/wp-content/uploads/2023/12/image1-1.png?w=1982)
  - Primary failover and additional steps to finalize MySQL 8.0 upgrade for a database.
- Step 4: Internal facing instance types upgraded
  - Have ancillary servers for backups or non-production workloads.
- Step 5: Cleanup
  - Once confirmed that cluster no need to rollback, they removed the 5.7 replicas and the 5.7 primary.
  - Validation consisted of at least one complete 24 hour traffic cycle to ensure no issues during peak traffic.

#### Ability to rollback

- Ensured enough 5.7 replicas were online to rollback to serve production traffic load, or 8.0 replicas were not performing well.
- In order to roll back without data loss or service disruption, they needed to be able to maintain backwards data replication between both versions of MySQL.
- Need to know, MySQL support replication to the next higher, but does not support the reverse.
- When they tested promoting 8.0 host to primary, they saw replication break on all 5.7 replicas.
- There the problem were overcome:
  - In MySQL 8.0, `utf8mb4` is the default character set, and `utf8mb4_0900_ai_ci` collation as default.
  - The prior version in MySQL 5.7 supported `utf8mb4_unicode_520_ci` collation but not the latest version of Unicode `utf8mb4_0900_ai_ci`.
  - MySQL 8.0 introduces roles for managing privileges, but not exist in MySQL 5.7.
  - They have the problem with promoted 8.0 to be a primary. Broke downstream replication to 5.7 replicas which is configuration management was expanding certain permission sets to include role statements and executing them.
  - Solved the problem with temporarily adjusting defined permissions for affected users.
- They set the default character encoding to `utf8` and collation to `utf8_unicode_ci` for address the incompatible collation issue.

#### Challenges

- Throughout their testing, preparation and upgrades, they encountered some technical challenges.
- Vitess is a sharding middleware for MySQL and they using this tool for horizontally sharding relational data.
- Replication delay
  - They use read-replicas to scale their read availability.
  - Requires low replication delay in order to serve up-to-date data.
  - `replica_preserve_commit_order` for GTID based replication.
  - [freno](https://github.com/github/freno) to throttle write workloads based on replication lag.
- Queries would pass CI but fail on production
  - Encountered a problem where queries with large `WHERE IN` clauses would crash MySQL.
  - Large `WHERE IN` queries containg over ten of thousands of values.
  - To solve the problem was rewrite the queries to continuing the upgrade process.
  - Query sampling helped to track and detect these problems.
  - [Solarwinds DPM (VividCortex)](https://www.solarwinds.com/database-performance-monitor) a SaaS database performance monitor, for query observability.

#### Learning and takeaways

- Observability platform, testing plan, and rollback capabilities.
- Testing and gradual rollout strategy allowed them to identify problems early and reduce the failure modes.
- Needed the ability to rollback at every step and observability to identify signals.
- The most challenging aspect of enabling rollbacks was ensuring backwards replication between MySQL 5.7 and 8.0.

# Ransomware-As-A-Service: The Growing Threat You Can't Ignore

[reference from thehackernews](https://thehackernews.com/2023/12/ransomware-as-service-growing-threat.html?_m=3n%2e009a%2e3221%2ene0ao45e79%2e27p8)

- Traditional and double extortion ransomware attacks
  - Ransomware is a type of malware that encrypts files on a victim's computer and demands a ransom to unlock them.(Traditionally)
  - Bad actors create copies of the stolen data and threaten to release it publicly if the ransom is not paid.(Double extortion)
- New model for ransomware
  - Inexperienced hackers can now take advantage with RaaS.
  - Instead of traditional ransomware, RaaS are given the option to pay a fee, and select the target.
  - This method reduces the cost and time to attack.
- Business model of RaaS
  - RaaS operates similarly to legitimate businesses.
  - Customers referred to as 'affiliates'.
  - Various of payment options, including flat fees, subscriptions, or a percentage of the revenue.
  - Sometime, providers offer to manage the ransom collection process.
  - Highly competitive market... with user feedback on 'dark web' forums.
  - [Customers] will not hesitate to give a try to another RaaS group if they are not satisfied with the service.
  - Competitiveness between RaaS group is increasing with that all the afgfiliates are searching for the best service.
  - Small failure of RaaS group's malware not can make them lose their affiliates.
- Defending against RaaS
  - Maintaining reliable backups and implementing effective disaster recovery plans.
  - [Pen testing as a service(PTaas)](https://outpost24.com/products/web-application-security-testing/?utm_source=thehackernews.com&utm_medium=referral&utm_campaign=na_thehackernews&utm_content=guest-post) offers real time insights, continuous monitoring, and expert validation, ensuring the security of your web applications at scale.

# SLAM Atack: New Spectre-based Vulnerability Impacts Intel, AMD, and ARM CPUs

[Reference from thehackernews](https://thehackernews.com/2023/12/slam-attack-new-spectre-based.html?_m=3n%2e009a%2e3222%2ene0ao45e79%2e27qm)

- New side-channel attack - SLAM (Vrije Univeriteit Amsterdam researchers)
- SLAM could be exploited to leak sensitive information from kernal memory on current and upcoming CPUs from Intel, AMD, and ARM.
- SLAM attack is an end-to-end exploitfor Spectre based on a new feature in Intel CPUs called Linear Address Masking(LAM), AMD called Upper Address Ignore(UAI) and ARM called Top Byte Ignore(TBI).
- "SLAM exploits unmasked gadgets to let a userland process leak arbitrary ASCII kernel data," VUSec researchers said.
- Leak the root password hash within minutes from kernel memory.

### CVE-2020-12965