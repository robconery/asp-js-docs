# Installation

Getting started with ASP.NET and a client application is simple, but first let's be sure you have everything you need installed and ready to go.

## Required Tools

You'll need to have .NET installed and you can find the installer you need [from here]([https://dotnet.microsoft.com/download/dotnet-framework](https://dotnet.microsoft.com/en-us/download)). This will install the `dotnet` software development kit (SDK) that you'll need for the next step.

Depending on the toolset you're using, you're probably going to need Node.js installed, [which you can download](https://nodejs.org) from here.

That's it! Let's write some code.

## Creating The Application

We're going to use a .NET *template* to install our application, which is a premade project that has all the things we need ready to go. We currently have 3 templates that use the following JavaScript frameworks:

 - React using `dotnet new react`
 - Angular using `dotnet new angular`
 - Vue using `dotnet new vue`  after template installation

We'll make more as we can, but you can also [create your own template](/advanced/templates) and publish it on NuGet if you want.

Let's use Vue for this example, but you can feel free to use whichever framework you're experienced with - the concepts we're about to jump into are all the same!

### Install the Template

.NET comes with templates for React and Angular built in, but we'll need to install [the Vue template](https://www.nuget.org/packages/Vue.Web.Starter/), which we can do using:

```
dotnet new install Vue.Web.Starter
```

This command talks to NuGet.org, the package manager used by .NET programmers, and asks it to install the latest version of the `Vue.Web.Starter` template in the `dotnet` template library. You can specify a version, if you like, by appending a `:X.X.X` to the end of the command, where `X.X.X` is the version number (`1.0.0` e.g.).

Once installed, we're ready to go!

```
dotnet new vue -n contoso
```

You should see a few things happening in your console, eventually ending with a success message!

![Successful Install](/img/01/success.jpg)

## What We Just Created

Let's have a look at the application we just created with the `dotnet new vue` command. If you're a seasoned ASP.NET developer, this will look familiar; same if you're a seasoned Vue developer. If you're both, hang in there as there might be a few things you'll need to understand.

We just generated two separate applications, which we'll dig into now.

### An ASP.NET Web App

We created an ASP.NET Web complete with a sample controller (`/Controllers/WeatherForecastController.cs`) and a model (`WeatherForecast.cs`). There is also a place for Razor pages, which are rendered on the server, but we're going to leave those alone as we won't be using them for this application.

![The ASP.NET Web App](/img/01/directory.jpg)

This is our *server application* which is going to be our API (using REST) and which will server our client application on first render.

### A Vue 3.0 Client Application

The other thing that was generated for us is a stock Vue application, which is the exact same application as when you run `npm init vue@latest`:

![The Vue Application](/img/01/vue_app.jpg)

Let's see if everything works!

## Running Our Applications

To run the application, navigate to the root directory of your project or, if you're using VS Code, press `CMD-Shift-\` (`Ctrl-Shift-\` on Windows) to open a new terminal session inside VS Code.

Next, run:

```
dotnet run
```

If you want ASP.NET to watch for changes in your ASP.NET code (not your client code), you can also use:

```
dotnet watch
```

There's more to this, so let's go deeper.

## Understanding The Client/Server Setup

We're working with two different applications here: a client app (Vue) and a server app (ASP.NET). Both are using their own web servers to run:

 - ASP.NET is running on Kestrel, the .NET Core web server, using port 8080. When the ASP.NET application started, it created a secondary process which is running...
 - Vue. Or, more accurately: Vue is running using Vite, which is the JavaScript build service that Vue uses. The client application is being served on port 8088.

Modern JavaScript frameworks rely on external services to "build" them. These services include:

 - Module bundling
 - Linting and minification
 - A web server
 - Reloading the application when things change (hot reload)

For most frameworks this means using an application called Webpack. Vue, on the other hand, uses a newer bundler called Vite, which is focused on speed.

You don't need to know more than this in order to use the Vue template, but it *is* important to understand that there are two applications being served on two different ports: ASP.NET is the API running on port 8080 and Vue, our client application, is running on port 8088.

## Summary

Now that we understand the code that's been created for us, let's go further and add some simple styling.
