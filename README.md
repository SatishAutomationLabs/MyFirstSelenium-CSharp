# MyFirstSelenium-CSharp
Selenium UI Automation using c# for Macbook
Creating our first NUnit Project
Writing Your First Selenium C# Test Automation
Facebook
Twitter
LinkedIn
WhatsApp
Email
Getting started with Selenium and C# is easy if you have the idea about connecting the right blocks for test code development. In one of the earlier blogs, we covered the Selenium WebDriver architecture in great detail. This is chapter 2 of the Selenium C# tutorial series where we are going to help you set up Selenium in Visual Studio for automated browser testing of your web-application. In chapter 1 we talked about the overview of Selenium C# tutorial series. We also covered why Selenium C# is a good call for test automation. This chapter, we are going to get down to business and run your first Selenium C# test automation script.

In this Selenium C# tutorial, we are going to:

TABLE OF CONTENT

Getting Started with Visual Studio 2019
Downloading & Installing Selenium WebDriver
Creating our first NUnit Project
Writing Your First Selenium C# Test Automation
Getting Started with Visual Studio 2019
Visual Studio is the best IDE (Integrated Development Environment) to use for Selenium C# test automation. In this Selenium C# tutorial, we will use the latest version of Visual Studio i.e. (VS 2019).

There are a number of download options available with VS 2019. The non-commercial version is Visual Studio Community, whereas the commercial versions are Visual Studio Professional & Visual Studio Enterprise. For the demonstration in this Selenium C# tutorial series, we would make use of the Community Edition of Visual Studio 2019 for Selenium test automation.

visual-studio-2019

Install the necessary packages for Selenium C# test automation in your operating system.

visual-studio-setup

Note: The license of the Community Edition expires after 30 days of usage. To extend the license, you should sign-in to the IDE. Signing-in also lets you use the other powerful features of Visual Studio such as pushing source code to private Git, syncing Visual Studio settings, and more.

Downloading & Installing Selenium WebDriver
Selenium WebDriver is one of the most popular open-source test automation framework used for automating web application testing. Selenium WebDriver helps to greatly reduce the efforts involved in cross browser testing by automating the test scripts.

Selenium WebDriver Tutorial for Cross Browser Testing

Now, let’s install the Selenium WebDriver for the browser under test on your operating system. Shown below are the locations from where you can download the Selenium WebDriver for popular browsers.

BROWSER
DOWNLOAD LOCATION
Opera	https://github.com/operasoftware/operachromiumdriver/releases
Firefox	https://github.com/mozilla/geckodriver/releases
Chrome	http://chromedriver.chromium.org/downloads
Internet Explorer	https://github.com/SeleniumHQ/selenium/wiki/InternetExplorerDriver
Microsoft Edge	https://blogs.windows.com/msedgedev/2015/07/23/bringing-automated-testing-to-microsoft-edge-through-webdriver/
In this Selenium C# tutorial, we will make use of the Google Chrome for automation testing with Selenium in Visual Studio.

Note: It is recommended to install the Selenium WebDriver executable in the location where the Google Chrome browser is present. That way, you need not mention the location of the Selenium WebDriver when invoking the same in your test implementation.

application-path

Creating our first NUnit Project for Selenium C# in Visual Studio
Now, you have installed Visual Studio 2019 along with the Selenium WebDriver for Google Chrome. You are all set to execute your first Selenium C# testing script through the NUnit framework.

NUnit is a test automation framework that helps to perform Selenium C# testing with much ease. In this chapter of the Selenium C# tutorial series, we will touch upon basic aspects of NUnit such as the installation of the framework along with installing the Selenium WebDriver for the test project. We will talk more about NUnit as we go forward. For now, let get your first Selenium C# example script running through NUnit.

You will need to create an NUnit project for running an automation script using Selenium in Visual Studio. Here are the steps to create an NUnit project for Selenium C# development:

Step 1: Create a new project of the type ‘NUnit Test Project (.Net Core)’ in Visual Studio.

create-new-project

Step 2: Give an appropriate name to the project and click Create.

configure-new-project

