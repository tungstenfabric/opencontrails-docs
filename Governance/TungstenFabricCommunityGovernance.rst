Introduction
============

The Tungsten Fabric technical project has been established as TF Project a Series of LF Projects, LLC (“TF” or, alternatively, the “Project”). LF Projects, LLC is a Delaware series limited liability company. Governance for the Project is detailed within the Project Technical Charter available at Tungsten.io (“Charter”). This Technical Community Document is intended to provide additional operational guidelines for the Project, and is subject to the Technical Charter.

0 Acronyms
==========

ACC - Active Community Contributor, see section **3.2** and **5.2.3.2.3**

ARB - Architecture Review Board, standing committee of architects responsible for design and code reviews, see section **5.2.2**

ATC - Active Technical Contributor, see section **5.2.3.2.1**

CC - Community Committee, standing committee responsible for all non-tech issues, see section **5.2.2**

PTL - Project Technical Lead, person elected to lead a specific project or subproject, see section **4.1.2**

TC - Technical Committee, standing committee responsible for technology guidance, see section **5.2.2**

TF - Tungsten Fabric (this community)

TSC - Technical Steering Committee, overall governance body of the project

TSC-ATC - TSC approved ATC, see section **5.2.3.2.2**

1 Guiding Principles
====================

The Tungsten Fabric Project a Series of LF Projects, LLC (“TF”) will operate transparently, openly, collaboratively, and ethically.  Project proposals, timelines, and status must not merely be open, but also easily visible to outsiders.

2 Structure of the Community
============================

The Tungsten Fabric Community consists of a number of contributors working across technical and other project activities with Technical Steering Committee providing project governance and technical leadership. Tungsten Fabric internally is divided into a number of projects.

3 Community Roles
=================

A given individual can be identified as either a Technical Contributor or a Community Contributor but not both.

3.1 Technical Contributor
-------------------------

A Technical Contributor is someone who contributes to the technical aspects of a project. Contributions could take the form of code, code reviews, documents or other artifacts. Contributors work on individual projects with a project’s Committers. A Contributor may be promoted to a Committer on a specific project by the project’s existing Committers after demonstrating a history of meritocratic contribution to that project.

3.2 Community Contributor
-------------------------

Tungsten Fabric success as a project and community will be predicated on more than simply slinging code. Community adoption and growth will depend on creating a stable and well documented governance structure, conducting outreach to attract new users and contributors, ensuring proper project operation and a large number of other activities in which project volunteers who do not write code can participate.  Tungsten Fabric community recognizes the value of these contributions through adoption to the project success to be as important as pure code development. A Community Contributor is someone who contributes to a project via active participation in community activities such as infrastructure administration, creation of policies, drafting of budgets, marketing, events and other outreach activities.

4 Per Project
=============

4.1 Project Roles 
------------------

4.1.1 Committer
~~~~~~~~~~~~~~~

For each project there is a set of Contributors approved for the right to commit code to the source code management system (the “Committers”) for that project.

-  Committer rights are per project; being a Committer on one project does not give an individual committer rights on any other project.

-  The Committers will work with Technical Committee and ARB to implement and enforce decisions of these bodies and ensure that project design and code complies with the architecture and release and code guidelines.

-  Committers are responsible for delivering new code to the project as well as helping Contributors through review and other guidance, and must actively participate in the project to maintain their status.

-  Committers are responsible for the quality of the code that they commit, they must ensure sufficient test coverage for any piece of code they commit to the project.

Each project should strive for diversity of Committers representing different organizations as well as individuals. However Committer promotions are based on meritocracy and prioritize project contributions above other considerations.

4.1.2 Project Technical Leader:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A project is required to elect a Project Technical Leader (“PTL”). The primary responsibilities of the PTL are:

- Manage day to day operations of the project, including cross-project coordination to ensure Project delivery according to the Tungsten Fabric release schedule

- Act as the de facto spokesperson for the Project

- Represent the Project in the TSC and other necessary meetings

- Resolve conflicts that may arise within the Project

4.1.2.1 Project Technical Leader Candidates
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Candidates for the project’s Project Technical Leader will be derived from the Committers of the Project.

Candidates must self nominate.

4.1.2.2 Project Technical Leader Voters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Only Committers for a project are eligible to vote for a project’s Project Technical Lead.

4.1.3.3 Project Technical Leader Election Mechanics
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

An election for Project Technical Leader occurs when any of the following are true:

-  The project is initially created

-  The Project Technical Leader resigns their post

-  The majority of committers on a project vote to call a new election

-  One year has passed since the last Project Technical Leader election for that project.


4.2 Project Operations
----------------------

