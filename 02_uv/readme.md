
##  **A. Introduction to `uv`**

### 🧠 What is `uv`?

**Simple Definition:**
`uv` is a **modern, fast tool** that helps Python developers manage:

* 🧩 **Projects** (folders and files)
* ⚙️ **Dependencies** (like libraries)
* 🌐 **Virtual environments** (Python environments)
* 🚀 **Packaging and running apps**

<br>
### 💡 Why we use `uv`?

Because it combines what `pip`, `venv`, and `poetry` do — **all in one tool**.
It is **super fast**, easy to use, and handles Python projects from setup to publishing.

<br>
<br>

## **B. Key Features of `uv`**

| Feature                   | Meaning (Simple Words)                                    |
| ------------------------- | --------------------------------------------------------- |
| ⚡ Speed                   | `uv` is written in Rust, so it’s much faster than pip.    |
| 📦 Dependency Management  | Installs and locks packages in seconds.                   |
| 🧰 Virtual Environments   | Automatically creates `.venv` folder for each project.    |
| 📘 pyproject.toml         | Central configuration file — replaces `requirements.txt`. |
| 🧠 Python Version Pinning | Fixes the exact Python version for your project.          |
| 🚀 Run Commands           | You can run code or scripts directly with `uv run`.       |

<br>

## 🅲️ **C. Types of Applications in `uv`**

There are two main project types you can create using `uv`:

1. **Simple Application** → for small projects or experiments.
2. **Packaged Application** → for professional projects you’ll share or publish.


<br>
<br>


---

## ⚙️ **D. UV Installation Guide**

Before using `uv`, you must have **Python** installed on your system.  
<br>

Below are **step-by-step instructions** for installing Python on **Windows**, **macOS**, and **Linux**, followed by **UV installation**.


## 💻 **Python Installation (Step-by-Step for All OS)**

<br>

### 🪟 **Windows**

#### ✅ Step 1: Download Python

🔗 Go to the official Python website:  
👉 [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/)

Click **"Download Python 3.x.x"** (latest version).


#### ✅ Step 2: Run the Installer

1. Double-click the downloaded `.exe` file.  
2. **Important:** Check the box ✅ **“Add Python to PATH”**  
3. Click **“Install Now”**
<br>

#### ✅ Step 3: Verify Installation

Open **Command Prompt** and type:

python --version

<br>
<br>

### 🍎 **macOS**

### ✅ Step 1: Use Homebrew (Recommended)

- First, install Homebrew (if not already installed):

- /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"


Then install Python:

- brew install python

### ✅ Step 2: Verify Installation
python3 --version


### ✅ Expected Output Example:

Python 3.00.0 (latest version)


## 🐧 **Linux (Ubuntu / Debian-based)**
### ✅ Step 1: Update System
sudo apt update

### ✅ Step 2: Install Python
sudo apt install python3 python3-pip -y

### ✅ Step 3: Verify Installation
python3 --version
pip3 --version


### ✅ Expected Output Example:

Python 3.00.0 (latest version)
pip 24.00 (latest version)

<br>
<br>

## UV Package Manager Installation (All OS)


### 💻 **Windows**

* ✅ **Step 1:** Open PowerShell as Admin
* ✅ **Step 2:** Run Installation Script
  ```powershell:disable-run
  powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
  ```
* ✅ **Step 3:** Verify
  ```bash
  uv --version
  ```

---

### 🍎 **macOS**

* ✅ **Option 1:** Install via Homebrew
  ```bash
  brew install uv
  ```
* ✅ **Option 2:** Install via Script
  ```bash
  curl -LsSf https://astral.sh/uv/install.sh | sh
  ```
* ✅ **Step 3:** Verify
  ```bash
  uv --version
  ```

---

### 🐧 **Linux**

* ✅ **Step 1:** Install via Curl
  ```bash
  curl -LsSf https://astral.sh/uv/install.sh | sh
  ```
* ✅ **Optional:** If Needed, Add to PATH
  ```bash
  export PATH="$HOME/.local/bin:$PATH"
  ```
* ✅ **Step 2:** Verify
  ```bash
  uv --version
  ```
<br>
<br>



## **E. Steps to Create a Simple Application**

Let’s create a simple app called `my-simple-app`.

---

### 🧩 Step 1 — Create the Project

Run:

```bash
uv init my-simple-app
cd my-simple-app
```

**It creates:**

```
my-simple-app/
├── .gitignore
├── .python-version
├── main.py
├── pyproject.toml
└── README.md
```

🧠 Explanation:

* `.gitignore`: files to ignore in git
* `.python-version`: locks the Python version
* `main.py`: your main Python script
* `pyproject.toml`: your project’s configuration
* `README.md`: info about the project

---

### ⚙️ Step 2 — Create the Environment

Run:

```bash
uv sync
```

This command:

* Creates `.venv/` (virtual environment)
* Creates `uv.lock` (locks dependencies)

Now your project is fully ready to run in isolation.

---

### 💻 Step 3 — Optional: Activate the Environment

If you want to use Python directly:

**Windows:**

```bash
.\.venv\Scripts\activate
```

**macOS/Linux:**

```bash
source .venv/bin/activate
```

To deactivate:

```bash
deactivate
```

🧠 Note: You don’t need to activate manually if you use `uv run`.

---

### 🧑‍💻 Step 4 — Open in VS Code

Run:

```bash
code .
```

Then select:

> Command Palette → “Python: Select Interpreter” → choose `.venv/python`

Now VS Code knows which Python version to use.

---

### ✍️ Step 5 — Write Your Code

Open `main.py` and add:

```python
def main():
    print("Hello from my-simple-app! — IB CODING SCHOOL")

if __name__ == "__main__":
    main()
```

---

### 🚀 Step 6 — Run the Application

Run directly using `uv`:

```bash
uv run python main.py
```

**Output:**

```
Hello from my-simple-app! — IB CODING SCHOOL
```

✅ No need to activate or manually run Python — `uv` handles it.

---

## 🅶️ **G. Optional: Advanced Run Methods**

### 🧩 1. Run as Module

```bash
uv run -m main
```

Runs your script as a Python module (useful for future expansion).

---

### ⚙️ 2. Add a CLI Command

Let’s make our app run with a simple command like `uv run myapp`.

Open `pyproject.toml` and add this:

```toml
[project.scripts]
myapp = "main:main"

[tool.uv]
package = true
```

Then run:

```bash
uv sync
uv run myapp
```

**Output:**

```
Hello from my-simple-app! — IB CODING SCHOOL
```

🧠 Here,
`myapp` = command name
`"main:main"` = means open `main.py` → run `main()` function.

---

## 🅷️ **H. Adding Packages**

Want to use an external library (like `requests`)?
Just run:

```bash
uv add requests
```

Now it’s automatically added to your `pyproject.toml` and locked.

---

## 🅸️ **I. Sharing or Reproducing the Project**

If you share your project with someone, they can recreate it exactly with:

```bash
uv sync --frozen
```

This ensures everyone uses the same versions of Python and dependencies.

---

## 🅹️ **J. Quick Command Reference**

| Task                 | Command                                                   |
| -------------------- | --------------------------------------------------------- |
| Create new app       | `uv init my-simple-app`                                   |
| Create environment   | `uv sync`                                                 |
| Activate environment | `source .venv/bin/activate` or `.\.venv\Scripts\activate` |
| Add dependency       | `uv add <package>`                                        |
| Run file             | `uv run python main.py`                                   |
| Run module           | `uv run -m main`                                          |
| Run custom CLI       | `uv run myapp`                                            |
| Recreate env exactly | `uv sync --frozen`                                        |
| Deactivate           | `deactivate`                                              |

---

## 🅺️ **K. Summary (Recap)**

* `uv` = All-in-one Python project manager (fast & modern)
* Simple App = No packaging, just scripts
* `uv init` → creates project
* `uv sync` → builds environment
* `uv run` → executes your app
* Optional: Add commands or dependencies
* Ideal for beginners, internal tools, and prototypes

---

## 🧠 Practical Example for Class

```bash
uv init hello-uv
cd hello-uv
uv sync

# Edit main.py:
# print("Hello, UV World! — IB CODING SCHOOL")

uv run python main.py
```

**Output:**

```
Hello, UV World! — IB CODING SCHOOL
```

---

Would you like me to now create:

1. 🎤 A **teacher script / lecture notes** version (what you’ll say in each slide), or
2. 🖼️ A **PowerPoint-style slide outline** for this same lecture (ready for class or YouTube)?
