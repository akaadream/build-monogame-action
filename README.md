# build-monogame

This action allows you to build your monogame project via **msbuild**.

The action sets up `dotnet`, `msbuild`, and the `mgcb` build tool.
It then builds the `Content` resources using `mgcb` and then builds the game/project using `msbuild`.

# Usage

```yml
name: Run checks on incoming PR

on:
  push:
    branches: [main]

  # allow running this workflow manually
  workflow_dispatch:

jobs:
  build:
    name: build-${{ matrix.os }}
    runs-on: ${{ matrix.os}}-latest

    steps:
      - name: Check out the repo
        uses: actions/checkout@v4

      - name: Build android project
        uses: akaadream/monogame-builder-action@v0.1.0
        with:
          solution-path: '${{ github.workspace }}\Project\Project.sln'
          content-mgcb-path: '${{ github.workspace }}\Project\Android\Content'
          content-mgcb-platform: "Android"
          csproj-path: '${{ github.workspace }}\Project\Android.csproj'
          build-target: "PackageForWindows"
          build-configuration: "Release"
          build-os: "win-x64"
```
# License

This Github Action is based on the works of [igotinfected](https://github.com/igotinfected) and updated for modern version of MonoGame.
The scripts and documentation in this project are released under the [MIT License](LICENSE)