4.2.1 Project Decisions Making Process
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Tech Committee (TC) of the TSC is responsible for setting technical TF goals, identifying use cases, setting release guidelines and milestones. It will work with ARB to develop and maintain project high level and detailed architecture. Project Committers will work within this technical and release guidance to deliver individual projects.

Within the project, Committers should operate by general consensus.  If consensus cannot be reached within a reasonable timeframe, decisions are taken by majority vote of a project’s Committers.  Committers may, by majority vote, delegate (or revoke delegation) of any portion of such decisions to an alternate open, documented, and traceable decision making process.

4.2.2 Committer Lifecycle
~~~~~~~~~~~~~~~~~~~~~~~~~

4.2.2.1 Adding Committers
^^^^^^^^^^^^^^^^^^^^^^^^^

-  Initial Committers for a project will be specified at project creation

-  Committer rights for a project are earned via contribution and community trust. Committers for a project propose and vote for new Committers for that project, subject to TSC approval.

-  New Committers for a project should have a demonstrable established history of meritocratic contributions.

4.2.2.2 Adding Committers to moribund projects
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In the event that a project has no active committers (e.g., due to resignations, etc.), the TSC may appoint an interim Committer from a project’s active Contributors. This term shall last until the next release date, after which time the Committer must stand for election from amongst other Committers on the project to maintain his or her status. In this special case, approval requires a majority of committers who respond within two weeks. If no one responds by the deadline, then the committer status is approved. This provision allows a project to continue development following an unexpected change in personnel.

The method by which the TSC appoints an interim Committer is first by request to the tsc@lists.tungsten.io list indicating the request to appoint an interim Committer for a project. After the reception of such an email, the normal TSC decision process applies.

4.2.2.3 Removing Committers
^^^^^^^^^^^^^^^^^^^^^^^^^^^

A Committer may voluntarily resign from a project by making a public request to the PTL to resign (via the project and tsc@lists.tungsten.io lists).

A Committer for a project who is disruptive, or has been inactive on that project for a period greater than six months, may have his or her Committer status revoked by the project’s Project Technical Leader in consultation with TSC or by 2/3 super-majority vote of the project’s committers.

The Project Technical Leader is responsible for informing the Technical Steering Committee (TSC) of any committers who are removed or resign via the tsc@lists.tungsten.io list.

Former committers removed for reasons other than being disruptive may be listed as ‘Emeritus Committers’. That title expresses gratitude for their service, but conveys none of the privileges of being a Committer.

4.2.3 Umbrella Projects
~~~~~~~~~~~~~~~~~~~~~~~

The TSC may create umbrella projects (“Umbrella Projects”) that in turn support multiple sub-projects. Umbrella Projects will be led by an Umbrella Committee made up of the PTLs of each subprojects and one or more Committers, who are the Committers of each of the subprojects. Each subproject will have its own set of committers with responsibility only for the subproject repository.

With the approval of the TSC, Umbrella Projects may establish and modify additional technical roles for sub-project participants.

4.2.4 3rd Party Projects
~~~~~~~~~~~~~~~~~~~~~~~~

As TF community increases, it may expand out beyond its current role and host other related project(s) which do not require close oversight by TC and ARB and will only need loose coordination with TF community. Such projects may be accepted to TF after a majority vote by the TSC members. These projects will operate under a traditional Committer consensus model guided by their PTL. 3rd party projects may set up different release requirements and will have exclusive control of their own release cycle and will be required to coordinate with TC and ARB only on the shared APIs between 3rd party project and the rest of the TF code.

4.3 Project Lifecycle
---------------------

4.3.1 Tungsten Fabric Project Lifecycle
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The activities of the TF community are articulated around projects and releases. The scope of each project is aligned with the TF architecture. The scope of each release is defined with the objective to create new features or enhance existing ones, fix bugs etc.. The scope of each release is documented in the Release Plan of a project.

A **project** is a **long term endeavor** setup to deliver features **across multiple releases**, which have a shorter lifespan.

The project and release lifecycle are simple and provide sufficient visibility to allow teams to coordinate with one another and flock naturally.

The key point of the project and release lifecycle process is to provide adequate visibility to all stakeholders, provide synchronization, and support to all contributors.

This document covers the Tungsten Fabric project lifecycle. The Release Lifecycle is documented in a separate document (include link when ready).

4.3.2 Project Lifecycle Overview
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Tungsten fabric represents a coherent system. In order to maintain this coherence, the Tech WG in close coordination with ARB will designate projects into 4 categories: Core, Affiliated, Incubation, and 3rd Party.

Projects may be following release models: in-cycle, cycle trailing, independent

