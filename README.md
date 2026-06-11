# Multi Target Example

This repository is a small sample that shows how to use multiple targets in a .NET solution.

It contains:

- a multi-targeted class library in `MultiTargetLibrary` that builds for `net10.0` and `netstandard2.0`
- a .NET 10 console app in `CallWithNet10`
- a .NET Core 3.1 console app in `CallWithNetStandard`

The library uses target-specific partial class implementations so each framework can return its own message. 
 - For `net10.0`, the implementation lives in `MultiTargetLibrary/Net10/MyBestService.net10.cs`.
 - For `netstandard2.0`, the implementation lives in `MultiTargetLibrary/NetStandard/MyBestService.netstandard.cs`.

## What This Sample Demonstrates

- How to define multiple target frameworks in one project
- How to include or exclude source files per target framework
- How to consume the same library from apps targeting different frameworks

## Projects

- `MultiTargetLibrary`: shared library with target-specific implementations
- `CallWithNet10`: console app that references the library and targets `net10.0`
- `CallWithNetStandard`: console app that references the library and targets `netcoreapp3.1`

## Run The Sample

Both **CallWithNet10** and **CallWithNetStandard** projects call the **MyBestService.GetMessage()** from the same library but the output is different:

-  when call from CallWithNet10 it displays **This is the best service - .NET 10.0!**
-  when call from CallWithNetStandard it displays  **This is the best service - .NET Standard!**

So each console app prints the message from the library implementation that matches its target framework.
