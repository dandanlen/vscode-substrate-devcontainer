# VS Code Substrate Devcontainer

## What?

Configuration for developing a substrate project in a docker container using VS Code's remote containers feature.

## Why?

Check out the [main vs code remote development page](https://code.visualstudio.com/docs/remote/remote-overview) for a
list of reasons to use devcontainers. In short: it gives you a reproducible, disposable development environment.

## How?

Clone the repo and then either
**(A)** create a link to the `.devcontainer` from your project root (`cd my-project-root && ln path-to-vscode-substrate-devcontainer/.devcontainer`);
or **(B)** copy the `.devcontainer` folder into your project root.

Now, in VS Code, open the command pallet (`cmd-shift-P`) and look for `Remote Containers - Open Folder in Container...` and
navigate to your project root folder. The first time it will take a while to download and build the dependencies.
