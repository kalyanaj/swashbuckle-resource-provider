Auto-Generate Swagger Docs in Asp.Net API Apps
=========

This is a sample ASP.Net Web API application to demmonstrate how to use Swashbuckle to automatically generate Swagger 2.0 docs from **ApiController** types in the project.
A live site of this sample project is at http://swashapitest.azurewebsites.net.

##To Run This Example##

* Download the code to the local machine
* Open *SwashApiTest.sln* with Visual Studio 2015
* F5 to run the application. The home page will open in a browser
* Click *Generate Swagger Doc* on the top bar to see the generated Swagger document
* Click *Swagger UI* on the top bar to see the Swagger UI that can be used to try out the API calls

## To Get Started with Swagger Doc Generation##

If you have an ASP.Net Web API application and want to add Swashbuckle support for Swagger doc generation,

* Add NuGet package **Swashbuckle.Core** to your project
* Copy, paste, and add folder **SwashApiTest/Swagger** to your project
* F5 to run your project. The generated Swagger doc should be at *[root]/swagger/docs/2016-04-27dev*. The exposed APIs in the Swagger doc are generated from ApiController type controllers.

##To Customize the Swagger Doc Generation##

With Swashbuckle, you can do a lot of customizations to your Swagger doc generation.

* Open Swagger/SwaggerConfig.cs, update the following to point your Swagger document to a host other than the default.
```
     //swaggerDoc.host = new Uri("http://swashapitest.azurewebsites.net/").Host;
```

* This will set your API name, version and description,

```
     c.SingleApiVersion("2016-04-27dev", "SwashApiTest").Description("Api test client for Swashbuckle");
```

* Currently, it is renaming XXXViewModel classes to XXXView, just for demonstration. You can change the code here for your own customization.
```
     defaultId = defaultId.Replace("ViewModel", "View");
```

* Open Swagger/SwaggerSchemaFilter.cs. There is a lot you can here. In the sample, there is code to filter out classes with namespace not starting with "SwashApiTest" and 
     to strip trailing "Internal" out of enum definitions.

* Open Swagger/SwaggerDocumentFilter.cs. In the sample code, we are adding two global parameters to all calls, 
     and adding a default reponse code to all responses, amoung others.

* F5 to run your project. The generated doc should be at *[root]/swagger/docs/[your new api version]*

##To Learn More
This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
