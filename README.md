# MyFirstSelenium-CSharp
Selenium UI Automation using c# in Visual Studio

	Getting started with Selenium and C# is easy if you have the idea about connecting the right blocks for test code development. In one of the earlier blogs, 	    we covered the Selenium WebDriver architecture in great detail. This is chapter 2 of the Selenium C# tutorial series where we are going to help you set 	    up Selenium in Visual Studio for automated browser testing of your web-application. In chapter 1 we talked about the overview of Selenium C# tutorial               series. We also covered why Selenium C# is a good call for test automation. This chapter, we are going to get down to business and run your first Selenium         C# test automation script.

	In this Selenium C# tutorial, we are going to:

# TABLE OF CONTENT
Creating our first NUnit Project
Writing Your First Selenium C# Test Automation

Step 1: Create a new project of the type ‘NUnit Test Project (.Net Core)’ in Visual Studio.

# create-new-project

Step 2: Give an appropriate name to the project and click Create.

# configure-new-project

Step 3: Since the project is of the type NUnit (.Net Core), the newly created .cs file will contain the basic functionalities of the NUnit framework.

# Nunit-pannel

Step 4: Install the Selenium WebDriver (for Google Chrome) and NUnit framework. Execute the appropriate Package Manager(PM) commands to install the necessary packages.

To execute PM commands from the PM console, navigate to Tools -> NuGet Package Manager -> Package Manager Console.

# PM-console

Execute these commands on the PM console to install Selenium in Visual Studio:

Install-Package Selenium.WebDriver
Install-Package Selenium.Chrome.WebDriver
Similarly, execute the following commands on the PM console to install NUnit:

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
 
            searchText.SendKeys("Selenium using c#");
 
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
 
    	searchText.SendKeys("Selenium using c#");
 
    	......................................
    	......................................
	} 
Now, you can execute the test using the IDE. The status of the tests can be seen using the Test Explorer in Visual Studio. For accessing Test Explorer, go to View Test Explorer.

To build the project and execute all the tests, go to Test 🡪 Run All Tests. On successful execution, you would see a Green test in the Test Explorer window.

nunit-tests
