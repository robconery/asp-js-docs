# Installation

Getting started with ASP.NET and a client application is simple, but first let's be sure you have everything you need installed and ready to go.

## Required Tools

You'll need to have .NET installed and you can find the installer you need [from here](https://dotnet.microsoft.com/en-us/download/dotnet-framework). This will install the `dotnet` binary that you'll need for the next step.

Depending on the toolset you're using, you're probably going to need Node.js installed, [which you can download](https://nodejs.org) from here.

That's it! Let's write some code.

## Creating The Application

We're going to use a .NET *template* to install our application, which is a premade project that has all the things we need ready to go. We currently have 3 templates that use the following JavaScript frameworks:

 - React
 - Angular
 - Vue

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

![Successful Install](/img/01_success.jpg)
