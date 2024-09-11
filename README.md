# MonoGame Builder

This action allow you to build a **MonoGame project**.

The action sets up `dotnet` and you project's dependencies.
It then builds the `Content` resources and your MonoGame project.

## Usage

```yml
name: Build MonoGame Project

on:
  push:
    branches: [main]
jobs:
  build:
    name: build-windows
    runs-on: windows-latest

    steps:
      - name: Check out the repo
        uses: actions/checkout@v4

      - name: Build android project
        uses: akaadream/build-monogame-action@v1.0.0
        with:
          dotnet-version: "6.0.x"
          solution-path: '${{ github.workspace }}\Project\Project.sln'
          csproj-path: '${{ github.workspace }}\Project\Project.DesktopGL\DesktopGL.csproj'
          build-os: "win-x64"
```

## Options

* dotnet-version: You can select the version of .NET you want (default `8.0.x`)

## Required options:

* solution-path: The path to you .sln file
* csproj-path: The path of the C# project you want to build
* build-os: The OS targeted by the build (default `win-x64`)

## Contributions

Contributions are welcome!  
You can simply fork the project and create a pull request with a description of the features/fixes you've written.

## License

This Github Action is based on the works of [igotinfected](https://github.com/igotinfected) and updated for modern versions of MonoGame.
The scripts and documentation in this project are released under the [MIT License](LICENSE)
