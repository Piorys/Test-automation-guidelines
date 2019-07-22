# Step Definition Files

Step definition file is meeting point of scenario and all logic implemented within component/page objects. Within this level we are calling the actions defined within lower levels of logic structure. 
  
General rules:
- It is firmly advised to not hard code any data within this level, utilize data objects instead.
- Within push how down narrative, data is passed to page/component objects functions. 
- Assertions are to be made within step definition level, gather data by functions from page/component objects and compare them using [testNG Assert](https://static.javadoc.io/org.testng/testng/6.8.17/org/testng/Assert.html) library 

```java
@Then("^User will see success message about address update")
	public void iWillSeeSuccessMessageAboutAddressUpdate() throws InterruptedException  {
	// Get expected value - TBD
        String expectedMessage = dataParser
        // Get actual value
        String actualMessage = accountDashboard.getSuccessMessage();
        // Assert values
        Assert.assertEquals(actualMessage,expectedMessage);
	}

@Then("^User will not see lite search bar")
    public void userWillNotSeeLiteSearchBar()throws InterruptedException{
        // Get boolean value of element visibility
        Boolean isLogoVisible = upperbar.isLogoVisible();
        // Assert value
        Assert.assertFalse(isLogoVisible);
    }
```
- Data are to be obtained from data objects using DataParser tool (*TBD*)
  
   [<- Go Back](../Readme.md)