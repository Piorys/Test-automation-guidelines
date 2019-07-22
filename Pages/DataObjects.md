# Data Objects

To utilize **Data Driven Testing** approach, it is advised to utilize data objects to allow maximum versatility of tests. By switching data objects we can manipulate how the test should behave.

Data objects are .json files that store all necessary data for the test execution such as:
- Credentials
- Environments (*TBC*)
- Product informations
- Expected page messages
...
  
Every data object should be within a separate .json file grouped in functional scope (per scenario) or component-scope (per functional component, ie - products, credentials, page messages)

Example Data Object:
```
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

TBD  
  
