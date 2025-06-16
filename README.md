# Shell

This project implements a **Bash-like shell in C++**, offering standard shell functionalities along with additional utilities for malware detection and file deletion under locked conditions. It interacts directly with Linux system interfaces such as `/proc`, enabling process monitoring and control.

---

## 📑 Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Built-in Commands](#built-in-commands)
- [File Structure](#file-structure)
- [References](#references)
- [License](#license)

---

## 🧾 Introduction

This shell provides a command-line interface similar to Bash, supporting key functionalities like command execution, input/output redirection, piping, and background processing. It also includes **custom commands** such as:
- `sb`: Detects potential malware processes based on CPU heuristics.
- `delep`: Unlocks and forcefully deletes files currently in use.

The project is built using C++ and uses the Linux `/proc` file system and system calls to interact with processes and files.

---

## ✨ Features

- **Command Execution**: Supports internal and external command execution.
- **I/O Redirection & Piping**: Handles `<`, `>`, `|`, etc.
- **Background Execution**: Use `&` to run processes in the background.
- **Command History**: Integrated via GNU Readline.
- **Arrow Key Navigation**: Use up/down arrows to scroll through history.
- **Malware Detection (sb)**: Identifies idle parent processes with high child CPU usage.
- **File Deletion Utility (delep)**: Force-deletes locked or in-use files.

---

## ⚙️ Installation

### Clone the repository:
```bash
git clone https://github.com/ayushmohta7/custom-shell.git
cd custom-shell
```

### Build the shell:
```bash
make
```

Ensure you have a C++ compiler (e.g., `g++`) and `make` installed.

---

## ▶️ Usage

Run the shell:
```bash
./shell
```

You'll be presented with a prompt where you can execute shell commands and use custom utilities.

---

## 🛠 Built-in Commands

### 1. `sb` – SquashBug (Malware Detector)
Detects potential malware-like behavior using the following heuristic:
- If a sleeping parent process spawns many child processes that consume high CPU collectively, it is flagged as suspicious.
- CPU usage is calculated using `/proc/[pid]/stat`.
- Child hierarchy from `/proc/[pid]/task/[tid]/children`.

### 2. `delep` – Delete Locked Files
Unlocks and forcefully deletes a file even if it's in use by another process:
```bash
delep <filename>
```

---

## 📁 File Structure

| File/Folder         | Purpose                                   |
|---------------------|-------------------------------------------|
| `shell.cpp`         | Main shell implementation                |
| `sb.cpp`            | Malware detection logic (`sb` command)   |
| `delep.cpp`         | File deletion utility (`delep` command)  |
| `Makefile`          | Build configuration                      |
| `README.md`         | Project documentation                    |

---

## 📚 References

- [Linux Shell](https://en.wikipedia.org/wiki/Unix_shell)
- [`/proc` File System](https://man7.org/linux/man-pages/man5/proc.5.html)
- [GNU Readline](https://tiswww.case.edu/php/chet/readline/rltop.html)
- [Process Monitoring in Linux](https://linux.die.net/man/5/proc)

---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.
