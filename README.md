[![Retyped logo](https://user-images.githubusercontent.com/62210/30553225-bf327466-9c5d-11e7-8737-b353f4cb219d.png)](https://retyped.com/)

<p align="center"><img src="https://user-images.githubusercontent.com/62210/30553224-bf2f6bb8-9c5d-11e7-8524-0fa681af17a4.png"></p>

<h1 align="center">Access 2200+ JavaScript libraries from C#</h1>

<br />[![NuGet Status](https://img.shields.io/nuget/v/Retyped.svg)](https://www.nuget.org/packages/Retyped)
[![Join the chat at https://gitter.im/bridgedotnet/Bridge](https://badges.gitter.im/bridgedotnet/Bridge.svg)](https://gitter.im/bridgedotnet/Bridge?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

## Getting Started

**Retyped** can be added to any existing [Bridge.NET](http://bridge.net/) C# Class Library project.

If you haven't already done so, the first step is to create a Bridge C# Class Library project. The following tutorials demonstrate three techniques for creating a Bridge project.

Install Technique | Video Tutorial
---- | ----
Visual Studio Extension | [![youtube](https://user-images.githubusercontent.com/62210/30516389-2a02a31a-9afb-11e7-9979-01fa73586680.png)](https://www.youtube.com/watch?v=cEUR1UthE2c)
NuGet Package Manager | [![youtube](https://user-images.githubusercontent.com/62210/30518461-c3307270-9b3b-11e7-8b86-86edcbd3cdb7.png)](https://www.youtube.com/watch?v=VMjsQrB9rQc)
NuGet Package Console | [![youtube](https://user-images.githubusercontent.com/62210/30518454-aa99a51a-9b3b-11e7-9764-a31240d42758.png)](https://www.youtube.com/watch?v=hAaxLrVeG0c)

See the Bridge [Getting Started](https://github.com/bridgedotnet/Bridge/wiki) documentation for more details.

Once you have **Bridge** installed to your project, **Retyped** is added using [NuGet](https://www.nuget.org/packages/retyped).

Search for **Retyped** within the NuGet Package Manager, or by running the following command within your NuGet Package Console:

```
install-package retyped
```

The base [Retyped](https://www.nuget.org/packages/retyped) package adds support for the entire JavaScript ES5 and DOM API. This includes all JavaScript types, functions, classes, and events. Everything.

**PRO TIP:** Use [Deck.NET](https://deck.net/welcome) to experiment with the Retyped base packages. Currently, only the [dom](https://www.nuget.org/packages/retyped.dom), [es5](https://www.nuget.org/packages/retyped.es5), and [jquery](https://www.nuget.org/packages/retyped.jquery) packages are supported on Deck. We're planning to add configurable support for every Retyped package soon.

Several thousand JavaScript libraries are supported by Retyped. Search for available libraries on the [retyped.com](https://retyped.com#search) or [bridge.net](http://bridge.net/download#search) websites.

![install-nuget-package](https://user-images.githubusercontent.com/62210/30530936-20bc70de-9c08-11e7-85d5-db8d9c34267f.gif)

Each Retyped library has been created as a NuGet Package and can be found through the NuGet Package Manager, or by using the pattern of `retyped.{library_name}` in the NuGet Package Console, or by searching the NuGet [website](https://www.nuget.org/packages?q=retyped). It's really easy to find the library you're looking for.

For example, to install [Node](https://www.nuget.org/packages/retyped.node):

```
install-package retyped.node
```

To install [jQuery](https://www.nuget.org/packages/retyped.jquery):

```
install-package retyped.jquery
```

## About

The **Retyped** parser is built on top of [ANTLR](http://www.antlr.org/), [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/), and the .NET [Roslyn](https://github.com/dotnet/roslyn) Compiler Platform.

Retyped reads TypeScript declaration files (.d.ts) and creates a NuGet Package for each library. The TypeScript Definition files are sourced from several locations including [Definitely Typed](http://definitelytyped.org/) and direct from the original author through [NPM](https://www.npmjs.com/).

A TypeScript declaration file is written in TypeScript and represents the public (exported) members and types of a JavaScript library. If you are familiar with **C++** you can think of a declaration file as a header file **(.h)**. It contains interfaces and definitions, but there are no implementation details.

Retyped is built and professionally supported by the team at **Bridge.NET** ([website](http://bridge.net) | [forums](https://forums.bridge.net) | [github](https://github.com/bridgedotnet/) | [twitter](http://twitter.com/bridgedotnet)).

## Package Structure

**Retyped** reads declaration files, compiles each into an individual **C# Class Library** project, and creates a NuGet Package for each. These are considered _Binding Libraries_ for Bridge.NET projects.

Each **Retyped** package also embeds the source .d.ts declaration file. That file (or files) will be emitted to your output folder if the corresponding [generateTypeScript](https://github.com/bridgedotnet/Bridge/wiki/global-configuration#generatetypescript) setting is configured in your projects **bridge.json** file:

```js
"generateTypeScript": true
```

In a future release, Retyped packages will also contain all required JavaScript (.js) source files. This is a priority item on our roadmap. Once this feature is supported, that would make the installation process as smooth as possible. For now, the JavaScript .js source file or Module for a particular library must be added to your .html file manually.

## FAQ

1. **Question:** I've found a mistake in the Retyped package {library_name}. How can it be fixed?<br/>
   **Answer:** Since Retyped parses original TypeScript declaration files, please double check the error does not originate from the original .d.ts file. If it does, please report the issue (or submit a PR) to the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) repository. Once the issue is fixed, Retyped will recompile the library and publish a NuGet package.

2. **Question:** I've found an issue related to incorrect JavaScript being emitted, or the C# API doesn't correspond to the source declaration file. The source .d.ts file appears to be correct.<br/>
   **Answer:** Please report the [issue](https://github.com/Retyped/Retyped/issues) and we will investigate right away.

3. **Question:** I have a proposal for simplifying or enhancing Retyped syntax. Where can we discuss?<br/>
   **Answer:** We really appreciate your feedback and ideas. Please create an [issue](https://github.com/Retyped/Retyped/issues) so we can review and discuss with you.

4. **Question:** I need a Retyped package for `{library_name}`. The library is available in the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) repository but I cannot find a Retyped package for it?<br/>
   **Answer:** Sorry for that. We do our best to support all the libraries from the DefinitelyTyped repository. However, some libraries can't be compiled due to specific syntax that is not currently supported by Retyped compiler, or the library contains a defect.<br/>
   Another possible reason is that your library has just been added, and in this case, a Retyped package is on its way. Either way, please report the [issue](https://github.com/Retyped/Retyped/issues) to draw our attention to the problem. Don't hesitate to add your comment or reaction, if the issue already exists.

5. **Question:** I need a Retyped package for a library that is not in the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) repository. Can we get a custom Retyped package made?<br/>
   **Answer:** The simplest process is to add that library into the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) repository. On the next recompile by Retyped, the library will be available and can be searched on the [retyped.com](https://retyped.com/#search) website.<br/>
   If the library is private and cannot be released publicly, please send an email to hello@object.net and we'll try to help.

## Badges

Show your support by adding a **built with Retyped** badge to your project's README or website.

[![Built with Retyped](https://img.shields.io/badge/built%20with-Retyped-blue.svg)](http://retyped.com/)

#### Markdown

```
[![Built with Retyped](https://img.shields.io/badge/built%20with-Retyped-blue.svg)](http://retyped.com/)
```

#### HTML

```
<a href="http://retyped.com/">
    <img src="https://img.shields.io/badge/built%20with-Retyped-blue.svg" title="Built with Retyped" />
</a>
```

## License

Licensing for use of the individual JavaScript libraries should be sourced from the original JavaScript library.

Retyped packages are licensed under [Apache-2.0](https://github.com/Retyped/Retyped/blob/master/LICENSE.md) licence and are free to use in both commercial and open-source projects.

Currently, the original C# source code generated for each library by Retyped are not publicly available. We hope to release these at some point in the future, but for now, they're private. The NuGet Packages are public, the C# source code for each package is private.

The Retyped parser and compiler source code is private.
