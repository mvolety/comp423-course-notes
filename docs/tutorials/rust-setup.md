# Setting Up a DevContainer for Rust

Welcome! In this tutorial, you'll learn how to set up a Rust development environment using Dev Containers in Visual Studio Code. By the end of this guide, you'll have a working Rust project that prints "Hello COMP423" to the console.

## Why Dev Containers for Rust?

Setting up consistent development environments can be challenging. Dev Containers, powered by Docker, make this easy by creating a pre-configured environment for your project. For Rust, this means you'll have the language tools (`rustc`, `cargo`) and helpful extensions (`rust-analyzer`) ready to go.

Using a Dev Container ensures your code runs the same way on any machine, making it easier to collaborate, debug, and onboard new team members.

## Why This Matters

Rust is a modern, high-performance systems programming language known for its safety and speed. It powers some of the most critical systems, including web browsers, operating systems, and distributed databases. Learning to set up a project using Rust's tools and a Dev Container not only teaches you valuable skills but also sets you up to work efficiently in professional environments.

## What You Will Learn

By completing this tutorial, you will:

- Set up a Rust development container in VS Code.
- Configure the `rust-analyzer` extension for enhanced coding features.
- Create a basic Rust project using `cargo`.
- Write, build, and run a "Hello COMP423" program in Rust.
- Understand Rust's build and run workflow using `cargo`.

## Prerequisites

Before diving in, ensure you have the following:

- **A GitHub Account**: If you don't have one yet, sign up at [GitHub](https://github.com/)
- **Git Installed**: Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don't already have it
- **Visual Studio Code (VS Code)**: [Download VS Code](https://code.visualstudio.com/).
- **Dev Containers Extension**: Install the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers).
- **Docker Desktop**: [Install Docker](https://www.docker.com/).

## Part 1: Setting Up the Project

### Step 1: Create a Local Directory and Initialize Git

1. Open your terminal and navigate to where you'd like to create the project.
2. Create a new directory for your project and initialize a Git repository:
    * `mkdir rust-dev-container`
    * `cd rust-dev-container` 
    * `git init`
3. Add a README file:
    * `echo "# Rust Dev Container Project" > README.md`
    * `git add README.md`
    * `git commit -m "Initial commit with README"`

### Step 2: Create a Remote Repository on GitHub

1. Log in to your GitHub account and navigate to the **Create a New Repository** page.

2. Fill in the details as follows:
   - **Repository Name**: `rust-tutorial`
   - **Description**: "Hello World program in Rust"
   - **Visibility**: Public

3. Do not initialize the repository with a `README`, `.gitignore`, or license.

4. Click **Create Repository**.

# Step 3. Link your Local Repository to GitHub

1. Add the GitHub repository as a remote:

        git remote add origin https://github.com/<your-username>/rust-tutorial.git

Replace `<your-username>` with your GitHub username.

2. Check your default branch name with the subcommand:

        git branch

If it's not `main`, rename it to `main` with the following command:

        git branch -M main

> Old versions of Git use `master` for the primary branch, but `main` is now the standard.

3. Push your local commits to the GitHub repository:

        git push --set-upstream origin main

### Understanding the `--set-upstream` Flag

- The command `git push --set-upstream origin main` pushes the `main` branch to the remote repository `origin`.
- The `--set-upstream` flag sets the `main` branch to track the remote branch. This allows future pushes and pulls to be done without specifying the branch name. You can simply use:

        git push origin

when working on your local `main` branch.
- The long flag `--set-upstream` has a corresponding short flag `-u`.

4. Back in your web browser, refresh your GitHub repository to confirm that the same commit you made locally has been pushed to the remote repository.  
 - Use `git log` locally to see the commit ID and message, which should match the most recent commit on GitHub.
 - This confirms your changes have been successfully pushed to the remote repository.


## Part 2: Setting Up the Development Environment

### Step 1: Create the Dev Container Configuration

1. Create a `.devcontainer` folder in the project directory: 
    * `mkdir .devcontainer`.
2. Inside `.devcontainer`, create a `devcontainer.json` file with the following content:

            {
                "name": "Rust Dev Container",
                 "image": "mcr.microsoft.com/devcontainers/rust:latest",
                 "customizations": {
                     "vscode": {
                        "extensions": ["rust-lang.rust-analyzer"]
                    }
                }
            }

#### Explanation of the Configuration

- `"image"`: Specifies the Rust base image provided by Microsoft.
- `"customizations.vscode.extensions"`: Ensures the rust-analyzer extension is installed in VS Code.

### Step 2: Open the Project in a Dev Container

1. Open the project in VS Code.
2. Press Ctrl+Shift+P (or Cmd+Shift+P on Mac), type "Dev Containers: Reopen in Container," and select it.
3. VS Code will build and open the container. This may take a few minutes during the initial setup.
4. Once the container is ready, verify Rust is installed by running the command `rustc --version`.

## Part 3: Creating a Rust Project

### Step 1: Use cargo to Create a New Project

1. Inside the container, use cargo to create a new binary project.

   - Create a new project: `cargo new hello_comp423 --vcs none`
   - Navigate into the project directory: `cd hello_comp423`

#### What does `--vcs none` mean?

It prevents cargo from automatically creating a Git repository, as you’ve already initialized one manually.

### Step 2: Write Your "Hello COMP423" Program

1. Open the `src/main.rs` file in VS Code.
2. Replace its content with the following code:

        fn main() {
            println!("Hello COMP423");
        }

3. Save the file.

### Step 3: Build and Run Your Program

1. Compile the program using cargo build: `cargo build`.  
   The compiled binary is stored in the `target/debug` directory.

#### How does this compare to COMP211?

This is similar to using gcc to compile C programs in COMP211.

2. Run the binary directly: `./target/debug/hello_comp423`.

3. Alternatively, use cargo run to build and execute in one step: `cargo run`.

#### Difference Between `build` and `run`

- **cargo build**: Compiles the code without running it.
- **cargo run**: Combines compilation and execution, making it faster for testing changes.

## Part 4: Push Changes to GitHub

Now that your configuration is ready, let’s test it out:

1. Add and commit your changes:

        git add .
        git commit -m "Finished Rust tutorial"

2. Push the changes to GitHub:

        git push origin main

## Part 5: Why This Matters

By setting up a Dev Container and working with Rust, you’ve learned critical skills for modern software development:

- **Consistency**: Ensures that all developers work in identical environments.
- **Efficiency**: Automates environment setup, saving time.
- **Industry Standards**: Rust is widely used for high-performance and safe systems programming.

Congratulations! You've successfully created and configured a Rust Dev Container project. 🎉

* Primary author: [Mya Volety](https://github.com/mvolety)

* Reviewer: [Rachel Alvis](https://PartnerGithubProfileLink)
