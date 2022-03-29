# set-vscode-xcode
A script to enable VSCode native debugging on Mac with Xcode in a non-default location

To use

* Download `set-vscode-xcode` script somewhere
* Run it: 
  ```console
  ./set-vscode-xcode
  ```
 
  This will configure VScode to use currently default Xcode for debugging. If you use CMake extension and its debugging support, you are all set.
* If you use `launch.json` configurations to debug you will need to set the following in each native configuration
 
  ```json
  "MIMode": "lldb",
  "miDebuggerPath": "${env:HOME}/.vscode-lldb-mi/lldb-mi"
  ```

  This config is fixed and doesn't need to change.
 
**Important Note #1**: you will need to re-run the script:
1. After C++ extension is updated (usually every time VScode updates itself)
2. If you want to use a different Xcode

**Important Note #2**: the script assumes that VSCode is installed in default location. If it isn't, modify `vsCodeLocation` variable in the beginning.

You can control which Xcode is default by using `xcode-select` command line tool or by going to Xcode's Preferences -> Locations tab and selecting the instance you want in "Command Line Tools" field.

If you want to use non-default Xcode you can run `set-vscode-xcode` with `DEVELOPER_DIR` environment variable set to point to the one you want to use. 

Something like

```console
$ DEVELOPER_DIR=/Path/To/A\ Different/Xcode.app/Contents/Developer ./set-vscode-xcode
```



