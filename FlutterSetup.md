
## Flutter Installation and Setup

### Mac OS

If you’re installing on an Apple Silicon Mac, add Rosseta,
else you can ignore step 1.
 - Step 1

    ```
    sudo softwareupdate --install-rosetta --agree-to-license
    ```

- Step 2

    Download Flutter from the following link for the purpose of this course 

    - [For Intel Processors](https://storage.googleapis.com/flutter_infra_release/releases/stable/macos/flutter_macos_3.3.10-stable.zip)

    - [Apple Silicon Mac](https://storage.googleapis.com/flutter_infra_release/releases/stable/macos/flutter_macos_arm64_3.3.10-stable.zip)


 - Step 3

    Go to your desired Folder through the terminal.

    ```
    cd ~/development
    ```

Note: I also recommend using `iTerm` which can be downloaded [here](https://iterm2.com/downloads/stable/latest). You can use `iTerm` instead of `terminal`.

- Step 4

    Apple Silicon Users 

    ```
    unzip ~/Downloads/flutter_macos_arm64_3.3.10-stable.zip
    ```

    Intel Users

    ```
    unzip ~/Downloads/flutter_macos_3.3.10-stable.zip
    ```

 - Step 5

    Add flutter tool to your PATH using the following command

    ```
    export PATH="$PATH:`pwd`/flutter/bin"
    ```

    Note : This only adds Flutter to path in the current terminal window.

    Run the follownig command in your current terminal to view your updated path.

    ```
    echo $PATH
    ```
    Copy the content of what is returned. We will need it later. 

    Do the Following to add it permanently.

    1. Run the following command to determine what you are using 

        ```
        echo $SHELL
        ```

        Note: You will see either of the following `/bin/zsh` or `/bin/bash`

    2. If you see `zsh` - edit `$HOME/.zshrc`
    3. If you se `bash` - edit `$HOME/.bashrc` | `$HOME/.bash_profile`
    4. Run the following command to open your `zsh` file.
        ```
        open $HOME/.zshrc
        ```
        Run the following command if you use `bash`
        ```
        open $HOME/.bashrc
        ```
    5. If no such file exist do the following 
        ```
        touch $HOME/.zshrc
        ```
        or 
        ```
        touch $HOME/.bashrc
        ```
        and repeat step 4.
    6. Paste previously copied path to this file.
    7. Run the following command to refresh or source the file
        ```
        source $HOME/.zshrc
        ```
        or
        ```
        source $HOME/.bashrc
        ```
    8. Run `flutter doctor` 
    
Note: This commad should now be recognized by all `terminal` windows.

This should install and set you up with flutter.