-  In-cycle release model will be bound by all milestones set by TC and must release at the same time as the core projects.

-  Cycle trailing model typically applies to Lifecycle Management (LCM) tools and installer, although other non critical components may eventually evolve to this model. Cycle trailing project will work with TC to create a set of milestones and release schedule for their releases. These projects must provide a release for every major release cycle and must release their components no later than 3 months following the core release.

-  Projects adopting the independent release model may create their own release timelines, however must coordinate with the TC on any cross project dependencies.


**Core Projects** will represent a minimum viable set of projects required for TF to function. Core Projects must follow the in-cycle release model. These projects will be aligned to the release dates established by the TC and will follow release quality guidelines established by the TC. Release can be declared only when all Core projects have met release quality guidelines set by TC. Majority vote by the combined TSC is required to waive the guidelines and declare a release. Examples of Core Projects are vrouter and controller.

**Affiliated Projects** may adopt one of the 3 valid release models. Their releases should be structured as to not to impact release cycle of the core projects. These projects must negotiate their release timeline with the TC and must follow release quality guidelines set by TC in order to declare a release. Vote by the combined TSC is required to waive the guidelines and declare a release. Examples of such projects are optional installers and LCM tools or OpenStack or Kube integration projects.

**Incubation Projects** will be operating on an independent model until they graduate, their release milestones are not under TC control, although TC and ARB will review use cases these projects are trying to address and architecture decisions made by the project.  Incubation projects may set their own quality guidelines. Their release cycle must be structured not to impact any other project categories. TC may ask these projects to delay their release cycle to resolve resource constraints and other community concerns.

**3rd Party Projects** will operate on the independent release model.  These projects are only required to coordinate their APIs with TC and ARB. If these projects introduce non backward compatible API changes, these projects will be required to align their release cycle per TC request. These projects must be structured so that they do not impact release cycle of the core projects. 3rd party projects will specify their own release and quality guidelines, but these must be documented and made publically available.

TSC shall control project lifecycle for the Core and Affiliated Projects. Project lifecycle for the 3rd party and Incubation projects shall be under the control of the respective project teams.

TC will prepare a release plan for every release covering Core and Affiliated Projects for presentation to the combined TSC. 3rd party and Incubation Projects shall provide their release plans to the TC.

4.3.3 Project Lifecycle States and Reviews
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Tungsten Fabric project lifecycle defines five states that each project goes through. The project lifecycle typically **extends across** multiple releases.

The procedure of moving from one state to the next one is independent from the release, and the pace depends on each individual project.

In order to effectively review project progress, **four** reviews are built-in within the project lifecycle.

The lifecycle of a project is depicted on the following tables:

+-------------------+-----------------------------------------------+
| **Project State** | **Description**                               |
+===================+===============================================+
| Proposal          | Project doesn’t really exist yet, may not     |
|                   | have real resources, but is proposed and is   |
|                   | expected to be created due to business needs. |
+-------------------+-----------------------------------------------+
| Incubation        | Project has resources, but is recognized to   |
|                   | be in the early stages of development. The    |
|                   | outcome is a minimum viable product (MVP)     |
|                   | that demonstrates the value of the project    |
|                   | and is a useful vehicle for collecting        |
|                   | feedback, but is not expected to be used in   |
|                   | production environments.                      |
+-------------------+-----------------------------------------------+
| 3rd Party         | Project is fully functioning and stable, has  |
|                   | achieved successful releases, but its         |
|                   | functionality falls beyond the feature set of |
|                   | the TF project. These projects operate        |
|                   | largely independently of the community        |
|                   | technical oversight.                          |
+-------------------+-----------------------------------------------+
| Core/Affiliated   | These projects are fully functional and       |
|                   | stable. They represent the minimum viable     |
|                   | feature set of the TF project and must be     |
|                   | delivered with the TF release or based on the |
|                   | release time frame set by TC.                 |
+-------------------+-----------------------------------------------+
| Archived          | Project can reach Archived state for multiple |
|                   | reasons. Either project has successfully been |
|                   | completed and its artifacts provide business  |
|                   | values, or project has been cancelled for     |
|                   | unforeseen reasons (no value anymore,         |
|                   | technical, etc.).                             |
+-------------------+-----------------------------------------------+
               
Project in any state can be Archived through a Termination Review.

To move from one state to the next state, the Project Team has to formulate a project status review request to the TSC, by specifying its goal to move up the Project Lifecycle ladder.

