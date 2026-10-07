# Linux File and Directory Management Lab
> **Disclaimer:** This lab was completed as part of the Google Cybersecurity Certificate (Coursera). The scenario, directory structure, and tasks come from the course. The command walkthrough and takeaways are my own documentation of the work I performed.
## Overview
Hands-on lab where I used Linux Bash commands to reorganize the `/home/analyst` directory and document the changes with the nano text editor. Well-organized data makes it easier to detect issues and keep data safe, so creating, moving, and removing files and directories are core tasks for a security analyst.

## Skills Demonstrated
- Navigating the Linux file system from the command line
- Creating and removing directories
- Moving and deleting files
- Creating and editing files with `touch` and `nano`
- Verifying every change with `ls` and `cat`

## Commands Used
| Command | Purpose |
|---|---|
| `mkdir` | Create a directory |
| `rmdir` | Remove an empty directory |
| `cd` | Change directory |
| `mv` | Move a file |
| `rm` | Delete a file |
| `touch` | Create an empty file |
| `nano` | Edit a file in the terminal |
| `clear` | Clear the terminal screen |
| `cat` | Display file contents |
| `ls` | List directory contents |

## Scenario
Reorganize `/home/analyst` and record the changes in a notes file.

**Before**
```
home
└── analyst
    ├── notes
    │   ├── Q3patches.txt
    │   └── tempnotes.txt
    ├── reports
    │   ├── Q1patches.txt
    │   └── Q2patches.txt
    └── temp
```

**After**
```
home
└── analyst
    ├── logs
    ├── notes
    │   └── tasks.txt
    └── reports
        ├── Q1patches.txt
        ├── Q2patches.txt
        └── Q3patches.txt
```

## Walkthrough

### Task 1: Create a new directory
Created a `logs` directory for future log files and confirmed it exists.
```bash
mkdir /home/analyst/logs
ls /home/analyst
```
Output: `logs  notes  reports  temp`

### Task 2: Remove a directory
Removed the unused `temp` directory and confirmed it is gone.
```bash
rmdir /home/analyst/temp
ls /home/analyst
```
Output: `logs  notes  reports`

### Task 3: Move a file
Moved `Q3patches.txt` from `notes` to `reports`, where it belongs.
```bash
cd /home/analyst/notes
mv Q3patches.txt /home/analyst/reports
ls /home/analyst/reports
```
Output: `Q1patches.txt  Q2patches.txt  Q3patches.txt`

### Task 4: Remove a file
Deleted the unused `tempnotes.txt` file and confirmed `notes` is empty.
```bash
rm tempnotes.txt
ls /home/analyst/notes
```
Output: (no files listed)

### Task 5: Create a new file
Created an empty `tasks.txt` file to document the work.
```bash
touch tasks.txt
ls /home/analyst/notes
```
Output: `tasks.txt`

### Task 6: Edit a file
Opened `tasks.txt` in nano and added a note describing the work.
```bash
nano tasks.txt
```
Text added:
```
Completed tasks
1. Managed file structure in /home/analyst
```
Saved and exited with `CTRL+X`, `Y`, then `ENTER`. Then cleared the screen and verified the contents:
```bash
clear
cat tasks.txt
```
Output:
```
Completed tasks
1. Managed file structure in /home/analyst
```

## Full Command Sequence
```bash
mkdir /home/analyst/logs
ls /home/analyst
rmdir /home/analyst/temp
ls /home/analyst
cd /home/analyst/notes
mv Q3patches.txt /home/analyst/reports
ls /home/analyst/reports
rm tempnotes.txt
ls /home/analyst/notes
touch tasks.txt
ls /home/analyst/notes
nano tasks.txt
clear
cat tasks.txt
```

## Key Takeaways
- `mkdir` and `rmdir` manage directories. `rmdir` only works on empty directories, which makes it a safer delete.
- `mv` both moves and renames files, so it keeps data organized without duplicating it.
- `rm` is permanent, with no recycle bin, so verify the filename before running it.
- Running `ls` after every change confirms the result and catches mistakes early.
- Keeping a change log like `tasks.txt` builds the habit of documenting actions, which matters in security work.

## Tools
- Linux Bash shell
- nano text editor
