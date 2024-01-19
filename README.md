# ghul-targets

[![CI/CD](https://img.shields.io/github/workflow/status/degory/ghul-targets/CICD)](https://github.com/degory/ghul-targets/actions?query=workflow%3ACICD)
[![NuGet version (ghul.targets)](https://img.shields.io/nuget/v/ghul.targets.svg)](https://www.nuget.org/packages/ghul.targets/)
[![Release](https://img.shields.io/github/v/release/degory/ghul-targets?label=release)](https://github.com/degory/ghul-targets/releases)
[![Release Date](https://img.shields.io/github/release-date/degory/ghul-targets)](https://github.com/degory/ghul-targets/releases)
[![Issues](https://img.shields.io/github/issues/degory/ghul-targets)](https://github.com/degory/ghul-targets/issues) 
[![License](https://img.shields.io/github/license/degory/ghul-targets)](https://github.com/degory/ghul-targets/blob/main/LICENSE)
[![ghūl](https://img.shields.io/badge/gh%C5%ABl-100%25!-information)](https://ghul.dev)

This package provides MSBuild targets needed to build [ghūl language](https://ghul.dev) projects.
The targets work with the standard .NET SDK targets 
by overriding the `CoreCompile` target to call the [ghūl compiler](https://github.com/degory/ghul)

This is a minimal example `.ghulproj` (ghūl project file) using the targets from this package:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net8.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>    
    <GhulCompiler>dotnet ghul-compiler</GhulCompiler>
    <GhulSources Include="**/*.ghul" /> <!-- build all files with a .ghul extension: -->
    
    <PackageReference Include="ghul.runtime" Version="1.0.0" /> <!-- ghūl runtime library -->
    <PackageReference Include="ghul.pipes" Version="1.0.0" /> <!-- ghūl pipes provides the pipe operator, filter, map reduce etc. -->
    <PackageReference Include="ghul.targets" Version="1.3.0" /> <!-- this package provides ghūl MSBuild targets: -->
  </ItemGroup>
</Project>

```