# Gitflow

![Gitflow](../Assets/gitflow.png)

**Branches:** 
- **Master Branch** - Main branch of the repository, only User Stories automation that has been validated and tested can reside within it.
- **Develop Branch** - Transitory branch of the repository, place for User Stories that were scripted but not tested in integration. 
- **User Story Branch** - Working branch, for each User Story new branch should be created with compliance to naming convention as below: 

``` US_[Number] [Jira ticket ID] ex. US_1 ECOMM_1234 ```
- **Fix Branch** - *Ad hoc* branch created in case of failed integration testing of batch of user stories. For each fix new branch should be created with compliance to naming convention as below:

```US_[Numbers] int fix ex. US_1,2,3,4 int fix```