Step 3: Since the project is of the type NUnit (.Net Core), the newly created .cs file will contain the basic functionalities of the NUnit framework.

Nunit-pannel

Step 4: Install the Selenium WebDriver (for Google Chrome) and NUnit framework. Execute the appropriate Package Manager(PM) commands to install the necessary packages.

To execute PM commands from the PM console, navigate to Tools -> NuGet Package Manager -> Package Manager Console.

PM-console

Execute these commands on the PM console to install Selenium in Visual Studio:

Install-Package Selenium.WebDriver
Install-Package Selenium.Chrome.WebDriver
1
2
Install-Package Selenium.WebDriver
Install-Package Selenium.Chrome.WebDriver
Similarly, execute the following commands on the PM console to install NUnit:

Install-Package NUnit
Install-Package NUnit3TestAdapter
1
2
Install-Package NUnit
Install-Package NUnit3TestAdapter
Below are some of the screenshots of the execution:

Nunit-execution

package-manager-console

manager-console

Step 5: To verify the status of the package installation, execute the Get-Package command on the PM console.

PM> Get-Package
 
Id                                  Versions
--                                  --------                                          
Selenium.WebDriver                  {3.141.0}
Selenium.Chrome.WebDriver           {79.0.0}
...... ......
...... ......
1
2
3
4
5
6
7
8
PM> Get-Package
 
Id                                  Versions
--                                  --------                                          
Selenium.WebDriver                  {3.141.0}
Selenium.Chrome.WebDriver           {79.0.0}
...... ......
...... ......
Writing Your First Selenium C# Test Automation
In this section of Selenium C# tutorial, we look at the following test scenario:

Navigate to the URL https://www.google.com.
Locate the search-box on the page.
Enter the search item as LambdaTest and click Google Search.
We are using a basic test scenario that uses the bare minimum annotations of the NUnit framework. It is just to get you started with Selenium test automation using a test framework like NUnit.

using NUnit.Framework;
using OpenQA.Selenium;
using OpenQA.Selenium.Chrome;
using System;
 
namespace CsharpSeleniumUI
{
    class FirstSeleniumUI
    {
        String test_url = "https://www.google.com";
 
        IWebDriver driver;
 
        [SetUp]
        public void start_Browser()
        {
            // Local Selenium WebDriver
            driver = new ChromeDriver();
            driver.Manage().Window.Maximize();
        }
 
        [Test]
        public void FirstUITest()
        {
            driver.Url = test_url;
 
            System.Threading.Thread.Sleep(2000);
 
            IWebElement searchText = driver.FindElement(By.CssSelector("[name = 'q']"));
 
            searchText.SendKeys("Selenium Test");
 
            IWebElement searchButton = driver.FindElement(By.XPath("//div[@class='FPdoLc tfB0Bf']//input[@name='btnK']"));
 
            searchButton.Click();
 
            System.Threading.Thread.Sleep(6000);
 
            Console.WriteLine("Test Passed");
        }
 
        [TearDown]
        public void close_Browser()
        {
            driver.Quit();
        }
    }
}

As seen in the above implementation, the Chrome WebDriver is initiated in the code implemented under the [SetUp] attribute.

[SetUp]
public void start_Browser()
{
	// Local Selenium WebDriver
	driver = new ChromeDriver();
	driver.Manage().Window.Maximize();
}
The test implementation is under the [Test] attribute. The necessary web elements are located using the Inspect Tool in Google Chrome.

[Test]
public void test_search()
{
    driver.Url = test_url;
    System.Threading.Thread.Sleep(2000);
    IWebElement searchText = driver.FindElement(By.CssSelector("[name = 'q']"));
 
    searchText.SendKeys("LambdaTest");
 
    ......................................
    ......................................
} 
Now, you can execute the test using the IDE. The status of the tests can be seen using the Test Explorer in Visual Studio. For accessing Test Explorer, go to View 🡪 Test Explorer.

To build the project and execute all the tests, go to Test 🡪 Run All Tests. On successful execution, you would see a Green test in the Test Explorer window.

nunit-tests
