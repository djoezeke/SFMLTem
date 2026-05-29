```console
███████ ██████  ███   ███  ██    ████████ ██████   ███   ███  ██████ ██      ████  ████████ ██████
██      ██     ██ ██ ██ ██ ██       ██    ██      ██ ██ ██ ██ ██  ██ ██     ██  ██    ██    ██
███████ ██████ ██  ███  ██ ██       ██    █████   ██  ███  ██ ██████ ██     ██████    ██    ██████
     ██ ██     ██       ██ ██       ██    ██      ██       ██ ██     ██     ██  ██    ██    ██
███████ ██     ██       ██ ██████   ██    ██████  ██       ██ ██     ██████ ██  ██    ██    ██████

◎ A Base Project Setup for SFML/ImGui
```

<p align="center"><h1 align="center">SFML TEMPLATE</h1></p>
<p align="center">
  <em><code>C++ Rendering/Graphics project template with SFML and Dear ImGUI.
</code></em>
</p>
<p align="center">
  <img src="https://img.shields.io/github/license/djoezeke/SFMLTem?style=default&logo=opensourceinitiative&logoColor=white&color=0080ff" alt="license">
  <img src="https://img.shields.io/github/last-commit/djoezeke/SFMLTem?style=default&logo=git&logoColor=white&color=0080ff" alt="last-commit">
  <img src="https://img.shields.io/github/languages/top/djoezeke/SFMLTem?style=default&color=0080ff" alt="repo-top-language">
  <img src="https://img.shields.io/github/languages/count/djoezeke/SFMLTem?style=default&color=0080ff" alt="repo-language-count">
</p>

<details><summary>Table of Contents</summary>

