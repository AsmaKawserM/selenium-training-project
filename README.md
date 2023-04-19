## Project- Cucumber-Selenium Test Automation Framework

Main purpose of the project is to test- loging in to a website and placing an order.
This project was made using the complete BDD automation framework template for web functional testing using Java, Cucumber and Selenium.
The template was based on the Page Object model, and it provided all the required pieces to start creating page classes and tests cases.
This project was written using IntelliJ IDEA Community Edition.


## Execution methods:
Test execution is triggered by "mvn test" command in a terminal from the project directory. 
  - `mvn test`: takes test properties values from test.properties file

## Requirements
- Java JDK (11+)
- Maven

## Main Libraries
- Cucumber-7 with Junit-5
- Selenium 4.8

## Project Structure Overview
The project contains 2 major modules: 

- `main` contains all the elements required to interact with the web application, such as the Selenium WebDriver, page classes,
and helper classes and methods. 

- `test` contains the test properties management, test steps and feature files for the test execution. Basically, code 
in `test` calls web automation functionalities existing in `main`.






**In main:**

2. Create page classes under `pages`. Make new pages classes to extend `Page` class, which contains commonly used methods 
to interact with a web page using Selenium. Page classes must receive `AppSession` as an argument in the constructor, which 
contains the properties for the current session and the `DriverManager`.Then, add the element locators and methods 
for that page. Take `pages.Home` as an example. 
3. Add new page classes to the constructor of `app.PageManager` class. Take the existing examples as a reference.
4. Add any other property that needs to be passed to the page classes in the `app.AppSession` class. This template 
has already some predefined. 
5. Customize the creation of the web drivers in `app.DriverManager`. Add arguments and preferences as required. 
**Note: the DriverManager is using the [Selenium Manager(Beta)](https://www.selenium.dev/documentation/webdriver/getting_started/install_drivers/#1-selenium-manager-beta) approach to create the driver, which doesn't require the
driver files. Modify the `DriverManager` with any other suggested approach from Selenium if required.**

**In test:**

6. Define `test.properties` as required. To test on firefox and/or edge, change the browser on `test.properties`. For each property defined, make sure it is retrieved by `properties.TestProps` class either as mandatory or with a default value. By doing this, properties can be accessed easily from anywhere in the code.
**Note: test.properties is usually not shared in a repository since it might contain sensitive information like credentials**
7. Configure `properties.TestContext` to initialize `AppSession`, `PageManager` and to set session properties. `TestContext` is 
used to share properties across test steps using dependency injection, specifically [cucumber-picocontainer](https://cucumber.io/docs/cucumber/state/?lang=java#picocontainer) for this 
framework. 
8. Create a [test steps](https://cucumber.io/docs/cucumber/step-definitions/?lang=java) file under `testSteps`. 
`@Before` and `@After` steps are included in the `testSteps.CommonSteps` class. For all the test steps file, make sure 
`TestContext testContext` is defined as a parameter in the constructor, this way the properties and objects in TestContext 
are accessible from any test step in the file. Take `testSteps.LoginSteps` as an example.
9. Create [feature files](https://cucumber.io/docs/gherkin/reference/#steps) using existing test steps.
10. Execute tests typing `mvn test` in the terminal.

## Test properties
Test properties, like the app URL, credentials, etc., can be retrieved from several places using the following order of precedence:
1. Command argument `-Dkey=<value>`
2. `test.properties` file
3. Default value (if applicable)

`test.properties` file is located at root directory by default. **Note: test.properties is usually not shared in a 
repository since it might contain sensitive information like credentials**



## Other notes
- Features are run in alphabetical order of the .feature file name
