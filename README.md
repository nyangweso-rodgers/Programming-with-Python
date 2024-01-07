# Python

## Table of Contents

1. [Python - Getting Started]()

2. [Programming Paradigms in Python](#Programming-Paradigms-in-Python)

- [References]()
  - [Building modern Python API backends in 2022](https://sanjeevan.co.uk/blog/modern-python-backends)
  - [Python Project Ideas to Improve Your Résumé](https://www.freecodecamp.org/news/python-project-ideas-to-improve-your-resume/)
  - [140 Python Projects with Source Code](https://medium.datadriveninvestor.com/140-python-projects-with-source-code-fa12c9e2aeac)
  - [Backend Web Development with Python - Full Course](https://www.freecodecamp.org/news/backend-web-development-with-python-full-course/)

# Introduction to Python Programming Language

## How Python Works

- The python **source code** is first compiled into **Byte Code**. Though Python is an **interpreted language**, it first gets compiled into **byte code**. This byte code is then interpreted and executed by the **Python Virtual Machine**.

- This compilation and execution are what make Python slower than other low-level languages such as C/C++. In languages such as C/C++, the **source code** is compiled into **binary code** which can be directly executed by the CPU thus making their execution efficient than that of Python.

## `Pip` vs `Conda`: an in-depth comparison of Python’s two packaging systems

- `pip` is a package manager for Python. That means it’s a tool that allows you to install and manage additional libraries and dependencies that are not distributed as part of the standard library. JavaScript uses `npm` for package management, Ruby uses `gem`, and **.NET** use `NuGet`.
- In **Python**, `pip` has become the **standard package manager**.

- The fundamental difference between **pip** and **Conda** packaging is what they put in packages. **Pip packages** are **Python librarie** like `NumPy` or `matplotlib`. **Conda packages** include Python libraries (NumPy or matplotlib), C libraries (libjpeg), and executables (like C compilers, and even the Python interpreter itself).

# How to Configure VS Code for Python Environment

## Python Extensions

1. Install [Python Extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python) from Microsoft.

   - This is actually an extension pack that contains two extensions.
     - The first extension is the Python extension. It lays the foundation for Python development in Visual Studio Code.
     - The other one is [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance), which is a very performant language server for Python.

2. **Ruff Linter**

   - Ruff is an extremely fast Python linter written in Rust that imposes stricter linting rules than Pylint.
   - Install [Ruff](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff)

3. **Isort**:

   - Like a linter, [isort](https://marketplace.visualstudio.com/items?itemName=ms-python.isort) is another utility that's sole purpose is sorting import statements.
   - The utility sorts all the imports alphabetically, while also dividing them into sections.

4. **InteiCode**

   - [InteiCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode) provides AI assisted code completion in Visual Studio Code.

5. **Error Lens**

   - While not related to Python specifically, [Error Lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens) is a great extension that embeds errors right by the side of the line of code.

6. **Indent Rainbow**
   - [indent-rainbow](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow) adds some color to the identation.

# Introduction to Virtual Environments

- A **virtual environment** is a Python tool for **dependency management** and **project isolation**. They allow Python **site packages** (third party libraries) to be installed locally in an isolated directory for a particular project, as opposed to being installed globally (i.e. as part of a system-wide Python).

- At its core, the main purpose of **Python virtual environments** is to create an isolated environment for Python projects. This means that each project can have its own **dependencies**, regardless of what dependencies every other project has. i.e., when you activate a virtual environment for your project, your project becomes its own self contained application, independent of the system installed Python and its modules.

- Your new **virtual environment** has its own:
  - `__pip__` to install libraries,
  - `__libraries__`folder, where new libraries are added, and its own
  - `__Python interpreter__` for the Python version you used to activate the environment.

## Benefits of Python Virtual Environment

- development environment is contained within your project, becomes isolated, and does not interfere with your system installed Python or other virtual environments
- You can create a new virtual environment for multiple Python versions
- You are able to download packages into your project without admin privileges
- You can easily package your application and share with other developers to replicate
- You can easily create a list of dependencies and sub dependencies in a file, for your project, which makes it easy for other developers to replicate and install all the dependencies used within your environment
- Keep your global site-packages/ directory tidy by removing the need to install packages system-wide which you might only need for one project.

## How Python uses a virtual environment

- During start-up, Python automatically calls the **site.main()** function (unless you specify the **-S** flag). That function calls **site.venv()** which handles setting up your Python executable to use the virtual environment appropriately. Specifically, the **site** module:
  1. Looks for **pyvenv.cfg** in either the same or parent directory as the running executable (which is not resolved, so the location of the symlink is used)
  2. Looks for **include-system-site-packages** in **pyvenv.cfg** to decide whether the system **site-packages** ends up on **sys.path**.
  3. Sets **sys.\_home** if **home** is found in **pyvenv.cfg** (**sys.\_home** is used by **sysconfig**)

## Components Of a Python Virtual Environment

1. A `__site-packages/__` folder where third party libraries are installed
2. [Symlinks](https://en.wikipedia.org/wiki/Symbolic_link) to Python executables installed on your system.
3. [Scripts](https://en.wikipedia.org/wiki/Shell_script) that ensure executed Python code uses the Python interpreter and site packages installed inside the given virtual environment.

## Structure of Python Virtual Environment

1. `bin` (`Scripts` on Windows) on Unix.

2. `include` (`Include` on Windows) on Unix:

   - The `include` directory is for any header files that might get installed for some reason from a project.

3. `lib/pythonX.Y/site-packages` where `X`, `Y` is the Python version (`Lib/site-packages` on Windows) on Unix:

   - The `site-packages` directory is where projects get installed into the virtual environment (including `pip` if you choose to have it installed into the virtual environment).

4. `lib64` symlinked to `lib` if you're using a `64-bit` build of Python that's on a POSIX-based OS that's not macOS:

   - The `lib64` symlink is for consistency on those Unix OSs where they have such directories.

5. The configuration file is `pyvenv.cfg` and it lives at the top of your virtual environment directory (e.v. **.venv/pyvenv.cfg**). As of Python 3.11, it contains a few entries:
   - **home** (the directory where the executable used to create the virtual environment lives; **os.path.dirname(sys.\_base_executable)**)
   - **include-system-packages** (should the global **site-packages** be included, effectively turning off isolation?)
   - **version** (the Python version down to the micro version, but not with the release level, e.g. 3.12.0, but not 3.12.0a6)

## Setting Up Virtual Environment

1. Navigate to the root directory of your project using the terminal or command prompt.

2. Run the following command to create a new virtual environment: This will create a new directory called **env** in your project directory, which contains the virtual environment.

   ```sh
       python -m venv venv
   ```

3. Activate the virtual environment by running the following command: This will activate the virtual environment and change your shell's prompt to indicate that you're working within the virtual environment.

   ```sh
       source env/bin/activate  # For Linux or macOS
       source venv/Scripts/activate  # For Windows
   ```

## Installing Packages

- You can now install any required modules using `pip`, which will install them within the virtual environment. For example:

  ```sh
      pip install numpy
      # or, install a specific package
      pip install numpy==1.15.3
  ```

  - This will install the numpy module within the virtual environment, making it available for use in your project.

- By default, only `pip` and `setuptools` are installed inside a new environment.

  ```py
      pip list  # Inside an active environment
  ```

## Managing Environments Using `requirements.txt` File

- The easiest way to make our work reproducible by others is to include a requirements file in our project’s **root directory** (top directory). To do so, we’ll run `pip freeze`, which lists installed third party packages along with their version numbers,

  ```py
      pip freeze
  ```

- And write the output to a file, which we’ll call `requirements.txt`.

  ```py
    pip freeze > requirements.txt
  ```

- We can use this same command to rewrite our requirements file whenever we update a package or install a new one.

- Now anyone we share our project with will be able to run our project on their system by duplicating our environment using our `requirements.txt` file.

## Duplicating Environments

- Imagine our teammate Rpdgers has pulled down our **test-project/** from our team’s GitHub repository. On his system the project’s directory tree looks like:

  test-project/

        |---data
        |---deliver
        |---develop
        |---requirements.txt
        |---src
        |---tests

- Notice anything slightly — unusual? Yep, that’s right. There’s no venv/ folder. We’ve excluded it from our team’s GitHub repository because including [it can cause headaches](https://stackoverflow.com/questions/6590688/is-it-bad-to-have-my-virtualenv-directory-inside-my-git-repository)

- This is one reason having a `requirements.txt` file is essential to reproducing your project’s code.

- To run our **test-project/** on her machine, all Sara needs to do is to create a virtual environment inside the project’s root directory

  ```py
      Sara% cd test-project/
      Sara% python3 -m venv venv/
  ```

- And install the project’s dependencies inside an active virtual environment with the incantation `pip install -r requirements.txt`.

  ```py
      Sara% source venv/bin/activate
      (venv) Sara% pip install -r requirements.txt
  ```

# Resources

1. [freeCodeCamp](https://www.freecodecamp.org/news/how-to-setup-virtual-environments-in-python/)
2. [A Guide to Python’s Virtual Environments](https://towardsdatascience.com/virtual-environments-104c62d48c54)
3. [How virtual environments work](https://snarky.ca/how-virtual-environments-work/)
