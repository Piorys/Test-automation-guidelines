# Page/Component Objects

* Whenever element of the page is seen on multiple pages, consider making it an component object, ie - upperbar/footer 
* Keep Component Objects and Page Objects in separate directories
* Keep following scheme of the Page Object or Component Object

```java
/**  package statement */
package objects.component;
/** importing java-related packages */
import java.util.list;
/** importing test related packages */
import org.openqa.selenium.By;
/** importing frameworks proprietary packages */
import x.y.z.utilities.selenium.pageobjects.BasePO;
import x.y.z.utilities.selenium.pageobjects.Element;
import x.y.z.utilities.common.Reporter;


public class Minicart extends BasePo {
    /** locators */
    private By cartTitle = By.xpath("//*[contains(@class,'title cc_title')]");
    private By nextButton = By.css('button[name="continue"]')
    private By commentField = By.css('input[name="orderComments"]')

    /** if function is more complex than just for example returning the text or clicking an simple button, add comment with following scheme:
        Scope: [Concise information about what function does]
        Accepts: [What function accepts as param]
        Returns: [What is returned]
      */
    public String getCartTitle(){
        // Log 
        Reporter.addStepLog("Getting Cart Title");
        // Element
        WebElement cartTitleElement = findElement(cartTitle,5);
        // Action 
        return cartTitle.getText()
    }

    public void fillCommentField(String comment){
        // Log
        Reporter.addStepLog("Filling order comment field with "+comment);
        // Element
        WebElement commentFieldElement = findElement(commentField,5);
        // Action
        commentFieldElement.sendKeys(comment);
    }


    public void clickNextButton(){
        // Log
        Reporter.addStepLog("Clicking on 'next' button");
        // Element
        WebElement nextButtonElement = findElement(nextButton,5);
        // Action
        nextButtonElement.click();
    }
}
```

* Each function should comply with structure as shown above, keep comments as in example.  

General rules for Page/Component Objects:

* Parametrize as much as possible within reason, hard coding information is not advisable.
* If selector relies on some data that could change, consider creating a function that will return desired object  

  example:

  \`\`\`java

  // Unadvisable

  private By profileName = By.xpath\("//button\[@id='userDropdown'\]//span//span\[@class='invitation'\]\[contains\(text\(\),'Magda'\)\]"\);

// Better put it within function

public By getProfileNameByElement\(String profileName\){ // Log Reporter.addStepLog\("Constructing 'By' element for profile name"\); // Element String locator = "//button\[@id='userDropdown'\]//span//span\[@class='invitation'\]\[contains\(text\(\),'" + profileName + "'\)\]"; // Action return By.xpath\(locator\); }

```text
- Each Page/Component object needs to be completely separate from other Page/Component objects.
- Keep functions as granular as possible within reason, keep Single Responsibility Principle in mind. One function should do exactly one thing. Functions can be grouped in one in accordance to business logic if needed, ie 


```java
public void passCredentialsAndLogin(String username, String password){
    // Log
    Reporter.addStepLog("Passing credentials and clicking 'login'");
    // Action
    this.fillUsername(username);
    this.fillPassword(password);
    this.clickLoginButton();
}
```

