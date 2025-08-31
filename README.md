
<div>
<p align="center"><h1 align="center">Terminal Executor</h1></p>
<p align="center">Terminal executor for AI agents, with ANSI escape sequence support and image screenshots.</p>
<p align="center">
<a href="https://github.com/james4ever0/termexec/blob/main/LICENSE"><img alt="License: UNLICENSE"
 src="https://img.shields.io/badge/license-UNLICENSE-green.svg?style=flat"></a>
<a href="https://pypi.org/project/termexec/"><img alt="PyPI" src="https://img.shields.io/pypi/v/termexec"></a>
<a href="https://pepy.tech/projects/termexec"><img src="https://static.pepy.tech/badge/termexec" alt="PyPI Downloads"></a>
<a href="https://github.com/james4ever0/termexec"><img alt="Code style: black" src="https://img.shields.io/badge/code%20style-black-000000.svg"></a>
</p>
</div>

## Demo

Using termexec for solving the "vimgolf-test" challenge:

![vimgolf-test-success](https://github.com/user-attachments/assets/011c21d7-5b4b-4836-ac14-e4b8126c3ab4)

More info at [vimgolf-gym](https://github.com/james4ever0/vimgolf-gym)

## Installation

```bash
# install from pypi
pip install termexec

# or install the latest version from github
pip install git+https://github.com/james4ever0/termexec.git
```

Note: if your platform does not have prebuilt binaries of agg-python-bindings, just install cargo and rustc so the source code could compile.

## Usage

```python
from termexec import TerminalExecutor
import time

# Initializes executor with a command to run in terminal emulator, using avt as backend, with automatic context cleanup
with TerminalExecutor(['bash'], width=80, height=24) as executor:
    # Waits for the terminal emulator to be ready.
    time.sleep(1)  # Adjust sleep time as necessary for your environment

    # Get the current display of the terminal emulator as a string.
    terminal_text = executor.display
    print("Terminal Display:")
    print(terminal_text)

    # Send input to the terminal emulator.
    executor.input("echo Hello, World!\n")
    print("After input:")
    print(executor.display)

    # Saves the current display of the terminal emulator as a .png file
    executor.screenshot("screenshot.png")
    print("Screenshot saved as screenshot.png")

    # Get the PID of the terminal process.
    print("Terminal process PID:", executor.terminal.pty_process.pid)
```

## Alternatives

- Xterm.js running in phantomjs, electron or headless playwright

- LXterminal running in kiosk mode with x11vnc and novnc

## License

The Unlicense
