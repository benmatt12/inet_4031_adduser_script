# INET4031 Add Users Script and User List
## Program description
This Python script automates the process of adding new users to an Ubuntu VirtualBox machine system. Instead of executing individual commands like adduser and grep for each user, this script reads from an input file and performs all necessary operations.
Normally, adding a user involves commands such as:
- `sudo adduser <username>`
- `grep <username> /etc/passwd`
- `grep <username> /etc/group`

This script allows administrators to define users and their groups in a single input file and execute the process with one command using Python. It reads each line, validates the format, and executes the system commands to create users, set passwords, and assign groups.

## Program User Operation
How to use the script:
1. Clone the repo.
2. Modify the `create-users.input` file to define the users you want to create.
3. Run the script with the input file piped into it.
4. Confirm the users were created using `grep <username> /etc/passwd`.

The script handles:
- Creating users
- Setting passwords
- Assigning users to groups

### Input File Format
Each line in the input file should follow this format:
`username:password:last_name:first_name:group1,group2`

To skip a line: start with `#`, and the script will ignore it.

To exclude group membership: use `-` in the group field.

### Command Execution
To run the script:
`chmod +x create-users.py
./create-users/py < create-users.input`

Make sure you have root privileges or run with `sudo` if required.

### "Dry Run"
If the user elects to do a "dry run" using the script, it will simulate the process without making any changes to the system.
In this mode, the script will:
- Read and parse each line of the input file
- Skip lines that are commented out
- Print status messages

This mode is useful for verifying that the input file is correctly structured and that the logic of the script is functioning as expected. It allows the user to confirm which accounts would be processed without making any real changes to the system.
