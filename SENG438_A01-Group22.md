# SENG 438 - Software Testing, Reliability, and Quality

# Lab Report #1 - Introduction to Testing and Defect Tracking

| Group #22 |
|-----------|
|Kamand|
|Dylan|
|Spiro|
|Issy|

# Table of Contents
[Introduction](/SENG438_A01-Group22.md#introduction)

[High-level description of the exploratory testing plan](/SENG438_A01-Group22.md#high-level-description-of-the-exploratory-testing-plan)

[Comparison of exploratory and manual functional testing](/SENG438_A01-Group22.md#comparison-of-exploratory-and-manual-functional-testing)

[Notes and discussion of the peer reviews of defect reports](/SENG438_A01-Group22.md#notes-and-discussion-of-the-peer-reviews-of-defect-reports)

[How the pair testing was managed and team work/effort was divided](/SENG438_A01-Group22.md#how-the-pair-testing-was-managed-and-team-workeffort-was-divided)

[Difficulties encountered, challenges overcome, and lessons learned](/SENG438_A01-Group22.md#difficulties-encountered-challenges-overcome-and-lessons-learned)

[Comments/feedback on the lab and lab document itself](/SENG438_A01-Group22.md#commentsfeedback-on-the-lab-and-lab-document-itself)


# Introduction
In this lab, we were tasked with testing an ATM application using both manual functional testing (MFT) and exploratory testing principles. The application has two versions: the initial release and an updated release incorporating changes based on identified defects. This setup allows us to perform regression testing.

MFT involves verifying a predetermined list of test cases to ensure that fundamental requirements are functioning correctly. In contrast, exploratory testing is an open-ended approach where testers actively search for bugs and defects without following a rigid testing plan. The goal of this lab is to gain hands-on experience with software testing and develop a high-level understanding of different testing methods.

# High-level description of the exploratory testing plan

Our exploratory testing plan consisted of two paired testing groups. The first group tested as typical ATM users, while the second group tested as potential ATM exploiters, attempting to take unconventional paths to manipulate the system. Each pair alternated between testing and note-taking to gain new perspectives.

**Typical ATM User Test Plan:**

For this plan, we mimicked a normal ATM user and tested both Card #1 and Card #2. A rough overview of the test plan was as follows:

1) Insert a given card and enter the correct PIN.
2) Use the withdrawal functionality, then eject the card.
3) Reinsert the card and test the deposit functionality, then eject.
4) Reinsert the card and test the transfer functionality, then eject.
5) Reinsert the card and test the balance inquiry functionality, then eject.
   
**ATM Exploiter Test Plan:**

For this plan, we conducted more extensive testing of the login and withdrawal functionalities. While deposits were considered, they were not the primary focus. The following exploratory test cases were performed:

1) Inserting a false card (by entering non-numerical values or random numbers).
2) Entering random/incorrect PINs.
3) Checking whether the chosen withdrawal amount matches the actual amount dispensed.
4) Verifying that the amount withdrawn is correctly deducted from the account balance.
5) Attempting to withdraw money from an unavailable account (Money Market for Card #1 and Savings for Card #2).
6) Trying to withdraw more money than the account balance allows.
7) Checking whether the deposited amount is accurately reflected in the balance.
8) Testing what happens if an unrealistic deposit amount is entered.
9) Confirming that transferred funds are correctly moved from one account to another.
10) Attempting to transfer money from an unavailable account to another unavailable account.
# Comparison of exploratory and manual functional testing

Exploratory testing relies on a tester's creativity, intuition, and experience rather than well-defined testing scripts. Beginning with exploratory tests allowed our team to freely experiment with different functionalities and become familiar with a system we had not used before. Most of the bugs were identified during the exploratory testing phase, helping us understand the application's requirements before proceeding with manual functional testing (MFT).

MFT was more rigorous and detailed than exploratory testing. It covered each function and use case, providing predefined information about the system’s initial state and expected outcomes. MFT was also more efficient, as test cases were systematically executed and divided among team members to avoid duplication and wasted effort. However, there are trade-offs between MFT and exploratory testing.

MFT requires testers to strictly follow predefined scripts, which can lead to some bugs being overlooked if they fall outside the scripted test cases. Conversely, exploratory testing allows testers to uncover edge cases and exceptional pathways that may not be covered by MFT scripts. However, exploratory testing can be inefficient. During this phase, we noticed that some issues in the Jira backlog were duplicates. Additionally, when a bug was discovered, we sometimes had to repeat the steps to accurately document the initial state and inputs that led to the error.

Since the ATM system was a simple application, most bugs were discovered during the exploratory testing phase. However, for more complex applications, detailed test plans and scripts, such as those used in MFT, are essential. Both testing approaches have their strengths and limitations, so a balanced approach—combining exploratory and manual functional testing—can be the most effective strategy. By integrating both methods, we can maximize the number of identified and resolved defects, which is the ultimate goal of any quality assurance (QA) team.

# Notes and discussion of the peer reviews of defect reports
**Kamand:**

- Backlog entries from each pair were reviewed by all team members. We noticed that some entries lacked details regarding the initial state of the system, the inputs needed to reproduce the error, or had descriptions that required clarification. Additionally, we observed that in some cases, a single test case or bug could be broken down into multiple defects due to its overlap with other functionalities or its complexity.

**Spiro:**

