---
layout: post
title:  "Building F# 3.0 projects on a build server"
date:   2015-03-07 15:31:10

---
We have started building a project where our solution contains both c# and F# projects. The solution built local as Visual Studio(2012) has all the bits required.

When we tried to build on the build server it failed because Visual Studio is not installed here and there was no F# tools installed.

So you need to install this from [here][F#tools]. As of now this is Visual F# Tools 3.1.2

Once this is installed we done a build again and it failed. The reason for this is because the fsproj file expects to find the F# dll in this location:

`"$(MSBuildExtensionsPath32)\..\Microsoft SDKs\F#\3.0\Framework\v4.0\Microsoft.FSharp.Targets" Condition=" Exists('$(MSBuildExtensionsPath32)\..\Microsoft SDKs\F#\3.0\Framework\v4.0\Microsoft.FSharp.Targets')"`

However the 3.0 folder is not present on the build server - it is 3.1 as we installed Visual F# tools 3.1.2


To get this to work we created a 3.0 folder in the same location as 3.1 and copied all the content from the 3.1 folder into it.

This results in our build server sucessfully building the project and with no change to our fsproj, Visual Studio also continues to build on local development machines as we had to make no changes to fsproj file.

[F#tools]:      http://www.microsoft.com/en-us/download/details.aspx?id=44011
