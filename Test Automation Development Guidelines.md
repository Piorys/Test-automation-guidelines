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

## Coding standards

### Variables
- Variable names need to be meaningfull
examples:
```
String successMessage; - GOOD
String sm; - BAD

ProductListPage productListPage; - GOOD
ProductListPage plp; - BAD
```
- All names need to be written in camelCase style

Beginning with the prose form of the name:

From [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html#s5.3-camel-case) 

- Convert the phrase to plain ASCII and remove any apostrophes. For example, "Müller's algorithm" might become "Muellers algorithm".
- Divide this result into words, splitting on spaces and any remaining punctuation (typically hyphens).
    Recommended: if any word already has a conventional camel-case appearance in common usage, split this into its constituent parts (e.g., "AdWords" becomes "ad words"). Note that a word such as "iOS" is not really in camel case per se; it defies any convention, so this recommendation does not apply.
- Now lowercase everything (including acronyms), then uppercase only the first character of:
... each word, to yield upper camel case, or
... each word except the first, to yield lower camel case
- Finally, join all the words into a single identifier.

 Examples:

 - "my account page" -> myAccountPage  
 - "wait for loader" -> waitForLoader

### Page/Component Objects

- Whenever element of the page is seen on multiple pages, consider making it an component object, ie - upperbar/footer 
- When naming new page/component object finish start it with its type, ie - ComponentUpperbar or PageMyAccount
- Keep Component Objects and Page Objects in separate directories
- Keep following scheme of the Page Object or Component Object

```java
/**  package statement */
package pageobjects;
/** importing java-related packages */
import java.util.list;
/** importing test related packages */
import org.openqa.selenium.By;
/** importing frameworks proprietary packages */
import x.y.z.utilities.selenium.pageobjects.BasePO;
import x.y.z.utilities.selenium.pageobjects.Element;
import x.y.z.utilities.common.Reporter;
public class ComponentMinicart extends BasePo {
    /** locators */
	private By cartTitle = By.xpath("//*[contains(@class,'title cc_title')]");
    private By nextButton = By.css('button[name="continue"]')

    /** if function is more complex than jsut returning the text, add comment with following scheme:
        Scope: [Concise information about what function does]
        Accepts: [What function accepts as param]
        Returns: [What is returned]
      */
    public String function getCartTitle(){
        // Log 
        Reporter.addStepLog("Getting Cart Title");
        // Element
        WebElement cartTitleElement = findElement(cartTitle,5);
        // Action 
        return cartTitle.getText()
    }

    public void function clickNextButton(){
        // Log
        Reporter.addStepLog("Clicking on 'next' button");
        // Element
        WebElement nextButtonElement = findElement(nextButton,5);
        // Action
        nextButtonElement.click();
    }
}
```

- Each function should comply with structure as shown above, keep comments as in example. 
General rules for Page/Component Objects:
- Parametrise as much as possible within reason, hardcoding information is not advisable.
- Each Page/Component object needs to be completely separate from other Page/Component objects.


