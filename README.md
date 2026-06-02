## 项目介绍

一个基于 [Modern C++ Starter](https://github.com/TheLartians/ModernCppStarter) 的现代 C++ 项目模板。点击 [这里](https://github.com/TheLartians/ModernCppStarter#features) 查看使用该模板给你带来了哪些功能。

该文档只是该启动模板的介绍，而不是项目本身的文档。你也可以参考 [README_TEMP.md](README_TEMP.md) 为自己的项目编写 README 文档，然后删除该文件并将 [README_TEMP.md](README_TEMP.md) 重命名为 `README.md`。

## 如何使用

### 按照你的需要修改模板

- 点击 [作为模板使用](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template) 按钮
- 将项目中所有相关 CMakeLists.txt 中的 "Greeter" 替换为你的项目名称
    - 这里的大小写很重要：`Greeter` 指项目的名称，而 `greeter` 用在文件名中
    - 请记得将 `include/greeter` 目录重命名为你项目的小写名称，并相应地更新所有相关的 `#include`
    - 用你自己的文件替换源文件
    - 对于仅包含头文件的库：请参阅[CMakeLists.txt](CMakeLists.txt)中的注释
    - 将你的项目在 [Codecov](https://docs.codecov.io/docs/quick-start) 上的 token 添加到 `CODECOV_TOKEN` 环境变量中
    - Happy coding!

最终，你可以删除任何未使用的文件，例如独立的目录或不相关的 GitHub 工作流。请随意将许可证替换为适合你项目的许可证。

为了清晰地区分库和子项目代码，外层的 `CMakeLists.txt` 仅定义了库本身，而测试和其他子项目则各自包含在自己的目录中。

在开发过程中，通常很方便 [build all subprojects at once](#build-everything-at-once).

### 构建并运行独立目标

```bash
cmake -S standalone -B build/standalone
cmake --build build/standalone
./build/standalone/Greeter --help
```

### 构建并运行测试套件

```bash
cmake -S test -B build/test
cmake --build build/test
CTEST_OUTPUT_ON_FAILURE=1 cmake --build build/test --target test

# or simply call the executable: 
./build/test/GreeterTests
```

要收集代码覆盖率信息，请使用 `-DENABLE_TEST_COVERAGE=1` 选项运行 CMake。

### 运行代码格式化工具

从项目的根目录使用以下命令检查和修复 C++ 和 CMake 源代码风格。这需要在当前系统上安装 _clang-format_、_cmake-format_ 和 _pyyaml_。

```bash
cmake -S test -B build/test

# view changes
cmake --build build/test --target format

# apply changes
cmake --build build/test --target fix-format
```

### 构建文档

文档会在每次创建 [GitHub Release](https://help.github.com/en/github/administering-a-repository/managing-releases-in-a-repository) 时自动构建并发布。要手动构建文档，请调用以下命令。

```bash
cmake -S documentation -B build/doc
cmake --build build/doc --target GenerateDocs
# view the docs
open build/doc/doxygen/html/index.html
```

要在本地构建文档，您需要在系统上安装 Doxygen、jinja2 和 Pygments。

### 一次性构建所有

该项目还包括一个 `all` 目录，允许同时构建所有目标。

这在内联开发过程中很有用，因为它将所有子项目暴露给您的 IDE，并避免了库的重复构建。

```bash
cmake -S all -B build
cmake --build build

# run tests
./build/test/GreeterTests
# format code
cmake --build build --target fix-format
# run standalone
./build/standalone/Greeter --help
# build docs
cmake --build build --target GenerateDocs
```


## 更新日志

- 2026年6月2日：基于 Modern C++ Starter 模板的初始改造版本。
    - 修改了 README.md 文件。

## Showcase

> 基于该项目模板的项目示例

## 致谢

- 现代 C++ 项目模板：[Modern C++ Starter](https://github.com/TheLartians/ModernCppStarter)