- After performing exploratory tests related to transfer functionalities, I discovered that a functionality closely related to a passing MFT test was actually invalid. This may be because MFT follows a strict set of predefined outlines, which can lead to overlooking issues in surrounding functionalities. In the future, a potential improvement would be to create more thorough MFT tests or to ensure exploratory tests are conducted in related areas.

**Dylan:**

- I found that our approach of acting as an ATM exploiter was highly effective in identifying issues that would not necessarily be detected through regular or manual testing. For example, one of the bugs we discovered was that entering a deposit amount over $22 million completely freezes the ATM, making it unusable. This issue was not resolved in ATM 1.1 and needs to be patched before deployment. An ATM freeze could impact the physical hardware of the machine or leave it in a vulnerable state, potentially disrupting service for other customers.
- Some backlog entries required additional details regarding the steps needed to reproduce an error, but overall, they were original and informative. The added fields, which allowed us to specify whether an issue persisted in ATM 1.1, were particularly useful and improved efficiency.

**Issy:**

- Despite using pair testing, we still identified some overlooked defects, such as transaction logs displaying incorrect card numbers (e.g., 1 or 2). Since this defect was common across multiple test cases, it resulted in many duplicate reports. In the future, it would be beneficial to review the reported bugs before logging new defect entries to minimize redundancy.

# How the pair testing was managed and team work/effort was divided 
Following the guidelines of pair testing, the two pairs formed were:

- Kamand & Spiro
- Dylan & Issy
  
**Dylan & Issy:**
In this pair, responsibilities were alternated between testing and note-taking. Dylan focused on login and deposit-related tasks, while Issy tested withdrawal and transfer functions. This approach ensured an even distribution of work. While one person conducted the test, the other documented the steps taken, expected results, and actual outcomes. Pair testing also allowed for real-time feedback during and after testing, ensuring that different perspectives and potential improvements were considered. For the manual functional tests, test cases were evenly distributed among all team members, with each person responsible for executing ten tests. For regression testing, each member retested their assigned MFT and exploratory test cases from previous phases.

**Kamand & Spiro:**
This pair adopted a "divide and conquer" strategy by splitting testing responsibilities based on different functionalities. Kamand focused on deposits and withdrawals, while Spiro tested balance inquiries and system logs. Each member documented the defects they found in the backlog and later cross-checked for duplicates.


# Difficulties encountered, challenges overcome, and lessons learned
Teamwork played a crucial role in our success, as tasks were distributed efficiently among team members. Effective communication was a key factor that helped us navigate different testing phases. After completing each test, we realized the importance of thoroughly documenting any additional issues to prevent redundant efforts.

One major lesson we learned was the necessity of clearly defining roles before starting the testing process. We often found ourselves going back and forth to confirm responsibilities, which slowed our progress. Establishing a shared outline with predefined roles and responsibilities beforehand would have been beneficial.

From a technical perspective, we learned the importance of fully understanding the problem definition and deliverables before diving into testing. Taking the time to do this can save hours of extra work and reduce the need for iterative refinements. Additionally, we gained insight into how professional engineering teams conduct QA by testing software through multiple stages.

The significance of regression testing was highlighted, as certain functionalities remained faulty even in the updated version of the application. We also recognized the value of establishing standardized fields in our bug tracking tool before logging entries. Fields such as:

- Program Version: ATM 1.0, ATM 1.1
- Testing Type: Exploratory (EXP), Manual Functional Testing (MFT), Regression (REG)
- Feature/Function Tested
- Input
- Expected Output
- Actual (Faulty) Output

were introduced progressively as we tested. However, this meant we had to revisit and update older backlog entries for consistency. Making these fields mandatory from the start would have streamlined the process.

One significant challenge we encountered was ensuring our testing logs were sufficiently detailed so that defects could be consistently reproduced. Failure to document clear reproduction steps can lead to unreliable regression test results. We also realized that many test cases shared common steps, such as turning on the ATM and inserting the card. In the future, it may be beneficial to document these common steps separately as a reference section, reducing the size of individual defect reports.

# Comments/feedback on the lab and lab document itself
**Kamand:**
- I particularly appreciated the use of GitHub Classroom and real-world defect tracking systems in this lab. Working with Atlassian Jira was a great experience, as it helped me understand how defect reporting is handled in a professional setting. However, formatting the lab report in Markdown felt somewhat restrictive, as it limited our ability to simultaneously develop and structure the report in a visually appealing way. Additionally, it would be helpful to have a copy of the grading rubric available in D2L, such as in the Dropbox or Assignment 1 content page, for easier access.

**Spiro:**
- Overall, the lab served as a great introduction to software testing, presenting concepts in a clear and structured manner that made it accessible for beginners. Using the tool Jira was especially beneficial, as these platforms are widely used in real-world applications. While the lab was not particularly challenging, it provided a solid foundation for more advanced testing methods that we will encounter later in the course.

**Dylan:**
- The lab documents were detailed and mostly easy to follow, though the instructions for the Regression Testing section could have been clearer. The integration of GitHub Classroom was a nice addition, and in future labs, it will offer a valuable opportunity to learn version control for those who are unfamiliar with it. Overall, the tasks in this lab provided a broad overview of different testing approaches, making it a strong introduction to software testing.

**Issy:**
- This lab provided an intuitive and practical introduction to software testing. It effectively simulated a high-level testing process similar to those used in the industry, making it particularly valuable for someone like me who is not deeply familiar with quality assurance practices.
