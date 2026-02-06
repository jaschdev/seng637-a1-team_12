>   **SENG 637 - Software Testing, Reliability, and Quality**

**Lab. Report \#1 – Introduction to Testing and Defect Tracking**

| Group: 12 |
|-----------|
| Jason Chiu |
| William Watson |
| Jack Shenfield |
| Barrett Sapunjis |


**Table of Contents**

(When you finish writing, update the following list using right click, then
“Update Field”)

[1 Introduction	1](#_Toc439194677)

[2 High-level description of the exploratory testing plan	1](#_Toc439194678)

[3 Comparison of exploratory and manual functional testing	1](#_Toc439194679)

[4 Notes and discussion of the peer reviews of defect reports	1](#_Toc439194680)

[5 How the pair testing was managed and team work/effort was
divided	1](#_Toc439194681)

[6 Difficulties encountered, challenges overcome, and lessons
learned	1](#_Toc439194682)

[7 Comments/feedback on the lab and lab document itself	1](#_Toc439194683)

# Introduction

This lab focused on introducing fundamental software testing concepts through hands-on testing of a simulated ATM system and the use of industry standard defect tracking tools. The primary goal was to gain practical experience with exploratory testing, manual scripted testing, and regression testing, while learning how to effectively document and track defects throughout multiple iterations of a software system.

Before completing this lab, our understanding of exploratory testing was that it is a less rigorous, experience-based testing approach that is unscripted but still goal-based used to find defects in a quick manner. Manual scripted testing on the other hand was understood to be more structured and specific in testing functionalities where predefined test cases are executed to verify that the system behaves according to its specified requirements.

We applied both testing approaches to the ATM simulation system, beginning with exploratory testing to identify defects without predefined guidance, followed by manual scripted testing using a provided test suite. A regression testing phase was then conducted on an updated version of the system to verify defect fixes and identify any newly introduced issues. A final test report in the form of an Excel sheet was then generated to summarize the defects found, including updates across the SUT versions.

# High-level description of the exploratory testing plan

**Test Type:** Exploratory Testing (Manual, Non-Scripted)  
Testing is performed without predefined test cases, allowing test design, execution, and learning to occur simultaneously.

**Objective:**  
The objective of this exploratory testing session is to gain an initial understanding of the ATM simulation system’s behavior and to identify functional defects, usability issues, and unexpected behavior during normal operation. Testing is informed by the system requirements outlined in `seng637-a1.md` Appendix B and focuses on validating whether the implemented behavior aligns with expected user interactions within a limited time frame.

**Scope:**  
Exploratory testing focuses on core system functionality, limited to a maximum of two transactions per session to encourage exploration of multiple features rather than deep repetition. The following functions were targeted based on the system requirements:

- System startup and shutdown behavior  
- User authentication using card and PIN  
- Core transactions: withdrawal, deposit, transfer, and balance inquiry  
- Transaction cancellation and basic error handling  

**Table 1: Modules to be tested**

| Module name | Tester | Description |
|---|---|---|
| Initialization and shutdown | William Watson | The system should be able to be correctly initialized on startup. It should accept a cash amount and communicate with the bank. When in the correct state, the system should easily shut down. |
| Withdraws | William Watson / Jack Shenfield | The customer should be able to select from any of their accounts and withdraw the requested amount. If there are insufficient funds, they should be notified. |
| Deposits | Jack Shenfield / Barrett Sapunjis | Customers should be able to select from any of their accounts and deposit an envelope with an entered amount to update their account. |
| Transfers | Barrett Sapunjis | Customers should be able to make a transfer from any of their valid accounts and move money internally. |
| Inquiries | Jason Chiu | Customers should be able to “inquire” about their accounts and view balances. |
| Logs | Module dependent | On each transaction, or machine function, the system should log its actions for later review if needed. |
| Receipts | Module dependent | The system should print receipts for each withdrawal, transfer, deposit, or balance inquiry showing the users updates. |
| Display | Module dependent | The system should display useful and descriptive information to the customers to help them guide them through the use of the machine. |
| User account security | Jason Chiu | The system should protect the users account by requiring a proper entry of the PIN. In cases of failures or errors, the user should be able to make 3 attempts before their card is locked by the machine. |

Rather than exhaustively testing individual features, the scope prioritized covering multiple system functions at a high level to quickly surface defects and inconsistencies.

**Approach:**  
Testing is conducted as a time-boxed exploratory session guided by the system requirements. Test ideas are derived directly from these requirements and are generated by identifying:

- Common user paths regarding the targeted functions outlined in the scope such as successful authentication and standard transaction flows 
- Exceptional and boundary paths, including invalid inputs, transaction cancellation, and unexpected user actions

The testing strategy prioritizes broad functional coverage, with testers exploring many system functions lightly rather than exhaustively testing individual features. As testing progresses, test ideas are adapted based on observed system behavior and previously discovered defects.

Defects are recorded immediately in the bug tracking system to ensure accurate reproduction and documentation.

**Test Logistics:**  
- **Pair Testing:** Informal pair testing was used where possible, with one tester acting as the driver and the other as the observer. Roles were swapped as time permitted.  
- **Time Box:** Approximately 30 minutes per exploratory testing session  

**Test Deliverables:**  
- Defect reports logged in the defect tracking system  
- Informal notes capturing observations and unexpected behaviors  

# Comparison of exploratory and manual functional testing

Exploratory testing allowed for an organic discovery of bugs, which is a good first step in the black box testing process. The experience of the testers was that through this method, obvious bugs in the common use cases were found very quickly, with no prior use of the software, and no information about the code or development process. 

Some of the issues encountered with exploratory testing were as follows. First, in the exploratory testing, it was common to find a bug after a few other steps in a row. This made it difficult to know if an issue was isolated, or was caused by the previous steps, which may not have been tracked. This required taking additional time to restart the program and try to replicate the defect. Second, depending on the number of bugs present, it was not possible to complete the planned exploration within the time box allotted. For example, one tester initially aimed to evaluate multiple functions such as withdraws, deposits, and transfers in the allotted 30 minutes of testing, but a high number of issues found in withdraws took almost the entire test time to confirm and report. This however meant other testers could focus on the other missed functionalities.

The scripted testing, on the other hand, was positive in that there was more thought put in up front to test each functionality. This resulted in actively confirming the functionality of more basic features that it was not obvious to test in exploration such as boot up and shutdown. The downside of completing the scripted testing after the exploratory testing is that most of the bugs (roughly 75%) had already been discovered from the exploratory testing procedure. This resulted in tediously performing tests where the tester already knew the result. Perhaps it would be more practical to perform the scripted tests first to locate areas of interest, then play around with exploratory testing to potentially discover more issues.


**Table 2: Distribution of defects across testing strategies**

| Test Type | Defects Found |
|----------|---------------|
| Exploratory Testing (v1.0) | 25 |
| Scripted Testing (v1.0) | 9 |
| Regression Testing (v1.1) | 8 |

In total 34 unique bugs were found in version 1.0, with 8 of them remaining in version 1.1.

# Notes and discussion of the peer reviews of defect reports

The peer reviews made us realize the depth in which we need to describe the bug and how to repeat it. As you work with the software and a specific module, you begin to understand it intuitively and start to see the individual components. But when you don’t have this background and read another bug report, sometimes it is difficult to repeat or understand. For some of the bugs, we found we needed to change the wording or add more information. 

We also noticed some duplications in the bug reports. While we each had our own modules to test, the exploratory testing allowed for freedom and “extra testing” per individual. This caused some people to find bugs in other people’s modules which then got duplicated. Additionally, exploratory testing often uncovered bugs that would be found through scripted testing. When the scripted tests were completed, more duplications were made. This is largely due to the wording used in each report. Although the descriptions of duplicate bugs may be similar in sentiment, the actual words may not match. By the time the final bugs are being added, it can’t be expected that the testers will memorize all the previous bugs being entered. Nor is it feasible to deterministically search the titles or descriptions and match them to one another. To work around this, we simply applied more manual labor in checking the previous bug descriptions before adding a new one. This worked quite well and was then further supported by the use of an LLM for pure feedback.  

# How the pair testing was managed and team work/effort was divided 

For the exploratory testing portion, pair testing was done more informally as two members focused more on the testing and documentation of defects in the bug report, while the other two members did a thorough review of the reported bugs while also utilizing the simulation for affirmation and additional testing where needed. This ensured an effective split of workload while also maintaining quality results from pair and group reviewing.

For the manual scripted testing portion, the given 40 test cases were divided equally amongst the four group members to test their respective sections and modules where testers executed and documented bugs. Each person was also responsible for reviewing another member’s results to ensure quality and completeness. Finally, all documentation was worked with equal input from all members.


# Difficulties encountered, challenges overcome, and lessons learned

As noted in the peer-review comments on the defect reports, we encountered issues with duplicate bug entries and clearly understanding some defects. In several cases, we also struggled to decide whether an issue should be logged as a single bug or as multiple bugs. For example, incorrect withdrawal amounts and insufficient-funds errors were often caused by the same underlying issue, but we initially treated them as separate defects.

We also experienced limitations when using Jira, including a large learning curve with excessive options and limited control over the generated documentation. As a result, we chose to complete our bug reporting and tracking using a shared Excel, which proved to be simpler and more efficient for our current needs. However, this approach would not scale well in a long-term or ongoing project. In a persistent environment, it would be important to define components and link them to defects for better traceability. For instance, with our current approach, it is difficult to view the regression history for a specific scripted test. A dedicated tracking tool that stores scripted tests would allow those tests to be directly referenced within bug reports, making regression tracking much easier.

# Comments/feedback on the lab and lab document itself

 It was a bit unclear as to what the requirements were regarding the use of bug tracking tools like Jira and Azure DevOps as the tools seemed more tailored to a mix of software development and software testing rather than simply reporting bugs. Additionally, we were not happy with the formatting and redundant information of the bug reports automatically generated from these tools, so application of the tools was a bit challenging and, in the end, a manual Excel spreadsheet template 1  was used for tracking and producing the bug report.¹

¹ Bug report template reference: https://plaky.com/blog/bug-report-template/