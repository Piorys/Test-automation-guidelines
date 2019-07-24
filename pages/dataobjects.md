# Data Objects

To utilize **Data Driven Testing** approach, it is advised to utilize data objects to allow maximum versatility of tests. By switching data objects we can manipulate how the test should behave.

Data objects are .json files that store all necessary data for the test execution such as:

* Credentials
* Environments \(_TBC_\)
* Product informations
* Expected page messages

  ...

Every data object should be within a separate .json file grouped in functional scope \(per scenario\) or component-scope \(per functional component, ie - products, credentials, page messages\)

Example Data Object:

```text
{
    "Customer":{
        "Username":"xyz@gmail.com"
        "Password":"Some_P@$$word2137_!"
    },
    "Admin":{
        "Username":"admin@domain.com",
        "Password":"Fz#@124kjiy*&(gG"
    }
}
```

## Data Parser

In order to access JSON data files a DataParser should be introduced..

Example Data Parser for Java language can be found on repository - [https://github.com/Piorys/data-parser-java](https://github.com/Piorys/data-parser-java) 