+----------------+--------------+----------------------------------+
| **From State** | **To State** | **Review Description**           |
+================+==============+==================================+
| Null           | Proposal     | Proposal review by TSC           |
+----------------+--------------+----------------------------------+
| Proposal       | Incubation   | Incubation review by TC          |
+----------------+--------------+----------------------------------+
| Proposal       | 3rd Party    | 3rd Party proposal review by TSC |
+----------------+--------------+----------------------------------+
| Incubation     | Core         | Maturity review by TC            |
+----------------+--------------+----------------------------------+
| Incubation     | Affiliated   | Maturity review by TC            |
+----------------+--------------+----------------------------------+
| Incubation     | 3rd Party    | 3rd Party proposal review by TSC |
+----------------+--------------+----------------------------------+
| \*             | Archived     | Termination review by TC and TSC |
+----------------+--------------+----------------------------------+

Note 1: List of Projects by their release type shall be posted on TF wiki, with the state of each project clearly labeled.

Note 2: The proposal submitter can decide to remove projects in “proposal” state that do not progress to incubation state. TSC may also chose to delist proposals that have not progressed after a reasonable timeframe.

4.3.4 Tailoring
~~~~~~~~~~~~~~~

TSC by majority vote of the entire TSC may chose to create custom lifecycle and release parameters for a specific project.

4.3.5 Reviews & Metrics Overview
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Project promotion across states can only be done by appropriate review and voting. During the reviews the candidate projects are evaluated based on predefined metrics and KPIs. The target numbers may vary for each project and state.

-  Project ability to meet TF community goals: stability, scalability and performance

-  Project’s ability to follow TF release cadence

-  Comprehensiveness and maturity of the artifacts (code, test cases, documentation) the project produces

-  Ability of the project to consistently meet release quality criteria set by the TC


TC will be responsible for guiding the projects through the review cycle and presenting the project to the combined TSC. Simple majority approval by voting TSC members will be required to advance project state.

4.3.6 Project Reviews
~~~~~~~~~~~~~~~~~~~~~

4.3.6.1 Proposal Review
^^^^^^^^^^^^^^^^^^^^^^^

Project proposal must have a name, description of its goals, rough idea of the project architecture and community willing to support it.  Project proposal shall be prepared with the help of TC and posted to the TF wiki.

4.3.6.1 Incubation Review
^^^^^^^^^^^^^^^^^^^^^^^^^

The goal of the Incubation Review is to officially launch the project and to support its needs until project Termination Review.

Project may achieve incubation state by meeting following goals:

-  Project name reviewed by legal

-  Active community contributing to the project

-  Project initial use cases defined and approved by TC

-  Project architecture approved by ARB

-  Measurable project artifacts (code, BPs, specs, docs) under active development

-  Project following policies set by TSC and project technical guidelines specified by TC


Projects are expected to stay in the incubation phase until they are ready to meet release quality criteria set by the TC.  

4.3.6.2 Maturity Review
^^^^^^^^^^^^^^^^^^^^^^^

Maturity review is required before the project reaches production ready status. Maturity review shall evaluate project’s readiness to meet the TF community goals of stability, performance and scalability. Project is expected to be fully compliant with all the policies and development processes set by the community. Project shall provide following artifacts for review to the TC:

-  Build artifacts and instructions on how to use them

-  Test Plan and Test results

-  Current architecture document

-  Integration Plan with other projects in the TF community

In addition, projects committing to in-cycle or cycle trailing release model should demonstrate ability to successfully deliver timely releases.

4.3.6.3 3rd Party Proposal Review
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

3rd Party Proposal review exists for the purposes of determining if there is alignment between TF community and the incoming 3rd party project. There is an overhead in creating their own community for smaller projects, thus projects beneficial to TF may be hosted within the broader TF community and benefit from the TF organization. The review is designed to evaluate project impact on the TF community and ensure that project benefits to the TF are greater long term, than the long term cost of hosting this project within TF. 3rd party proposals are discussed and voted on by the combined TSC of the TF community.

4.3.6.4 Termination Review
^^^^^^^^^^^^^^^^^^^^^^^^^^

Projects reach the termination state if they no longer provide TF community with technical value as determined by TC and ARB, or they have lost their community and can no longer meet project release guidelines. As part of the termination process TC and ARB will evaluate impact on other Core and Affiliated Project to determine a transition plan to eliminate cross project dependencies. After transition plan is met, project artifacts will be archived and project releases will cease.

4.4 Amendments to the Technical Community Document
--------------------------------------------------

The TSC may make amendments to this Technical Community Document at any time. The charter amendment process is for a TSC voting member to propose changes that will be decided by simple majority of the full TSC. The proposed changes are subject to review and approval by the Series Manager of TF.

5 Technical Steering Committee
==============================

