# Simple Linux Backup Script
A simple Bash script to create backups of a Linux filesystem.

## Overview
  - This is a one-shot, manually run script with no scheduled backups.
  - This Bash script is designed to create simple backups of a Linux system. It archives the contents of your root directory (/) allowing specific directories or files to be excluded based on user-defined criteria.
  - Each backup consists of multiple `*.tar.gz` archive files depending on number of items inside root directory and provided exclusions. Backups are saved in a designated directory (/backups) under a subdirectory named with a timestamp, ensuring that each backup is uniquely identifiable.
  - The script `zalohuj` uses external textfile `zalohuj_okrem` which should be located in the same directory as the script.
  - The text file `zalohuj_okrem` contains a list of paths (each on a separate line) that will be ignored (excluded) from the backup process.
  - The `/backups` directory is automatically excluded and does not need to be added to the exclusion file.
  - In addition to creating archive files, the script will also generate text files containing the list of installed packages (dpkg) and the root user's crontab.

## Prerequisites
The script must be run as root or with sudo to ensure it has the necessary permissions to access all files and directories.
The script utilizes standard Debian-based Linux utilities, such as: `bash`, `tar`, `dpkg`, `crontab`, `mkdir`, `cat`, `ls`, `realpath`

## Usage
  1. Download the script `zalohuj` and the textfile `zalohuj_okrem`, for example into `/usr/local/bin` location.
  2. Use `sudo chmod +x zalohuj` to make `zalohuj` file executable.
  3. Open file `zalohuj_okrem` for text editing and if needed, add or remove the paths that should be excluded from the backup process - each absolute path on separate new line. For example, if the file `zalohuj_okrem` contains following line: `/root/.local/share/Trash` then the Trash directory of root will not be processed.
  5. Run the file `zalohuj` as root or with sudo privileges.
  6. Follow the prompts.
