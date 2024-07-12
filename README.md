# Understanding Developers’ Discussions and Perceptions on Non-Functional Requirements (The Case of the Spring Ecosystem).

# Complementary Material

# Abstract
Non-Functional Requirements (NFRs) should be defined in the early stages of the software development process, driving developers to make important design decisions. Neglecting NFRs may lead developers to create systems that are difficult to maintain and do not meet user expectations. Despite their importance, the discussion of NFRs is often ad-hoc and scattered through multiple sources, limiting developers' awareness of NFRs. In that scenario, Pull Request (PR) discussions provide a centralized platform for comprehensive NFR discussions. However, existing studies do not explore this important source of information in open-source software development, which developers widely use to discuss software requirements. In this study, we report an investigation of NFR discussions in PRs of repositories of the Spring ecosystem. We collected, manually curated, and analyzed PR discussions addressing four categories of NFR: maintainability, security, performance, and robustness. We observed that discussions surrounding these PRs tend to address the introduction of a code change or explain some anomaly regarding a particular NFR. Also, we found that more than 77% of the discussions related to NFRs are triggered in the PR title and/or description, indicating that developers are often provided with sufficient information straightway. Additionally, to gain more knowledge of NFR discussions, we investigated developers involved in discussions and fixing of NFR issues. For that, we performed an in-depth analysis of 63 developers that stood out in collaborating with the mapped PRs. We discovered that the developers who discuss NFRs often open and review most PRs related to NFRs. To complement this analysis, we conducted a survey with 63 developers to gather their perceptions on NFR discussions. By observing how developers approach NFRs and participate in discussions, we documented the best practices and strategies newcomers can adopt to address NFRs effectively. Through the characterization of NFR discussions, we aim to pave the way for developing automated tools to identify and manage NFRs better. Finally, we provide a curated dataset of 1,533 PR discussions classified with NFR presence.
</p>

<hr>

# Research Questions

<p>With this study, we have the goal of understanding developers’ discussions and perceptions on NFRs. Thus, our study is guided by the following research questions (RQs) </p>

- RQ1. What are the characteristics of the discussions in PRs addressing NFRs?

- RQ2. Who are the developers that engage in NFR discussions?

- RQ3. How do developers perceive and address NFRs in their daily work?

<hr>

# Dataset

