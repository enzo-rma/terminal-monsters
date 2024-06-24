# Terminal Monsters 👾

Welcome to Terminal Monsters, a fun terminal-based game where you can collect, train, and battle monsters that live in your terminal! Each monster in the dex embodies a specific programming language, framework, or technology, inspiring you to be curious and explore as many as possible to catch and train them all! 🚀

Embark on an exciting journey, enhance your coding skills, and become the ultimate Terminal Monsters trainer! 🤩

![Terminal Monsters Preview](https://github.com/enzo-rma/terminal-monsters/assets/127135864/6045ccbe-1a10-43d1-b3f4-a89160f1c4e0)

## 🛠️ Installation

To get started with Terminal Monsters, follow these steps:

### Install Rust 🦀

Make sure you have Rust installed on your machine. If you don't, follow the [official installation guide](https://doc.rust-lang.org/book/ch01-01-installation.html).

### Clone the Repository 📥

Clone the Terminal Monsters repository to your local machine:

```shell
git clone https://github.com/enzo-rma/terminal-monsters.git
```

### Install the Binary 💻

Navigate to the project directory and run the installation script:

```shell
sh install.sh
```

### Configure Your Shell 🐚

To fully enjoy the Terminal Monsters experience, you need to configure your shell to interact with the game. This involves adding some functions to your shell configuration file (`.bashrc` for Bash or `.zshrc` for Zsh). These functions will allow the game to monitor and respond to the commands you execute in your terminal, enabling the collection and training of monsters as you go about your programming tasks.

For Bash, open your .bashrc file and add the following code:

```bash
# Terminal Monsters Inc. function to send commands to the worker.
watcher() {
    # Capture the command
    local cmd="\$@"
    # Execute the command
    eval "\$cmd"
    # Send the command to the worker
    echo "\$cmd" | $WORKER_PATH
}

# Terminal Monsters Inc. function to collect and train monsters.
preexec_invoke_exec() {
    [ -n "\$COMP_LINE" ] && return  # Do not intercept tab-completion
    local cmd
    if [ -n "\$BASH_VERSION" ]; then
        cmd="\$BASH_COMMAND"
    elif [ -n "\$ZSH_VERSION" ]; then
        cmd="\$1"
    fi
    echo "\$cmd" | $WORKER_PATH
}

# Terminal Monsters Inc. preexec function for Zsh
if [[ -n "\$ZSH_VERSION" ]]; then
    autoload -Uz add-zsh-hook
    add-zsh-hook preexec preexec_invoke_exec
fi
EOL
fi
```

For Zsh, open your .zshrc file and add the following code:

```zsh
# Terminal Monsters Inc. function to send commands to the worker.
watcher() {
    # Capture the command
    local cmd="\$@"
    # Execute the command
    eval "\$cmd"
    # Send the command to the worker
    echo "\$cmd" | $WORKER_PATH
}

# Terminal Monsters Inc. function to collect and train monsters.
preexec_invoke_exec() {
    [ -n "\$COMP_LINE" ] && return  # Do not intercept tab-completion
    local cmd
    if [ -n "\$BASH_VERSION" ]; then
        cmd="\$BASH_COMMAND"
    elif [ -n "\$ZSH_VERSION" ]; then
        cmd="\$1"
    fi
    echo "\$cmd" | $WORKER_PATH
}

# Terminal Monsters Inc. preexec function for Bash
if [[ -n "\$BASH_VERSION" ]]; then
    trap 'preexec_invoke_exec' DEBUG
fi
EOL
fi
```

### Launch the Game 🚀

Locate and execute the `terminal-monsters-app` binary. It should be located in the `.cargo` directory at the following path: `{your_home_directory}/.cargo/bin/terminal-monsters-app`.

## 🌟 Let the Adventure Begin!

You're all set! Terminal Monsters is now installed and ready for you to embark on your monster-collecting journey. As you go about your programming routine, keep an eye out for Terminal Monsters that might join your party when you run certain commands. The more you code and the more programming languages you explore, the more monsters you'll encounter!

So what are you waiting for? Go catch'em all and become the ultimate Terminal Monsters trainer! 😄

Happy coding and monster-catching! 🎉
