### ASPCoreOnIIS

This is a sample .NET8.0 app for demostrating deployments of ASPNETCORE web apps 
and web apis to IIS. In order to get a ASPNetCore or .NET6 or later app to
integrate with IIS, read the article here:

https://www.c-sharpcorner.com/article/host-and-publish-net-core-6-web-api-application-on-iis-server2/

A couple of other points which I also did to make it work:

- Choose a deployment location outside of C:\Inetpub, like C:\MyInetPub, etc.

This IIS folder is considered a point of attack, and it also imposes some 
weird security from IIS.  C:\Inetpub also interfered with publishing from
Visual Studio.

- In Program.cs of the application, ensure app.Run() has no arguments.

The arguments are fine for non-IIS (even Linux, etc) deployments.  Arguments will
conflict with the IIS settings.

- When publishing to the folder, stop the web site in IIS manager before 
publishing.