5.1 TSC Roles
-------------

5.1.1 TSC Members
~~~~~~~~~~~~~~~~~

There will be a startup period for the TF project during the calendar year 2018 in which the TSC will be comprised of 11 members who volunteered to represent the project at its founding or stood for election as replacements following the resignation of one of the original members. After the startup period, January 2019 and beyond, the TSC will move to a “steady state” where the TSC is fully elected from the community. The specifics of this election process will be documented by the “startup” TSC no later than December, 2018. TSC shall be divided into 3 classes. Community 5 members, Technical 5 members and one ARB representative

5.1.1.1 Startup Period 
^^^^^^^^^^^^^^^^^^^^^^

TSC Member list for the start up period can be located in https://docs.google.com/document/d/1xFNNPNb8lXXha24lNbKkMMCvE30ydS97Obb1YhEaPeU/edit?usp=sharing

5.1.2 TSC Chair
~~~~~~~~~~~~~~~

The TSC will elect from amongst voting TSC members a chairperson for a term of one year according to the TF Technical Charter. The TSC shall hold elections to select a TSC Chair annually; there are no limits on the number of terms a TSC Chair may serve.

5.1.2.1 Responsibilities
^^^^^^^^^^^^^^^^^^^^^^^^

The primary responsibility of the TSC Chair is to represent the technical community in communications with the LF Networking Fund of The Linux Foundation and to be responsible for:

-  Leading TSC meetings;

-  This responsibility may be delegated to the another TSC member (in such case, this is to be informed via the TSC email list)

-  Representing the technical community to external organizations.

-  These responsibilities may be delegated to another member of the technical community.

-  Lead the TSC in the execution of the TSC’s responsibilities (section **5.3**).

5.1.3 Vice Chair
~~~~~~~~~~~~~~~~

The TSC may optionally elect from amongst voting TSC members a Vice Chair. If Vice Chair is elected, the TSC shall hold elections to select a Vice Chair annually; there are no limits on the number of terms a Vice Chair may serve.

5.1.3.1 Responsibilities
^^^^^^^^^^^^^^^^^^^^^^^^

The Vice Chair will support the TSC Chair.

The Vice Chair will represent the TSC when the TSC Chair is not available unless other delegation has been made explicitly.

5.2 TSC Operations
------------------

5.2.1 TSC Decision Making Process
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In order to accelerate decision making process within the community and minimize the number of meetings where large quorum is required, TSC will form 3 standing committees (described below) and delegate its decision making responsibilities to the appropriate committee.  Combined TSC shall set overall project goals for the year and next 6 month cycle and will meet to discuss and vote on global project issues, such as amendments to the Charter or Governance documents, approval of budget request to be sent to LFN, approval of new projects or project phase transitions as appropriate. Subcommittees
will be responsible for day to day operation of the community.

Decisions of the TSC should be made by rough consensus and documented as “agreed” decisions in the TSC meeting notes. If consensus cannot be reached, then a vote should be taken with the winning majority vote of TSC Members being documented as the decision in the TSC meeting notes.

5.2.2 Standing Committees
~~~~~~~~~~~~~~~~~~~~~~~~~

*Community Committee*: this committee will be responsible for non-technical aspects of the project, including initiating the budget proposals, controlling any budget delegated by the LFN directly to the project, drafting community policy and other governance materials, marketing and other outreach activities and other non-technical matters. CC members may be selected from the project Community Contributor and Technical Contributor candidates by the election process defined below. 

This committee consists of TSC members elected as part of Community-At-Large TSC class.

*Technical Committee*: this committee will be responsible for technical aspects of the project, including identifying and approving project use cases and technical definition of product features such as hardware support, creating technical processes for developers and projects, setting release and quality criterias, defining release cycle and other technical matters. TC members will be chosen from the project Technical Contributors by the election process defined below.

This committee consists of TSC members elected as part of Technical Project Leadership TSC class.

*ARB*: this committee is formed exclusively from project architects and will be responsible to ensure that project conforms to a coherent architecture and maintains its stability, scalability and performance. ARB will define project detailed architecture and will review all specs and code (as needed) to ensure compliance to project goals and architecture. Candidates to the ARB must be in a senior engineering role within their respective companies and be recognized as an area architect by their peers. Further description of the ARB is available in section **5.5**.

Decisions of the committees should be made by rough consensus and documented as “agreed” decisions in the meeting notes. If consensus cannot be reached, then a vote should be taken with the winning majority vote of committee members being documented as the decision in the meeting notes.

5.2.3 TSC Chair/Vice Chair Elections
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The TSC Chair/Vice Chair shall be elected separately, assuming that a Vice Chair is to be used in a project.

