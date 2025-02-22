---
ospool:
  path: overview/references/policy.md
---

Policies for Using OSG Connect and the OSPool 
====================================

Access to OSG Connect and the Open Science Pool (OSPool) is contingent on compliance with the below and with any requests from OSG staff to change practices that cause issues for OSG systems and/or users. **Please contact us if you have any questions! We can often help with exceptions to default policies and/or identify available alternative approaches to help you with a perceived barrier.**

As the below do not cover every possible scenario of potentially disruptive practices, OSG staff reserve the right to take any necessary corrective actions to ensure performance and resource availability for all OSG Connect users. This may include the hold or removal of jobs, deletion of user data, deactivation of accounts, etc. In some cases, these actions may need to be taken without notifying the user.

1. **By using the OSG Connect service, users are expected to follow the Open Science Pool [acceptable use policy](https://github.com/opensciencegrid/osgconnect-portal-markdowns/blob/master/signup_content/signup_modal.md)**, which includes appropriate scope of use and common user security practices. OSG Connect is only available to individuals affiliated with a US-based academic, government, or non-profit organization, or with a research project led by an affiliated sponsor.

2. **Users can have up to 10,000 jobs queued, without taking additional steps**, and should submit multiple jobs via a single submit file, according to our online guides. Please write to us if you’d like to easily submit more!

3. **Do not run computationally-intensive or persistent processes on the access points (login nodes).** Exceptions include single-threaded software compilation and data management tasks (transfer to/from the login nodes, directory creation, file moving/renaming, untar-ing, etc.). The execution of multi-threaded tasks for job setup or post-processing or software testing will almost certainly cause performance issues and may result in loss of access. Software testing should be executed from within submitted jobs, where job scheduling also provides a more accurate test environment to the user without compromising performance of the login nodes. OSG staff reserve the right to kill any tasks running on the login nodes, in order to ensure performance for all users. Similarly, **please contact us to discuss appropriate features and options, rather than running scripts (including `cron`) to automate job submission**, throttling, resubmission, or ordered execution (e.g. workflows), even if these are executed remotely to coordinate work on the OSG Connect login nodes. These almost always end up causing significant issues and/or wasted computing capacity, and we're happy to help you to implement automation tools the integrate with HTCondor.

4. **Data Policies**: *OSG Connect filesystems are not backed up and should be treated as temporary (“scratch”-like) space for active work, only*, following [OSG Connect policies for data storage and per-job transfers](../../../htc_workloads/managing_data/osgconnect-storage/). Some OSG Connect storage spaces are truly ‘open’ with data available to be downloaded publicly. Of note:
	 - Users should keep copies of essential data and software in non-OSG locations, as OSG staff reserve the right to remove data at any time in order to ensure and/or restore system availability, and without prior notice to users.
	 - Proprietary data, HIPAA, and data with any other privacy concerns should not be stored on any OSG Connect filesystems or computed in OSG. Similarly, users should follow all licensing requirements when storing and executing software via OSG Connect submit servers. (See “Software in OSG Connect”.) 
	 - Users should keep their /home directory privileges restricted to their user or group, and should not add ‘global’ permissions, which will allow other users to potentially make your data public.
	 - User-created ‘open’ network ports are [disallowed](https://github.com/opensciencegrid/security/blob/master/docs/policy/OSG_Connect_Login_Server_Open_Port_Policy.md), unless explicitly permitted following an accepted justification to support@osg-htc.org. (If you’re not sure whether something you want to do will open a port, just get in touch!)

5. The following actions may be taken automatedly or by OSG staff to stop or prevent jobs from causing problems. Please contact us if you’d like help understanding why your jobs were held or removed, and so we can help you avoid problems in the future.
	 - **Jobs using more memory or disk than requested** may be automatically held (see [Scaling Up after Test Jobs](../../../htc_workloads/workload_planning/preparing-to-scale-up/) for tips on requesting the ‘right’ amount of job resources in your submit file).
	 - **Jobs running longer than their JobDurationCategory allows for** will be held (see [Indicate the Job Duration Category of Your Jobs](../../../htc_workloads/workload_planning/roadmap/)).
	 - **Jobs that have executed more than 30 times without completing** may be automatically held (likely because [they’re too long](../../../overview/account_setup/is-it-for-you/) for OSG).
	 - **Jobs that have been held more than 14 days** may be automatically removed.
	 - **Jobs queued for more than three months** may be automatically removed.
	 - **Jobs otherwise causing known problems** may be held or removed, without prior notification to the user.
	 - **Held jobs may also be edited to prevent automated release/retry**
	 - NOTE: in order to respect user email clients, job holds and removals do not come with specific notification to the user, unless configured by the user at the time of submission using HTCondor’s ‘notification’ feature.