We provide a dataset with 1,583 PR discussions classified regarding NFR presence. After manual classification, we built a dataset composed of PR
discussions, each one classified in terms of (i) the presence of the NFRs type addressed, (ii) the location in the PR where the discussions are triggered, (iii) keywords mentioned in the discussion, and (iv) discussion content addressing the NFR. This classification allowed us to characterize the PR discussions and identify the developers discussing NFRs. The dataset is available at This material is available at [`/artifacts/dataset.csv`](https://github.com/devs-discussions-perceptions/devs_discussions_perceptions_paper/blob/main/artifacts/dataset.csv) 

The .csv file is structured with the following columns
- **NUMBER_PR**: The number from the PR analyzed
- **SYSTEM**: The system analyzed
- **URL**: The URL from the PR analyzed
- **NFR_TYPE**: The NFR type identified in the PR discussion
- **PHRASE**: The phrase that led to the NFR classification
- **KEYWORDS**: The keywords related to the NFR present in the discussion
- **LOCATION**: The location where the mention of the NFR was present (_e.g._ title, description)
- **OBS**: Observations regarding the discussion

In our dataset, we have:
- 609 PR discussions related to **Maintainability**
- 393 PR discussions related to **Security**
- 336 PR discussions related to **Robustness**
- 195 PR discussions related to **Performance**

# Keywords

The file [`/artifacts/Keywords.pdf`](https://github.com/devs-discussions-perceptions/devs_discussions_perceptions_paper/blob/main/artifacts/Keywords.pdf) contains the list of keywords for each NFR. We divided these keywords into two groups: (i) single keywords and (ii) composed sentences keywords. The second group has combinations of keywords that can reinforce the presence of the NFR due to its context. 

For each NFR, we also ranked the keywords according to the number of times that the keywords appeared on our manual classification. For instance, the `cleanup` keyword appeared 15 times when we were classifying maintainability PRs. 

The `*` represents that this keyword can have multiple variations. For instance, `doc*` can be related to _documentation_, _document_, _documenting_, and so on.

<hr>

# Open Coding NFRs (Codes and Categories)

To understand the content of the NFR discussions, we focused on analyzing the titles and descriptions in the PRs discussions. For that purpose, we randomly selected 160 PRs for a qualitative analysis. To ensure we evaluated all NFRs equally, we divided this analysis based on the total number of each NFR in our dataset. This analysis was performed on the PRs we knew mentioned the NFRs in the title or description. Through open coding, we generated 35 codes and nine categories that allowed us to understand the content of these titles and descriptions. The list of codes and categories are available at [`/artifacts/Open Coding NFRs.pdf`](https://github.com/devs-discussions-perceptions/devs_discussions_perceptions_paper/blob/main/artifacts/Open%20Coding%20NFRs.pdf) 

We divided the file into pages to make the reading better. If accepted, we will make available the Miro link with the full board with the codes. The last page contains the whole coding.

<hr>

# Survey 

To answer the RQ3, we conducted an opinion survey [Linaker et al . 2015] with 44 developers working with multiple closed-source systems. The survey is composed of questions ranging from the early stages of the software system to its continuous maintenance. 

The survey questions and answers are available at [`/artifacts/survey.xlsx`](https://github.com/devs-discussions-perceptions/devs_discussions_perceptions_paper/blob/main/artifacts/survey.xlsx). 

The survey applied is available at [`/artifacts/survey.pdf`](https://github.com/devs-discussions-perceptions/devs_discussions_perceptions_paper/blob/main/artifacts/survey.pdf).

<hr>


# Identification Protocol and NFR Complementary Material

The process of NFR identification by a single author can be posed as a threat. Although all authors are experienced with the NFRs explored in this study, we also provided complementary material with details about these NFRs to avoid misclassifications. This material is available at [`/artifacts/Protocol NFR Identification.pdf`](https://github.com/devs-discussions-perceptions/devs_discussions_perceptions_paper/blob/main/artifacts/Protocol%20NFR%20Identification.pdf) 

<hr>

# NFR Sub-Categories
For each NFR we subdivided them regarding the type of change that was mentioned in the discussion. That allowed us to understand how many different topics the title and description could address. Following, we describe each sub-category.

**Robustness**
- Error Representability: whether errors are properly represented/specified/thrown
- Error Propagation: whether the error is properly propagated by either remapping to another error type or directly propagated to upper levels
- Error Recoverability: whether proper exception handling and clean-up actions are executed after an exception is raised, and the program’s normal behavior returns to a consistent/safe state after those actions are executed.

**Performance**
- Memory Usage: whether the change increased the memory usage on the application
- Concurrency (Thread Sync): whether there was a change in the concurrency of the system by using threads
- Concurrency (Scheduling): whether there was a change in the concurrency of the system by using scheduling
- Response Time: whether the change increased (or decreased) the response time (_e.g._ page loading)
- Complexity: whether the change increased (or decreased) the computational complexity

**Security**
- Customize Parameters: whether the change allows configure security parameters
- Information Protection: whether the change avoids accessing encrypted addresses
- Support for New Feature: whether the change supports security features (_e.g._ authentication mechanisms) 
- Inconsistent Behavior: whether the change fixes an inconsistent behavior related to security

**Maintainability**
- Feature Enhancement: whether the change is related to an improvement in the system maintainability 
- Code Simplification: whether the changes aim at simplify the code, improving its readability
- Move Component: whether the change focuses on moving components that could be highly coupled, hampering the maintainability
- Documentation: whether the change improves the software documentation
- Readability: whether the change improves the code readability
- Extensibility:  whether the change improves the modules' extensibility 
- Encapsulation: whether the change improves the modules' encapsulation 

<hr>
# Developers Metrics

Aiming to investigate the developers' socio-technical profiles, we computed metrics describing their repository activities and code quality. We computed the metrics by gathering raw data through the GitHub API and performing aggregations to compound more complex metrics. The complete list of metrics are presented below:

- Number of PRs merged
- Number of PRs opened
- Number of PRs closed
- Mean time between merged PRs
- Number of Commits
- Average size of commits (Size in terms of source file)
- Number of commits with .XML files
- Number of commits with .Java files
- Number of reviews
- Number of lines revised
- Number of modules revised
- Number of refactorings
- Number of comments
- Mean time between developer comments
- Mean discussion duration (when the developer participates)
- Mean number of words from the developers' messages on PR discussions
- Total number of words from the developers' messages on PR discussions
- Experience in days (From the first contribution to the last)

<hr>

# Developers' NFR Metrics

We selected developers who had high participation in specific tasks. With this approach, we defined 15 developers to perform an investigation of their profiles. We computed the following metrics:

- **participates_[NFR]**: Number of times that the developer participates in a discussion related to the NFR (e.g., participates_security: 10, means that the developer participated in 10 discussions related to security)
- **opened_discussion_[NFR]**: Number of times that the developer opened discussions related to the NFR
- **commented_[NFR]**: Number of times that the developer commented on discussions related to the NFR
- **reviews_[NFR]**: Number of times that the developer reviewed source code on discussions related to the NFR
- **commited_[NFR]**: Number of times that the developer had commits linked to discussions related to the NFR

None indicates the number of times that the developer did not participate in any task related to the NFRs All NFRs is the total sum for the tasks regarding the four NFRs

For each metric, we computed the quartiles and indicated whether the developer was part of the high, low, or medium quartile. The never tag is marked as True when the developer never performs the task for the correspondent NFR. To exemplify, let us consider the following metrics:

```
"reviewed_robustness_high": true,
"reviewed_robustness_low": false,
"reviewed_robustness_medium": false,
"reviewed_robustness_never": false
```
  
In this case, the developer had a high rate of reviews related to Robustness compared to other developers in the same system. 

The list with these metrics for all developers is available at [`/artifacts/metrics/`](https://github.com/devs-discussions-perceptions/devs_discussions_perceptions_paper/tree/main/artifacts/metrics) 

<hr>


# Developers' Profile (Clusterization)

To understand the developer's socio-technical profile, we clusterize them. Below, we made available the code used for clusterization and analysis.

* [Colab for the SpringBoot dev's clusterization.](https://colab.research.google.com/drive/1aURN4nfoWLs72ok3xiA-1mMEbFcyblba?usp=sharing)
* [Colab for the SpringFramework dev's clusterization.](https://colab.research.google.com/drive/1KBZz0CByU1XIm1EdqmiNLUxpekJhZSfD?usp=sharing)
* [Colab for the SpringSecurity dev's clusterization.](https://colab.research.google.com/drive/1UJLfiF9nU6IZ1kU7j_9VJmFEEVLf2SBf?usp=sharing)

<hr>

# Developers' Inspection Protocol

<p>To answer RQ2, we selected 15 developers, contributing with PRs, to manually perform an inspection on their profiles and evaluate their social metrics. Since the profiles of these developers were not available in a specific document on the repository, we created a protocol for this evaluation, in which four authors participated. </p>


This protocol is available at [`/artifacts/Protocol to identify developers profile.pdf`](https://github.com/devs-discussions-perceptions/devs_discussions_perceptions_paper/blob/main/artifacts/Protocol%20to%20identify%20developers%20profile.pdf) 

<hr>

# Open Coding Developers (Codes and Categories)

We wanted to understand what makes them discuss NFRs. For that purpose, we analyzed other artifacts available (e.g., Github profile and Spring Team page) that could help us understand what could make these developers discuss specific NFRs. Our manual analysis through open coding generated 17 codes and 6 categories, which allowed us to understand who these developers are. More details about these codes and categories are available at [`/artifacts/Open Coding Developers.pdf`](https://github.com/devs-discussions-perceptions/devs_discussions_perceptions_paper/blob/main/artifacts/Open%20Coding%20Developers.pdf) 

<hr>







