# Test Automation Development Guidelines

This document was created in order to unify test automation development on [PROJECT] project.

## Gitflow

![Gitflow](Assets/gitflow.png)

**Branches:** 
- **Master Branch** - Main branch of the repository, only User Stories automation that has been validated and tested can reside within it.
- **Develop Branch** - Transitory branch of the repository, place for User Stories that were scripted but not tested in integration. 
- **User Story Branch** - Working branch, for each User Story new branch should be created with complaince to naming convention as below: 

``` US_[Number] [Jira ticket ID] ex. US_1 ECOMM_1234 ```
- **Fix Branch** - *Ad hoc* branch created in case of failed integration testing of batch of user stories. For each fix new branch should be created with compliance to naming convention as below:

```US_[Numbers] int fix ex. US_1,2,3,4 int fix```

**Workflow**

![Workflow](Assets/workflow.png)

**Legend:**
- **Review and Test of scripts** - Code created during automation of user story is reviewed both by static code review, and by dynamic review during execution of scenarios agains the environment.
- **Integration Tests off multiple US** - All Test Cases developed  are executed at once in functional groups (iteration/suites) in order to check potential conflicts 

**Steps:**
1. Test Team designates user stories for automation, distrtibutes it within team.
2. Test Developer clones repository to local machine or pulls newest code.
3. Test Developer creates User Story branch from Develop Branch 
4. Test Developer develops automated test cases for given user story
5. Test Developer opens pull request to develop branch
6. Test Team Lead or designated Test Developer performs code review and executes created test cases agains environment
7. If Code Review and Test is passed successfully, pull request is accepted and codebase is merged to develop branch. If Code Review or Test fails, Test Developer introduces neccesary changes and step 6 is repeated.
8. After gathering all user stories from designated batch (see pt 1) Test Team Lead or designated Test Developer performs integration testing by executing all automated test cases against environment. 
9. If Integration Test passes, codebase is merged with Master branch with appropriate tag. If Integration Test fails, Test Team Lead or designated Test Developer creates fix branch and introduces neccesary changes, and step 8 is repeated.


**Rules** 
- Direct pushing to master branch is **forbidden**. Master branch can only be updated by merging with develop branch
- Direct pushing to develop branch is **unadvisable**. On edge cases such as typo fix during steps 7 or 9 pushing is allowed after consulting with Test Team Lead


