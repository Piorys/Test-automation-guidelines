# Coding standards

## Variables

* Variable names need to be meaningful and descriptive  

```text
String successMessage; - GOOD
String sm; - BAD

ProductListPage productListPage; - GOOD
ProductListPage plp; - BAD
```

* All names need to be written in camelCase style

From [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html#s5.3-camel-case)

Beginning with the prose form of the name:

* Convert the phrase to plain ASCII and remove any apostrophes. For example, "Muller's algorithm" might become "Mueller algorithm".
* Divide this result into words, splitting on spaces and any remaining punctuation \(typically hyphens\).

    Recommended: if any word already has a conventional camel-case appearance in common usage, split this into its constituent parts \(e.g., "sWords" becomes "ad words"\). Note that a word such as "iOS" is not really in camel case per se; it defies any convention, so this recommendation does not apply.

* Now lowercase everything \(including acronyms\), then uppercase only the first character of:

  ... each word, to yield upper camel case, or

  ... each word except the first, to yield lower camel case

* Finally, join all the words into a single identifier.

  Examples:

  ```text
  "my account page" -> myAccountPage  
  "wait for loader" -> waitForLoader
  ```

* Class-scoped variables should have private access only and be initialized within constructor method

  ```java
  class SomeClass{
    private loginPage;
    private checkoutPage;

    /** Contructor*/
    public SomeClass(){
        loginPage = new PageLogin();
        checkoutPage = new PageCheckout();
    }
  }
  ```

## Function names

* Function name should clearly, without ambiguity indicate what it does, so you don't have to jump across the code to find truth. 
* Every function is an action, therefore name should contain at least one verb that adheres to said action.  
* Like variables, functions should utilize camelCase writing convention.

  examples:

  ```java
  isSomethingvisible();
  clickOnSomeButton(); 
  getThatPageMessageValue();
  doubleClickThatButton();
  fillThisInput();
  selectValueFromAccountDropdown();
  switchToIFrame();
  ```

## Class names

* Class names should be written using MixedCase, with every word having first letter capitalized



  `class SomeClass extends AnotherClass implements YetAnotherClass{}`

```text
## Packages
As per [Oracle](https://docs.oracle.com/javase/tutorial/java/package/namingpkgs.html) standards packages should be written in all lowercase, using dot as a separator which shall group them functionally in appropriate package directories.  

  Example usage:
```java
  import objects.component.Minicart;
  import objects.page.Checkout;
```

Directory structure:

```text
  |--objects:  
        |--component  
            |--Minicart  
        |--page  
            |--Checkout
```

## Brackets

* Use [egyptian-styled](https://blog.codinghorror.com/new-programming-jargon/) brackets whenever possible  

`public static someFunction(){`

`}` 

\`\`

