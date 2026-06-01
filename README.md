# set-vscode-xcode
A script to enable native debugging in VSCode on Mac with Xcode in a non-default location.

More info about why this is needed and what it does can be found in [this article](https://gershnik.github.io/2022/03/29/vscode-cpp-debugging-non-default-xcode.html)

To use:

* Download `set-vscode-xcode` script somewhere
* Make it executable
  ```console
  chmod a+x set-vscode-xcode
  ```
* Run it: 
  ```console
  ./set-vscode-xcode
  ```
 
  This will configure VSCode to use the currently-default Xcode for debugging. If you use the CMake extension and its debugging support, you are all set.
* If you use `launch.json` configurations to debug, you will need to set the following in each native configuration
 
  ```json
  "MIMode": "lldb",
  "miDebuggerPath": "${env:HOME}/.vscode-lldb-mi/lldb-mi"
  ```

  This config is fixed and doesn't need to change.
 
**Important Note #1**: you will need to re-run the script:
1. After the C++ extension is updated (usually every time VSCode updates itself)
2. If you want to use a different Xcode

**Important Note #2**: the script assumes that VSCode is installed in the default location. If it isn't, modify the `vsCodeLocation` variable at the top of the script.

You can control which Xcode is default by using the `xcode-select` command-line tool or by going to Xcode's Preferences -> Locations tab and selecting the instance you want in the "Command Line Tools" field.

If you want to use a non-default Xcode you can run `set-vscode-xcode` with the `DEVELOPER_DIR` environment variable set to point to the one you want to use.

Something like

```console
DEVELOPER_DIR=/Path/To/A\ Different/Xcode.app/Contents/Developer ./set-vscode-xcode
```