- [📍 Overview](#-overview)
- [👾 Features](#-features)
- [📁 Structure](#-structure)
- [🚀 Getting Started](#-getting-started)
  - [☑️ Prerequisites](#-prerequisites)
  - [⚙️ Building](#-building)
  - [🧪 Testing](#🧪-testing)
- [🔰 Contributing](#-contributing)
- [🙌 Acknowledgments](#-acknowledgments)
- [📃 License](#-license)

</details>

## 📍 Overview

This repository template should allow for a fast and hassle-free kick start of your next SFML project using CMake.
Thanks to [GitHub's nature of templates](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template), you can fork this repository without inheriting its Git history.

The template starts out very basic, but might receive additional features over time:

- Basic CMake script to build your project and link SFML on any operating system
- Basic [GitHub Actions](https://github.com/features/actions) script for all major platforms

### For whom is this for?

- Prototyping
- Getting started with game programming
- Getting started with graphics programming

## 👾 Features

- Sources, headers and mains separated in distinct folders
- Use of modern [CMake](https://cmake.org/) for much easier compiling
- Continuous integration via [GitHub Actions](https://help.github.com/en/actions)

## 📁 Structure

## 🚀 Getting Started

1. Install [Git](https://git-scm.com/downloads) and [CMake](https://cmake.org/download/). Use your system's package manager if available.

## ☑️ Prerequisites

This project leverages several modern libraries and tools to streamline development, building, and documentation.

### 🧰 Additional Tools

- [Git](https://git-scm.com/) – Version control and submodule/dependency management
- [Ninja](https://ninja-build.org/) – (Optional) Faster alternative build backend for CMake
- [Doxygen](https://doxygen.org/) – (Optional) Generate code documentation

## ⚙️ Building

### Build Program With [CMake](https://cmake.org/)

## 🧪 Testing

### Unit Testing With [Doctest](https://github.com/onqtam/doctest)

## 🔰 Contributing

- **💬 [Join the Discussions](https://github.com/djoezeke/SFMLTem/discussions)**: Share your insights, provide feedback, or ask questions.
- **🐛 [Report Issues](https://github.com/djoezeke/SFMLTem/issues)**: Submit bugs found or log feature requests for the `SFMLTem` project.
- **💡 [Submit Pull Requests](https://github.com/djoezeke/SFMLTem/blob/main/CONTRIBUTING.md)**: Review open PRs, and submit your own PRs.

<details closed>
<summary>Contributing Guidelines</summary>

1. **Fork the Repository**: Start by forking the project repository to your github account.
2. **Clone Locally**: Clone the forked repository to your local machine using a git client.
   ```sh
   git clone --recursive https://github.com/djoezeke/SFMLTem
   ```
3. **Create a New Branch**: Always work on a new branch, giving it a descriptive name.
   ```sh
   git checkout -b new-feature-x
   ```
4. **Make Your Changes**: Develop and test your changes locally.
5. **Commit Your Changes**: Commit with a clear message describing your updates.
   ```sh
   git commit -m 'Implemented new feature x.'
   ```
6. **Push to github**: Push the changes to your forked repository.
   ```sh
   git push origin new-feature-x
   ```
7. **Submit a Pull Request**: Create a PR against the original project repository. Clearly describe the changes and their motivations.
8. **Review**: Once your PR is reviewed and approved, it will be merged into the main branch. Congratulations on your contribution!
</details>

<details closed>
<summary>Contributor Graph</summary>
<br>
<p align="left">
   <a href="https://github.com{/djoezeke/SFMLTem/}graphs/contributors">
      <img src="https://contrib.rocks/image?repo=djoezeke/SFMLTem">
   </a>
</p>
</details>

## 🙌 Acknowledgments

We would like to express our gratitude to the following projects and individuals whose work made this project possible.

- [**SFML**](https://github.com/SFML/SFML) for Graphic Rendering
- [**Clang**](https://clang.llvm.org) for compilation with sanitizers
- [**ImGui**](https://github.com/ocornut/imgui) for Immediate Mode GUI
- [**CMake**](https://cmake.org) for build automation
- [**MkDocs**](https://www.mkdocs.org) for the documentation site
- [**Doctest**](https://github.com/onqtam/doctest) for the unit tests
- [**ImGui-SFML**](https://github.com/onqtam/doctest) to bind ImGui and SFML

> [!IMPORTANT]
> Special Thanks to the open-source community for their invaluable libraries, tutorials, and support.

If you feel your work should be acknowledged here, please open an issue or pull request.

### References

- [**CPPTem**](https://github.com/djoezeke/CppTem/) : A C/C++ Starter Template.
- [**SDLTem**](https://github.com/djoezeke/SDLTem/) : A SDL Starter Template with [SDL](https://www.libsdl.org/) and [ImGui](https://github.com/ocornut/imgui).
- [**RAYTem**](https://github.com/djoezeke/SDLTem/) : A Raylib Starter Template with [Raylib](https://www.raylib.com) and [ImGui](https://github.com/ocornut/imgui).
- [**SFMLTem**](https://github.com/djoezeke/SFMLTem/) : A SFML Starter Template with [SFML](https://www.sfml-dev.org/) and [ImGui](https://github.com/ocornut/imgui).
- [**GLFWTem**](https://github.com/djoezeke/GLFWTem/) : A GLFW Starter Template with [OpenGl](https://www.opengl.org/) and [ImGui](https://github.com/ocornut/imgui).

### More Reading

Here are some useful resources to learn more:

- [Official CMake Tutorial](https://cmake.org/cmake/help/latest/guide/tutorial/index.html)

## 📃 License

This project is protected under the [MIT](LICENSE) License.
For more details, refer to the [LICENSE](LICENSE) file.

<picture>
  <source
    media="(prefers-color-scheme: dark)"
    srcset="
      https://api.star-history.com/svg?repos=SFMLTem/djoezeke&type=Date&theme=dark
    "
  />
  <source
    media="(prefers-color-scheme: light)"
    srcset="
      https://api.star-history.com/svg?repos=SFMLTem/djoezeke&type=Date
    "
  />
  <img
    alt="Star History Chart"
    src="https://api.star-history.com/svg?repos=SFMLTem/djoezeke&type=Date"
  />
</picture>
