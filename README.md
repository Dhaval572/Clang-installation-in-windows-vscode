# 🚀 C++ Setup Guide for VSCode on Windows (LLVM/Clang++ 21.1.8)

<div align="center">

**Perfectly configured C++23 development environment with LLVM/Clang++ in Visual Studio Code**

![C++](https://img.shields.io/badge/C%2B%2B-23-blue.svg)
![VSCode](https://img.shields.io/badge/VSCode-Setup-green.svg)
![LLVM](https://img.shields.io/badge/LLVM-21.1.8-orange.svg)

</div>

---

## 📋 Table of Contents
- [Download LLVM Compiler](#download-llvm-compiler)
- [Install LLVM](#install-llvm)
- [Add to Environment Variables](#add-to-environment-variables)
- [Install Code Runner Extension](#install-code-runner-extension)
- [Configure Code Runner](#configure-code-runner)
- [Test Your Setup](#test-your-setup)
- [Troubleshooting](#troubleshooting)

---

## 📦 Download LLVM Compiler

First, download the latest LLVM compiler with Clang++:

### 🔗 [Download LLVM 21.1.8 for Windows (64-bit)](https://github.com/llvm/llvm-project/releases/download/llvmorg-21.1.8/LLVM-21.1.8-win64.exe)

> **Note:** This version includes full C++23 support and other modern C++ features.

---

## ⚙️ Install LLVM

1. Run the downloaded `LLVM-21.1.8-win64.exe` installer
2. Follow the installation wizard with default settings
3. Make sure to check "Add LLVM to the system PATH for all users" or "Add LLVM to the system PATH for current user" during installation

---

## 🔧 Add to Environment Variables

If you didn't select the option to add LLVM to PATH during installation, you'll need to do it manually:

### Steps to Add LLVM to PATH:

1. Press `Win + X` and select "System"
2. Click on "Advanced system settings" on the left side
3. Click on "Environment Variables..." button
4. In the "System Variables" section, find and select "Path", then click "Edit..."
5. Click "New" and add the LLVM bin directory:
   ```
   C:\Program Files\LLVM\bin
   ```
   *(Or wherever you installed LLVM - typically ends with `\bin`)*
6. Click "OK" to save all changes
7. **Restart your command prompt/PowerShell and VSCode** for changes to take effect

<div align="center">
  
### 🖼️ **Image Reference: Environment Variables Setup**

</div>

---

## 🧩 Install Code Runner Extension

1. Open Visual Studio Code
2. Go to Extensions (`Ctrl+Shift+X`)
3. Search for "Code Runner" by Jun Han
4. Click "Install"

<div align="center">

### 🖼️ **Image Reference: Code Runner Extension**

</div>

---

## ⚙️ Configure Code Runner

1. After installing Code Runner, click on the extension settings (gear icon)
2. Go to "Extension Settings" 
3. Find "Executor Map" section
4. Click on "Edit in settings.json"

<div align="center">

### 🖼️ **Image Reference: Code Runner Configuration**

</div>

### 📝 Configure the Executor Map

In your VSCode `settings.json`, find the `"code-runner.executorMap"` section and add or replace with:

```json
{
    "code-runner.executorMap": {
        "cpp": "cd $dir && clang++ $fileName -o $fileNameWithoutExt.exe -std=c++23 -O3 && .\\$fileNameWithoutExt.exe"
    }
}
```

### 🖼️ **Image Reference: Code Runner Configuration**

This configuration will:
- Change to the current directory (`cd $dir`)
- Compile your C++ file with Clang++ (`clang++ $fileName -o $fileNameWithoutExt.exe`)
- Use C++23 standard (`-std=c++23`)
- Optimize with O3 level (`-O3`)
- Execute the compiled program (`.\$fileNameWithoutExt.exe`)



---

## 🧪 Test Your Setup

Create a new file called `test.cpp` and paste this test code:

```cpp
#include <iostream>

using namespace std;

int main()
{
    if (__cplusplus >= 202301L)
    {
        cout << "You can use C++23";
    }
    else
    {
        cout << "You can't use C++23";
    }
    return 0;
}
```

### How to Run:

1. Save your `test.cpp` file
2. Right-click in the editor
3. Select "Run Code" or press `Ctrl+Alt+N`
4. If successful, you should see "You can use C++23" in the output

<div align="center">

### 🎉 **BOOM! 💥💥 Setup is Complete!**

**Now you can run C++ code directly from VSCode with C++23 support!**

</div>

---

## 🔍 Troubleshooting

### If you get "clang++ is not recognized as an internal or external command":

1. Verify LLVM is installed correctly
2. Check that the bin folder is added to your PATH environment variable
3. Restart VSCode and your terminal
4. Try opening a new command prompt and type `clang++ --version`

### If Code Runner doesn't work:

1. Ensure you have saved your `.cpp` file before running
2. Check that the executor map is correctly configured in settings.json
3. Make sure you're using the correct file extension (.cpp)

### Compilation errors:

- Make sure you're using the correct syntax for C++23 features
- Some features might require additional compiler flags

---

## 🎯 Pro Tips

- Use `Ctrl+Alt+N` to run code quickly
- The compiled executable will be in the same directory as your source file
- You can modify the executor command to add additional flags as needed
- For debugging, consider installing the C/C++ extension by Microsoft as well

---

<div align="center">

### 🏆 You're Now Ready to Code in C++23!

**Happy Coding! 🎉**

</div>