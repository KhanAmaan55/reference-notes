# Add ```code ``` terminal alias for VSCode

## METHOD 1 - by updating ```.zshrc``` file
After installing Visual Studio Code, you need to ensure that the "code" command is added to your shell's PATH. The PATH is a list of directories where the shell looks for executable files.

To add "code" to your PATH in Zsh, you can typically do this by modifying your shell configuration file. Here's how you can do it:

Open your Zsh configuration file in a text editor. The most common file to edit is "~/.zshrc." You can open it with a text editor like nano, vim, or any other of your choice:
```shell
nano ~/.zshrc
```

Add the following line to the file to export the Visual Studio Code executable path to your PATH:
```shell
export PATH="$PATH:/path/to/VSCode/bin"
```

Replace "/path/to/VSCode" with the actual path to your Visual Studio Code installation directory.

Save the file and exit the text editor.

Then, you need to apply the changes by reloading your Zsh configuration. You can do this by running:
```shell
source ~/.zshrc
```


## METHOD 2 - Add from VSCode
you can configure Visual Studio Code to open from the terminal using a command like "code .". Here's how you can set it up:

1. **Open Visual Studio Code**.

2. In the top menu, click on "View" and then select "Command Palette" or use the keyboard shortcut `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux).

3. In the command palette, type "Shell Command: Install 'code' command in PATH" and select it from the list of commands that appear.

4. Visual Studio Code will prompt you to allow the installation of the command-line tools. Confirm and proceed with the installation.

5. Once the installation is complete, you should be able to use the "code" command from the terminal to open Visual Studio Code in the current directory:

```bash
code .
```

This will launch Visual Studio Code with the current directory as the workspace.

By following these steps, you'll set up the ```code ``` command to work directly from the terminal, allowing you to open Visual Studio Code with ease.
