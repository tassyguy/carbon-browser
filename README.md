# Carbon Browser
An open-source no-BS browser built on the Blink engine

Welcome to the Carbon Browser repository! This project contains the custom code, assets, and build scripts for creating the Carbon Browser—a clean, minimalist, and developer-focused browser built on the Chromium engine.

This repository does not contain the full Chromium source code. Instead, it uses an "overlay" method where our custom files are applied on top of a fresh download of the Chromium source during the build process.

## Prerequisites

Before you can build Carbon Browser, you must have all the necessary prerequisites for building Chromium itself. This includes:
* A 64-bit OS (Windows 10/11, macOS 11+, or modern Linux).
* At least 100GB of free disk space (SSD highly recommended).
* At least 16GB of RAM.
* Required development tools like Git, Python 3, and platform-specific compilers (Visual Studio 2022 on Windows, Xcode on macOS, etc.).

For a complete list of prerequisites, please refer to the official Chromium developer documentation.
## How to Build

The entire build process is automated with a single script.

1. **Clone this Repository:**
> git clone https://github.com/tassyguy/carbon-browser.git
>
> cd carbon-browser

2. **Run the Build Script:**

  Execute the script appropriate for your operating system. This script will handle everything: creating a build directory, downloading depot_tools and the Chromium source, applying custom files, and compiling the final application.

**For Windows (in a PowerShell terminal):**
  > .\build.ps1

**For macOS or Linux:**
  > chmod +x build.sh
  > 
  > ./build.sh

The build process will take a very long time (potentially several hours) depending on your machine's performance. Once it's complete, the final browser executable will be located inside the chromium_build/src/out/Default/ directory.

## Customization

To modify the browser, you do not need to edit the code inside the temporary chromium_build directory. Instead, you modify the files within this repository.

1. **Find the File:** Locate the original file you wish to modify from the Chromium source code.

2. **Copy to this Repo:** Copy that file into the src_overrides/ directory, making sure to preserve the exact same folder structure.

    * **Example:** To change the main toolbar, you might copy chrome/browser/ui/views/toolbar/toolbar_view.cc to src_overrides/chrome/browser/ui/views/toolbar/toolbar_view.cc.

3. **Edit the File:** Make your changes to the file inside src_overrides/.

4. **Re-run the Build:** The build script will automatically copy your modified version over the original during the build process.

To change icons and other assets, simply replace the files in the assets/ directory with your own, ensuring the filenames match.
