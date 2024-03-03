---
title: Using &lt;bits/extc++.h&gt; Header File on MacOS (Example with VSCode)
tags:
  - c++
  - MacOS
  - Environment Setup
categories:
  - Tutorial
abbrlink: 15630
date: 2024-03-02 00:00:00
lang:
---

## Introduction

{% note info %}
To conclude first, it's difficult to use the `<bits/extc++.h>` header file with Clang as the compiler, as it will generate various mysterious errors. This article adopts the method of installing GCC via Homebrew and using GCC as the compiler.
{% endnote %}
<!--more-->

I originally wanted to try pbds while doing CSES problem set, but I found it completely unusable. There seems to be no solution on the internet, so after some research, this article was born.

## Install Homebrew (if not already installed)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Install GCC

Here you can choose to install different versions of GCC, but note that Macs with Arm architecture (M series chips) only support GCC version 11 and above.

```bash
# Install the latest version of GCC
brew install gcc

# Install GCC 11
brew install gcc@11
```

## Use GCC Compiler

If you don't know the installed GCC version, you can use the following command to check:

```bash
ls /usr/local/bin/gcc*  # Intel Mac
ls /opt/homebrew/bin/gcc*  # Apple Silicon Mac
```

Once you've confirmed the exact version number of GCC (for example, gcc-11), you can use that version of GCC to compile your code. For example, if the GCC version is 11, run:

```bash
g++-11 example.cpp -o Example

# If you want to compile with a specific version of C++ (for example, C++11), you can run
g++-11 example.cpp -o example -std=c++11
```

## Use GCC in VSCode

### Use [C/C++ Compile Run](https://marketplace.visualstudio.com/items?itemName=danielpinto8zz6.c-cpp-compile-run) Extension

Go to the extension settings page, search for `C-cpp-compile-run: Cpp-compiler`, and set it to use gcc for compilation.
![Set to use gcc for compilation](https://i.imgur.com/aUY9uQR.png)

### Use [Competitive Programming Helper (cph)](https://marketplace.visualstudio.com/items?itemName=DivyanshuAgrawal.competitive-programming-helper) Extension

Go to the extension settings page, search for `cph.language.cpp.Command`, and set it to use gcc for compilation.
![Set to use gcc for compilation](https://i.imgur.com/xKEDhsr.png)

## Conclusion

Now you can use the `<bits/extc++.h>` header file on MacOS. You can try whether the following code runs correctly:

```c++
#include <bits/extc++.h>

using namespace __gnu_pbds;
using namespace std;

int main() {
    tree<int, null_type, less<int>, rb_tree_tag, tree_order_statistics_node_update> s;
    s.insert(1);
    s.insert(3);
    cout << *s.find_by_order(1) << '\n'; // Outputs the second element (3)
    return 0;
}
```

If you have any questions about using GCC and the `<bits/extc++.h>` header file on MacOS, feel free to discuss in the comments below.