5.2.3.1 TSC Chair/Vice Chair Candidates
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Candidates for TSC Chair or Vice Chair must be TSC Members as defined in section **5.1.1.**

Candidates must self nominate.

5.2.3.2 TSC Chair/Vice Chair Voters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Only TSC Members (section **4.1.1**) are eligible to vote for TSC Chair/Vice Chair.

5.2.3.4 TSC Chair/Vice Chair Election Mechanics
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Election of a TSC Chair/Vice Chair shall use a multiple-candidate method, e.g.:

Condorcet: http://en.wikipedia.org/wiki/Condorcet_method; or Single Transferable Vote: http://en.wikipedia.org/wiki/Single_transferable_vote

5.2.4 TSC Member Elections - Steady State (January 1st, 2019 and beyond)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Election of TSC members shall use a multiple-candidate method, e.g.:

Condorcet: http://en.wikipedia.org/wiki/Condorcet_method; or Single Transferable Vote: http://en.wikipedia.org/wiki/Single_transferable_vote

5.2.4.1 Technical Community Constituencies
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

There are three constituencies with representatives in the TF TSC.

1. Community-At-Large - These individuals are Active Community Contributors as defined in section **3.2** and **5.2.3.2.3**

2. Technical Project Leadership - These individuals are actively engaged in the project as defined in section **3.1** and are recognized as providing technical leadership to the Tungsten Fabric community (as either ATC, or TSC-ATC).

3. Architectural Review Board (ARB) Representative - This individual is elected by the existing ARB members to represent the ARB directly on the TF TSC.

5.2.4.2 Types of TF Contributors
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

5.2.4.2.1 Active Technical Contributor (ATC)
""""""""""""""""""""""""""""""""""""""""""""

Active contribution to the TF project by contributing code/patches, which are approved by the project committers. The contribution is not limited to code, it could be documentation or other contributions. At least one approved/merged patch in one release is required in the preceding 12 months prior to the election.

5.2.4.2.2 TSC Approved Active Technical Contributor (TSC-ATC)
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Active contribution to the TF project that is recognized as beneficial by the TSC in one or more of the following areas:

a. Candidate actively participates in the TSC calls (e.g. 80% participation in TSC calls in past “6” months – The TSC reserves the right to change this criteria at its discretion)

b. Candidate leading/driving/contributing to sub-teams or sub-projects related to TF

c. Candidate championing or aligning TF activities among other projects within or outside of the Linux Foundation Networking (LFN) Fund.

Any TSC member can nominate a community member for TSC-ATC status, providing evidence as to the good work done by the individual for the community. The TSC will then vote to approve or decline the individual’s TSC-ATC status. Such a designation is good for one year, and must be renewed by the TSC annually to remain current.

