﻿<a name="HOLTop" />
# Introduction to ASP.NET 5 & ASP.NET MVC 6 #

---

<a name="Overview" />
## Overview ##

ASP.NET 5 is a new open-source and cross-platform framework for building modern cloud-based Web applications using .NET. It was built from the ground up to provide an optimized development framework for apps that are either deployed to the cloud or run on-premises. It consists of modular components with minimal overhead, so you retain flexibility while constructing your solutions. You can develop and run your ASP.NET 5 applications cross-platform on Windows, Mac and Linux. ASP.NET 5 is fully open source on [GitHub](https://github.com/aspnet/home).

ASP.NET 5 is built with the needs of modern Web applications in mind, including a unified story for building Web UI and Web APIs that integrate with today’s modern client-side frameworks and development workflows. ASP.NET 5 is also built to be cloud-ready by introducing environment-based configuration and by providing built-in dependency injection support.

<a name="Objectives" />
### Objectives ###
In this hands-on lab, you will learn how to:

- Create a Web site based on the **ASP.NET 5** template
- Build Web UI and Web APIs in the same project
- Identify the main components of an **ASP.NET 5** application
- Take advantage of the **ASP.NET Scaffolding** framework to automatically create Controllers and Views to perform CRUD operations based on your model classes
- Expose the same set of information in machine- and human-readable formats using the right tool for each job

<a name="Prerequisites"></a>
### Prerequisites ###

The following is required to complete this hands-on lab:

- [Visual Studio Community 2015][1] or greater

[1]: https://www.visualstudio.com/products/visual-studio-community-vs

<a name="Setup" />
### Setup ###
In order to run the exercises in this hands-on lab, you will need to set up your environment first.

1. Open Windows Explorer and browse to the lab's **Source** folder.
1. Right-click on **Setup.cmd** and select **Run as administrator** to launch the setup process that will configure your environment and install the Visual Studio code snippets for this lab.
1. If the User Account Control dialog box is shown, confirm the action to proceed.

> **Note:** Make sure you have checked all the dependencies for this lab before running the setup.

<a name="CodeSnippets" />
### Using the Code Snippets ###

Throughout the lab document, you will be instructed to insert code blocks. For your convenience, most of this code is provided as Visual Studio Code Snippets, which you can access from within Visual Studio 2015 to avoid having to add it manually. 

>**Note**: Each exercise is accompanied by a starting solution located in the **Begin** folder of the exercise that allows you to follow each exercise independently of the others. Please be aware that the code snippets that are added during an exercise are missing from these starting solutions and may not work until you have completed the exercise. Inside the source code for an exercise, you will also find an **End** folder containing a Visual Studio solution with the code that results from completing the steps in the corresponding exercise. You can use these solutions as guidance if you need additional help as you work through this hands-on lab.

---

<a name="Exercises" />
## Exercises ##
This hands-on lab includes the following exercises:

1. [Creating a New ASP.NET 5 Web Application Project](#Exercise1)
1. [Creating an MVC Controller Using Scaffolding](#Exercise2)
1. [Creating a Web API Controller Using Scaffolding](#Exercise3)

Estimated time to complete this lab: **60 minutes**

>**Note:** When you first start Visual Studio, you must select one of the predefined settings collections. Each predefined collection is designed to match a particular development style and determines window layouts, editor behavior, IntelliSense code snippets, and dialog box options. The procedures in this lab describe the actions necessary to accomplish a given task in Visual Studio when using the **General Development Settings** collection. If you choose a different settings collection for your development environment, there may be differences in the steps that you should take into account.

<a name="Exercise1" />
### Exercise 1: Creating a New ASP.NET 5 Web Application Project ###

In this exercise you will create a new ASP.NET 5 Web Application project in Visual Studio 2015. You will then explore the generated solution and identify its parts, and finally you will see the Web site in action.

<a name="Ex1Task1" />
#### Task 1 - Creating a New Site Using the One ASP.NET Experience ####

In this task you will start creating a new Web site in Visual Studio based on the **ASP.NET 5 Web Application** project template.

1. Open **Visual Studio Community 2015** and select **File | New Project...** to start a new solution.

	![Creating a New Project](Images/creating-a-new-project.png?raw=true "Creating a New Project")

	_Creating a New Project_

1. In the **New Project** dialog box, select **ASP.NET Web Application** under the **Visual C# | Web** tab, and make sure **.NET Framework 4.6** is selected. Name the project _MyWebApplication_, choose a **Location** and click **OK**.

	![New ASP.NET Web Application project](Images/creating-new-aspnet-web-application-project.png?raw=true "New ASP.NET Web Application project")

	_Creating a new ASP.NET Web Application project_

1. In the **New ASP.NET Project** dialog box, select the **Web Application** template under **ASP.NET 5 Templates**. Also, make sure that the **Authentication** option is set to **Individual User Accounts**. Click **OK** to continue.

	![Creating a new project with the ASP.NET 5 Web Application template](Images/creating-a-new-aspnet5-project.png?raw=true "Creating a new project with the ASP.NET 5 Web Application template")

	_Creating a new project with the ASP.NET 5 Web Application template_

1. You can now explore the structure of the generated solution.

	![Exploring the generated solution](Images/exploring-the-generated-solution.png?raw=true "Exploring the generated solution")

	_Exploring the generated solution_

	1. **global.json:** This file is used to configure the solution as a whole. It includes just two sections, projects and sdk by default.
	1. **References**: This folder details the server-side references for the project which might be assemblies, NuGet packages, or projects.
	1. **wwwroot:** This special folder represents the actual root of the web app when running on a web server. Resources like images, script files and stylesheets are located inside this folder.
	1. **Dependencies:** This section contains two subfolders: **Bower** and **NPM**. These folders correspond to two package managers by the same names, and they’re used to pull in client-side dependencies and tool.
	1. **Migrations:** This folder contains the Entity Frameworks migrations. This folder is added when the **Individual User Accounts** authentication option is selected during the configuration of the project template.
	1. **Models:** This folder will contain the classes that represent your application data.
	1. **Controllers**, **ViewModels**, **Views** and **Services**: These folders are related with **ASP.NET MVC** components. Except for the Controllers folder, these folders are added when the **Individual User Accounts** authentication option is selected during the configuration of the project template. You will explore the MVC and Web API technologies in the next exercises.
	1. **appsettings.json:** This file contains the configurations like connection strings and logging levels.
	1. **gulpfile.js:** This file contains the Gulp tasks for the project.
	1. **project.json:** This file is used to define the project’s server side dependencies, as well as other project-specific information.
	1. **Startup.cs:** class file wires up configuration, MVC, EF, Identity services, logging, routes, and more. It provides a good example for how to configure the services used by your ASP.NET app.

1. Double-click the **Index.cshtml** file located inside the _Views/Home_ folder, to explore the content of the page.

	![Exploring the Index.cshtml page](Images/index-page.png?raw=true "Exploring the Index.cshtml page")

	_Exploring the Index.cshtml page_

1. Double-click the **_Layout.cshtml** file located inside the _Views/Shared_ folder, to explore the layout of the page.

	![Exploring the _Layout.cshtml page](Images/layout-page.png?raw=true "Exploring the _Layout.cshtml page")

	_Exploring the _Layout.cshtml page_

1. Open the **Startup.cs** file. In the _Startup_ class you will find the wires up configuration. At the end of the **Configure** method, you will find the configuration which maps HTTP routes to **controllers**.

	<!-- mark:5-10 -->
	````C#
    public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
    {
        // ...

        app.UseMvc(routes =>
        {
            routes.MapRoute(
                name: "default",
                template: "{controller=Home}/{action=Index}/{id?}");
        });
    }
	````

<a name="Ex1Task2" />
#### Task 2 - Running the Solution ####

In this task you will run the generated solution, explore the app and some of its features, like URL rewriting and built-in authentication.

1. To run the solution, press **F5** or click the **Start** button located on the toolbar. The application home page should open in the browser.

	![Running the solution](Images/running-the-solution.png?raw=true "Running the solution")

	_Running the solution_

1. Verify the configured routes. To do this, append **/Home/Contact** to the URL in the address bar and press **Enter**.

	![Navigating to the Contact action](Images/navigating-to-contacts.png?raw=true "Navigating to the Contact action")

	_Navigating to the Contact action_

1. You will now explore the authentication flow integrated into the application. To do this, click **Register** in the upper-right corner of the page.

	![Registering a new user](Images/registering-a-new-account.png?raw=true "Registering a new user")

	_Registering a new user_

1. In the **Register** page, enter an **Email** and **Password**, and then click **Register**.

	![Register page](Images/register-page.png?raw=true)

	_Register page_

1. You will be prompt with the following error page that indicates that applying the migrations may resolve the issue. Click **Apply Migrations** and refresh the page once this action is completed.

	![Applying the migrations](Images/applying-the-migrations.png?raw=true "Applying the migrations")

	_Applying the migrations_

1. The application registers the new account, and the user is authenticated.

	![User authenticated](Images/user-authenticated.png?raw=true)

	_User authenticated_

1. Go back to Visual Studio and press **SHIFT + F5** to stop debugging.

<a name="Exercise2" />
### Exercise 2: Creating an MVC Controller Using Scaffolding ###
In this exercise you will take advantage of the ASP.NET Scaffolding framework provided by Visual Studio to create an ASP.NET MVC 6 controller with actions and Razor views to perform CRUD operations, without writing a single line of code. The scaffolding process will use Entity Framework Code First to generate the data context and the database schema in the SQL database.

**About Entity Framework Code First**

Entity Framework (EF) is an object-relational mapper (ORM) that enables you to create data access applications by programming with a conceptual application model instead of programming directly using a relational storage schema.

The Entity Framework Code First modeling workflow allows you to use your own domain classes to represent the model that EF relies on when performing querying, change-tracking and updating functions. Using the Code First development workflow, you do not need to begin your application by creating a database or specifying a schema. Instead, you can write standard .NET classes that define the most appropriate domain model objects for your application, and Entity Framework will create the database for you.

> **Note:** You can learn more about Entity Framework [here](http://www.asp.net/entity-framework).

<a name="Ex2Task1" />
#### Task 1 - Creating a New Model ####

You will now define a **Person** class, which will be the model used by the scaffolding process to create the MVC controller and the views. You will start by creating a **Person** model class, and the CRUD operations in the controller will be automatically created using scaffolding features.

1. Open **Visual Studio Community 2015** and the **MyWebApplication.sln** solution located in the **Source/Ex2-MvcScaffolding/Begin** folder. Alternatively, you can continue with the solution that you obtained in the previous exercise.

1. In **Solution Explorer**, right-click the **Models** folder of the **MyWebApplication** project and select **Add | Class...**.

	![Adding the Person model class](Images/adding-the-person-model-class.png?raw=true "Adding the Person model class")

	_Adding the Person model class_

1. In the **Add New Item** dialog box, name the file _Person.cs_ and click **Add**.

	![Creating the Person model class](Images/creating-the-person-model-class.png?raw=true "Creating the Person model class")

	_Creating the Person model class_

1. Replace the content of the **Person.cs** file with the following code. Press **CTRL + S** to save the changes.

	(Code Snippet - _IntroASPNET5 - Ex2 - PersonClass_)
	<!-- mark:1-11 -->
	````C#
    namespace MyWebApplication.Models
    {
        public class Person
        {
            public int Id { get; set; }

            public string Name { get; set; }

            public int Age { get; set; }
        }
    }
	````

1. In **Solution Explorer**, right-click the **MyWebApplication** project and select **Build**, or press **CTRL + SHIFT + B** to build the project.

<a name="Ex2Task2" />
#### Task 2 - Creating an MVC Controller ####

Now that the **Person** model is created, you will use ASP.NET MVC scaffolding with Entity Framework to create the CRUD controller actions and views for **Person**.

1. In **Solution Explorer**, right-click the **Controllers** folder of the **MyWebApplication** project and select **Add | New Scaffolded Item...**.

	![Creating a new scaffolded Controller](Images/creating-a-new-scaffolded-controller.png?raw=true "Creating a new Scaffolded Controller")

	_Creating a new Scaffolded Controller_

1. In the **Add Scaffold** dialog box, select **MVC 6 Controller with views, using Entity Framework** and then click **Add.**

	![Selecting MVC 6 Controller with views and Entity Framework](Images/selecting-mvc-6-controller.png?raw=true "Selecting MVC 6 Controller with views and Entity Framework")

	_Selecting MVC 6 Controller with views and Entity Framework_

1. Set _MvcPersonController_ as the **Controller name**, select the **Use async controller actions** option and select **Person (MyHybridSite.Models)** as the **Model class**.

	![Adding an MVC controller with scaffolding](Images/adding-an-mvc-controller-with-scaffolding.png?raw=true "Adding an MVC controller with scaffolding")

	_Adding an MVC controller with scaffolding_

1. Under **Data context class**, click **New data context** button. 

	![Creating a new data context](Images/creating-a-new-data-context.png?raw=true "Creating a new data context")

	_Creating a new data context_

1. In the **New Data Context** dialog box, name the new data context _PersonContext_ and click **Add**.

	![Creating the new PersonContext](Images/creating-the-new-personcontext.png?raw=true "Creating the new PersonContext")

	_Creating the new PersonContext type_

1. Click **Add** to create the new controller for **Person** with scaffolding. Visual Studio will then generate the controller actions, the Person data context and the Razor views.

	![After creating the MVC controller with scaffolding](Images/after-creating-the-mvc-controller-with-scaffo.png?raw=true "After creating the MVC controller with scaffolding")

	_After creating the MVC controller with scaffolding_

1. Open the **MvcPersonController.cs** file in the **Controllers** folder. Notice that the CRUD action methods have been generated automatically. 

	````C#
    // ...

    // POST: MvcPeople/Create
    [HttpPost]
    [ValidateAntiForgeryToken]
    public async Task<IActionResult> Create(Person person)
    {
        if (ModelState.IsValid)
        {
            _context.Person.Add(person);
            await _context.SaveChangesAsync();
            return RedirectToAction("Index");
        }
        return View(person);
    }

    // GET: MvcPeople/Edit/5
    public async Task<IActionResult> Edit(int? id)
    {
        if (id == null)
        {
            return HttpNotFound();
        }

        Person person = await _context.Person.SingleAsync(m => m.Id == id);
        if (person == null)
        {
            return HttpNotFound();
        }
        return View(person);
    }

    // ...
````

	> **Note:** By selecting the **Use async controller actions** check box from the scaffolding options in the previous steps, Visual Studio generates asynchronous action methods for all actions that involve access to the Person data context. It is recommended that you use asynchronous action methods for long-running, non-CPU bound requests to avoid blocking the Web server from performing work while the request is being processed.

<a name="Ex2Task3" />
#### Task 3 - Running the Solution ####

In this task, you will run the solution again to verify that the views for **Person** are working as expected. You will add a new person to verify that it is successfully saved to the database. 

1. Press **F5** to run the solution.

1. Navigate to **/MvcPerson**. The scaffolded view that shows the list of people should appear.

1. Click **Create New** to add a new person.

	![Navigating to the scaffolded MVC views](Images/navigating-to-the-scaffolded-mvc-views.png?raw=true)

	_Navigating to the scaffolded MVC views_

1. In the **Create** view, provide a **Name** and an **Age** for the person, and click **Create**.

	![Adding a new person](Images/adding-a-new-person.png?raw=true)

	_Adding a new person_

1. The new person is added to the list. In the element list, click **Details** to display the person's details view. Then, in the **Details** view, click **Back to List** to go back to the list view.

	![Person's details view](Images/person-details-view.png?raw=true)

	_Person's details view_

1. Click the **Delete** link to delete the person. In the **Delete** view, click **Delete** to confirm the operation.

	![Deleting a person](Images/deleting-a-person.png?raw=true)

	_Deleting a person_

1. Go back to Visual Studio and press **SHIFT + F5** to stop debugging.

<a name="Exercise3" />
### Exercise 3: Creating a Web API Controller Using Scaffolding ###

HTTP is not just for serving up web pages. It’s also a powerful platform for building APIs that expose services and data. HTTP is simple, flexible, and ubiquitous. Almost any platform that you can think of has an HTTP library, so HTTP services can reach a broad range of clients, including browsers, mobile devices, and traditional desktop apps.

Previous versions of ASP.NET included the Web API framework for creating web APIs. In ASP.NET 5, this functionality has been merged into the MVC 6 framework. Unifying the two frameworks makes it simpler to build apps that include both UI (HTML) and APIs, because now they share the same code base and pipeline.

In this exercise, you will use ASP.NET Scaffolding again to generate a Web API controller. You will use the same **Person** and **PersonContext** classes from the previous exercise to provide the same person data in JSON format. You will see how you can expose the same resources in different ways within the same ASP.NET application.

<a name="Ex3Task1" />
#### Task 1 - Creating a Web API Controller ####

In this task you will create a new **Web API Controller** that will expose the person data in a machine-consumable format like JSON.

1. If not already opened, open **Visual Studio Community 2013** and open the **MyHybridSite.sln** solution located in the **Source/Ex3-WebAPI/Begin** folder. Alternatively, you can continue with the solution that you obtained in the previous exercise.

	>**Note:** If you start with the Begin solution from Exercise 3, press **CTRL + SHIFT + B** to build the solution.

1. In **Solution Explorer**, right-click the **Controllers** folder of the **MyHybridSite** project and select **Add | New Scaffolded Item...**.

	![Creating a new scaffolded Controller](Images/creating-a-new-scaffolded-controller.png?raw=true)

	_Creating a new scaffolded Controller_

1. In the **Add Scaffold** dialog box, select **Web API** in the left pane, then **Web API 2 Controller with actions, using Entity Framework** in the middle pane and then click **Add.**

	![Selecting Web API 2 Controller with actions and Entity Framework](Images/selecting-web-api-2-controller.png?raw=true "Selecting Web API 2 Controller with actions and Entity Framework")

	_Selecting Web API 2 Controller with actions and Entity Framework_

1. Set _ApiPersonController_ as the **Controller name**, select the **Use async controller actions** option and select **Person (MyHybridSite.Models)** and **PersonContext (MyHybridSite.Models)** as the **Model** and **Data context** classes respectively. Then click **Add**.

	![Adding a Web API Controller with scaffolding](Images/adding-a-web-api-controller-with-scaffolding.png?raw=true "Adding a Web API controller with scaffolding")

	_Adding a Web API controller with scaffolding_

1. Visual Studio will then generate the **ApiPersonController** class with the four CRUD actions to work with your data.

	![After creating the Web API controller with scaffolding](Images/after-creating-the-web-api-controller.png?raw=true "After creating the Web API controller with scaffolding")

	_After creating the Web API controller with scaffolding_

1. Open the **ApiPersonController.cs** file and inspect the _GetPeople_ action method. This method queries the db field of **PersonContext** type in order to get the people data.

	<!--mark: 4-->
	````C#
	// GET api/ApiPerson
	public IQueryable<Person> GetPeople()
	{
		return db.People;
	}
	````

1. Now notice the comment above the method definition. It provides the URI that exposes this action which you will use in the next task.

	<!--mark: 1-->
	````C#
	// GET api/ApiPerson
	public IQueryable<Person> GetPeople()
	{
		return db.People;
	}
	````

	>**Note:** By default, Web API is configured to catch the queries to the _/api_ path to avoid collisions with MVC controllers. If you need to change this setting, refer to [Routing in ASP.NET Web API](http://www.asp.net/web-api/overview/web-api-routing-and-actions/routing-in-aspnet-web-api). 


<a name="Ex3Task2" />
#### Task 2 - Running the Solution ####

In this task you will use the Internet Explorer **F12 developer tools** to inspect the full response from the Web API controller. You will see how you can capture network traffic to get more insight into your application data.

> **Note:** Make sure that **Internet Explorer** is selected in the **Start** button located on the Visual Studio toolbar.
>
> ![Internet Explorer option](Images/internet-explorer-option.png?raw=true)
>
>The **F12 developer tools** have a wide set of functionality that is not covered in this hands-on-lab. If you want to learn more about it, refer to [Using the F12 developer tools](http://msdn.microsoft.com/library/ie/bg182326\(v=vs.85\)).

1. Press **F5** to run the solution.

	>**Note:** In order to follow this task correctly, your application needs to have data. If your database is empty, you can go back to Task 3 in Exercise 2 and follow the steps on how to create a new person using the MVC views. 

1. In the browser, press **F12** to open the **Developer Tools** panel. Press **CTRL** + **4** or click the **Network** icon, and then click the green arrow button to begin capturing network traffic.

	![Initiating Web API network capture](Images/initiating-web-api-network-capture.png?raw=true "Initiating Web API network capture")

	_Initiating Web API network capture_

1. Append **api/ApiPerson** to the URL in the browser's address bar. You will now inspect the details of the response from the **ApiPersonController**.

	![Retrieving person data through Web API](Images/retrieving-person-data-through-web-api.png?raw=true "Retrieving person data through Web API")

	_Retrieving person data through Web API_

	>**Note:** Once the download finishes, you will be prompted to make an action with the downloaded file. Leave the dialog box open in order to be able to watch the response content through the Developers Tool window.

1. Now you will inspect the body of the response. To do this, click the **Details** tab and then click **Response body**. You can check that the downloaded data is a list of objects with the properties **Id**, **Name** and **Age** that correspond to the **Person** class.

	![Viewing Web API Response Body](Images/viewing-web-api-response-body.png?raw=true "Viewing Web API Response Body")

	_Viewing Web API Response Body_

<a name="Ex3Task3" />
#### Task 3 - Adding Web API Help Pages ####

When you create a Web API, it is useful to create a help page so that other developers will know how to call your API. You could create and update the documentation pages manually, but it is better to auto-generate them to avoid having to do maintenance work. In this task you will use a Nuget package to automatically generate Web API help pages to the solution.

1. From the **Tools** menu in Visual Studio, select **Library Package Manager**, and then click **Package Manager Console**. 

1. In the **Package Manager Console** window, execute the following command:

	````NuGet
	Install-Package Microsoft.AspNet.WebApi.HelpPage
	````

	>**Note:** The **Microsoft.AspNet.WebApi.HelpPage** package installs the necessary assemblies and adds MVC Views for the help pages under the **Areas/HelpPage** folder.

	![HelpPage Area](Images/helppage-area.png?raw=true "HelpPage Area")

	_HelpPage Area_

1. By default, the help pages have placeholder strings for documentation. You can use XML documentation comments to create the documentation. To enable this feature, open the **HelpPageConfig.cs** file located in the **Areas/HelpPage/App_Start** folder and uncomment the following line:

	````C#
	config.SetDocumentationProvider(new XmlDocumentationProvider(HttpContext.Current.Server.MapPath("~/App_Data/XmlDocument.xml")));
	````
1. In **Solution Explorer**, right-click the project **MyHybridSite**, select **Properties** and click the **Build** tab.

	![Build tab](Images/build-section.png?raw=true "Build section")

	_Build tab_

1. Under **Output**, select **XML documentation file**. In the edit box, type **App_Data/XmlDocument.xml**.

	![Output section in Build tab](Images/output-section-in-build-tab.png?raw=true "Output section in build tab")

	_Output section in Build tab_

1. Press **CTRL** + **S** to save the changes.

1. Open the **ApiPersonController.cs** file from the **Controllers** folder.

1. Enter a new line between the _GetPeople_ method signature and the _// GET api/ApiPerson_ comment, and then type three forward slashes.

	>**Note:** Visual Studio automatically inserts the XML elements which define the method documentation.

1. Add a summary text and the return value for the _GetPeople_ method. It should look like the following.

	````C#
	// GET api/ApiPerson
	/// <summary>
	/// Documentation for 'GET' method
	/// </summary>
	/// <returns>Returns a list of people in the requested format</returns>
	public IQueryable<Person> GetPeople()
	{
		return db.People;
	}
	````

1. Press **F5** to run the solution.

1. Append **/help** to the URL in the address bar to browse to the help page.

	![ASP.NET Web API Help Page](Images/aspnet-web-api-help-page.png?raw=true "ASP.NET Web API Help Page")
	
	_ASP.NET Web API Help Page_

	>**Note:** The main content of the page is a table of APIs, grouped by controller. The table entries are generated dynamically, using the **IApiExplorer** interface. If you add or update an API controller, the table will be automatically updated the next time you build the application.
	>
	>The **API** column lists the HTTP method and relative URI. The **Description** column contains information that has been extracted from the method's documentation.

1. Note that the description you added above the method definition is displayed in the description column.

	![API method description](Images/api-method-description.png?raw=true "API method description")

	_API method description_

1. Click one of the API methods to navigate to a page with more detailed information, including sample response bodies.

	![Detail Information page](Images/detail-information-page.png?raw=true "Detail Information page")

	_Detailed information page_

---

<a name="Summary" />
## Summary ##

By completing this hands-on lab you have learned how to:

- Create a new Web application using the One ASP.NET Experience in Visual Studio 2015
- Integrate multiple ASP.NET technologies into one single project
- Generate MVC controllers and views from your model classes using ASP.NET Scaffolding
- Generate Web API controllers, which use features such as Async Programming and data access through Entity Framework
- Automatically generate Web API Help Pages for your controllers