5.2.4.2.3 Active Community Contributors (ACCs)
""""""""""""""""""""""""""""""""""""""""""""""

A Community Contributor is someone who contributes to a project via active participation in community activities such as infrastructure administration, creation of policies, drafting of budgets, marketing, events and other outreach activities. These members who are not technical code contributions, but nevertheless focused on project growth and adoption. Requirements:

a) Active contribution to TF policy creation, budget, evangelism, marketing, event activity and other non-technical project tracks.

b) Standing active participation in community meetings. Active is defined as execution of action items, participation in planning or execution of events and other outreach activities, contributions to community documents.

Any TSC member can nominate a community member for ACC status, providing evidence as to the good work done by the individual for the community. The TSC will then vote to approve or decline the individual’s ACC status. Such a designation is good for one year, and must be renewed by the TSC annually to remain current.

5.2.4.3 Candidate and Voter Eligibility
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Community-At-Large**

    -  Voter Criteria

        -  Community members designated as ATC, TSC-ATC or ACC

    -  Candidate Criteria

        -  (ATC or TSC-ATC) and ACC

    -  CaL Representation

        -  5 TSC Seats

        -  Each seat determined by ranked voting of all candidates with the top 5 candidates from different, and unrelated companies winning the election.

**Technical Project Leadership**

    -  Voter Criteria

        -  Community members designated as ATC or TSC-ATC

    -  Candidate Criteria

        -  ATC or TSC-ATC

    -  Technical Project Leadership Representation

        -  5 TSC Seats

        -  Each seat determined by ranked voting of all candidates with the top 5 candidates from different, and unrelated companies winning the election.

**Architectural Review Board (ARB) Representative**

    -  Voter Criteria

        -  Current ARB member

    -  Candidate Criteria

        -  Current ARB member

    -  1 TSC Seat is designated for the ARB Representative

5.2.4.4 TSC Member Candidates
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

-  There are no limitations on the number of candidates that can run for a TSC seat, nor is there a limit to the number of candidates from any company, or group of related companies (please see sec **5.4.1.4** for definition of related company) that can run in a TSC election.  However only a single company candidate per class may assume the TSC role. If multiple candidates from the same company are elected per single class, the candidate with the most votes will assume the seat and the other candidates from the same company disqualified.

-  Candidates must self nominate

5.2.4.5 TSC Member Election Mechanics
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

-  The election of the Community-At-Large, Project Technical Leadership candidates will take place in separate votes. Each vote shall consist of a single stack-ranked vote of all candidates via CIVS ( Condorcet: http://en.wikipedia.org/wiki/Condorcet_method);

-  The top 5 ranked candidates from different and unrelated companies will be determined the winners of the vote.

-  ARB shall meet and elect a representative to the TSC by simple majority vote.

5.3 Responsibilities of the TSC. 
---------------------------------

Subject to the Technical Charter, the TSC is responsible for:

-  Defining Tungsten Fabric’s release vehicles (such as a Coordinated Release) that align with the Project’s,mission,

-  Fostering cross-project collaboration including external open source projects

-  Serving as TF’s primary technical liaison body with other consortiums and groups,

-  Developing an architecture,

-  Setting simultaneous release dates,

-  Defining release quality standards,

-  Defining technical best practices and community norms (including the establishment and maintenance of a Development Process),

-  Monitoring technical progress,

-  Mediating technical conflicts between Committers and PTLs, working-groups, etc.

-  Organizing inter-project collaboration,

-  Coordinating technical community engagement with the end-user community.

-  TSC will devolve portion of its responsibilities to standing committees defined in the section **5.2.2** and may create additional standing committees with a super majority (⅔) vote of the entire TSC.

5.4 TSC Additional Subcommittees
--------------------------------

The TSC, at its discretion, may establish additional subcommittees to assist the TSC with its responsibilities and provide expert guidance in technical subject areas (e.g., architecture or security).  

5.4.1 Membership
~~~~~~~~~~~~~~~~

5.4.1.1 Subcommittee Membership Eligibility
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Each subcommittee shall determine its own membership eligibility, in consultation with the TSC. It is expected that subcommittee membership shall be open to all Tungsten Fabric contributors; however, subcommittees may impose restrictions such as the number of participants from a single company. While the desire may be to keep its size and scope limited, each subcommittee shall be open to the LFN community members. In particular, all elected TSC members are eligible to join a subcommittee.

5.4.1.2 Subcommittee Chair / Vice Chair
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Each subcommittee may elect a Chair and optionally a Vice-Chair who is responsible for leading meetings and representing the subcommittee to the TSC.

5.4.1.3 Subcommittee Chair / Vice Chair Elections
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Chair or Vice-Chair will be elected by members of the subcommittee as of the date the nomination process starts for the election.

5.4.1.4 Subcommittee Voter Eligibility
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Voting for a Chair or Vice-Chair is not limited to LFN member companies.  However only 1 Subcommittee member from each company, or group of related companies may vote in the election.

For the purpose of this document, “Related Company” shall mean any entity (Company-A) which controls or is controlled by another entity (Company-B) or which, together, is under the common control of a third party (Company-C), in each case where such control results from ownership, either directly or indirectly, of more than fifty percent of the voting securities or membership interests of the entity in question; and “Related Companies” are entities that are each a Related Company as described above.

5.4.1.5 Subcommittee Election Confirmation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The elected Chair (and/or Vice-Chair) is submitted to the TSC for confirmation. The TSC decides to accept the outcome or requests a new voting.

5.4.2 Advisory role for subcommittees
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The 3 standing committees listed in this document have delegated decision power as well as any future standing committees created by TSC, all other subcommittees are advisory in nature, and not authoritative. They provide advice to projects and to the TSC.

Subcommittees operate on a rough consensus basis. If the subcommittee is unable to reach consensus on what advice to offer, the subcommittee Chair shall raise the issue with the TSC, where a formal vote can be taken, or advise the project that the subcommittee cannot reach consensus.

5.4.3 TSC subcommittee lifecycle.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

5.4.3.1 Creation of a TSC subcommittee
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The TSC decides the creation of a subcommittee in accordance with TSC decision procedure.

In order to create a TSC subcommittee, a TSC member shall make a proposal to the TSC (via tsc@lists.tungsten.io list) that that shall cover at least the following:

-  TSC subcommittee name.

-  TSC subcommittee purpose: <Description of subcommittee purpose>

-  TSC subcommittee expected deliverables: <List of expected deliverables>

-  TSC subcommittee starting participants: <List of expected starting participants>

-  Optionally TSC subcommittee definition of done: <Description of what is expected at the conclusion of the subcommittee. This may relate to the deliverables>

5.4.3.2 Update of a TSC subcommittee
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The TSC can modify a TSC subcommittee via a TSC decision. To request such a modification, a request is made to the TF-TSC email list.

5.4.3.3 Conclusion of a TSC subcommittee
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The TSC decides the termination of the TSC subcommittee in accordance with the TSC decision procedure. The submission of a request to terminate the TSC subcommittee should cover:

-  TSC subcommittee name

-  TSC subcommittee deliveries: <description of what has been achieved>

-  Motivation for termination of TSC subcommittee: <Reason for requesting the termination of the subcommittee>

5.5 ARB
-------

ARB has a singular mission in TF organization, preservation of coherent architecture and ensuring that all code in the project complies to that architecture and is high performance, scalable and production ready. Thus ARB constitutes a committee of project experts and has a unique set of qualifications.

5.5.1 ARB Member Qualification
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Mandatory requirements:

-  Members with strong technical background. As an example an architect, a CTO, a technical director with direct technical role

-  Understanding of the Tungsten Fabric architecture

-  Understanding of SDN/NFV and their use cases

-  Core contributor on at least one TF project or specifically nominated by TSC for proven expertise.

Optional Requirements:

-  Understanding how Open Source operates (blueprint reviews etc)

-  Understanding the code of the specific component and related third party libraries that is being reviewed

-  Understanding of the full system view, but either be an expert in system level or be an expert in a specific area but with some level of understanding in the system.

5.5.2 ARB Responsibilities
~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Develop and maintain detailed project architecture based on goals set by TSC

-  Control all APIs between components

-  Review all specs to ensure compliance with project architecture and to ensure that stability, scalability and performance goals for the project are met by every new feature introduced.

-  Reviewing code as necessary to ensure compliance with project architecture and to ensure that stability, scalability and performance goals for the project are met by every new feature introduced.

-  ARB team members can -2 code on any project

-  Establishing format and/or template for ensuring that code is vetted for security and integrity in compliance with the process and policy established by the TC.

5.5.3 Membership and Elections
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ARB is a Committee of seven members representing different areas of the code. The number of ARB members is set both to provide expertise on various areas and to divide the necessary workload. Number of ARB members can be revised by TSC to address both project growth and increase in the workload by the ARB. ⅔ majority vote of the TSC is required to alter the number of ARB members.

In order to ensure architectural consistency, ARB member term will run for 24 months. ARB committee will have staggered elections which replace no more than 60% of ARB per election cycle. Election process shall be set up by TSC starting with 2019.

Election of a ARB members shall use a multiple-candidate method, e.g.:

Condorcet: http://en.wikipedia.org/wiki/Condorcet_method; or Single Transferable Vote: http://en.wikipedia.org/wiki/Single_transferable_vote

The ARB Committee members are initially selected from the Project’s Committers and Community volunteers. Initial ARB member list maintained here: https://github.com/tungstenfabric/docs/blob/master/TSCWG/ARB_Members

After the initial period ARB members shall come from the pool of project cores or be specifically nominated for ARB candidacy by TSC.  Any TSC member can nominate a community member for ARB, providing evidence as to the good technical work done by the individual for the community. Majority vote of TSC is required to affirm nominee.

-  Voter Criteria

-  Project Committers, PTLs, TSC members

-  Candidate Criteria

-  Project Core or TSC nominee

-  ARB Representation

-  7 Seats

-  Each seat determined by ranked voting of all candidates with the top 7 candidates winning the election.

5.5.4 Process and Decision Making
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  ARB shall divide code base into areas of responsibility, and each area shall have a single ARB member designated as that area's ARM member. Each area shall operation autonomously. Approval from the area ARB member is sufficient for spec or code commit to be accepted.  Rejection of a spec or commit may be overridden by ⅔ vote of all ARB members.

-  Voting shall be required only to adopt architecture, API specifications, general ARB processes and as a dispute resolution mechanism.

-  Decisions by vote will be conducted electronically even if initiated verbally, and will require a majority vote of all eligible (not merely present or responding) voting members in favor.

-  If ARB is unable to resolve a particular issue, ARB shall escalate the issue to TSC.

-  Any meetings of the Architectural Review Board are intended to be open to the public, and can be conducted electronically, via teleconference, or in person.

-  ARB shall elect ARB representative to act as the ARB chair for meetings and votes and to represent ARB on the TSC.
