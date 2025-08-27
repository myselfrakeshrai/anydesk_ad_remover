# AnyDesk Ad Remover

## Overview
This batch script, `AnyDesk Ad Remover`, is designed to reset AnyDesk configurations by removing specific configuration files and thumbnails, stopping and restarting the AnyDesk service, and preserving user settings. It requires administrative privileges to run and is intended for users who want to reset AnyDesk to a clean state, potentially removing advertisements or unwanted configurations.

## Prerequisites
- **Operating System**: Windows
- **Permissions**: Must be run with administrative privileges
- **AnyDesk**: Installed on the system (either in `Program Files` or `Program Files (x86)`)

## Features
- Stops the AnyDesk service and terminates the AnyDesk process.
- Deletes AnyDesk service configuration files (`service.conf`) from both user and system directories.
- Backs up and restores the user configuration (`user.conf`) and thumbnails.
- Restarts the AnyDesk service and application after resetting.
- Checks for the presence of a valid AnyDesk ID in the system configuration before completing the process.

## Usage
1. **Run as Administrator**:
   - Right-click the batch script and select "Run as administrator" to ensure proper execution.
   - The script checks for admin privileges and will exit if not run as an administrator.

2. **Execution**:
   - The script stops the AnyDesk service and process.
   - It deletes configuration files (`service.conf`) from `%ALLUSERSPROFILE%\AnyDesk` and `%APPDATA%\AnyDesk`.
   - User settings (`user.conf`) and thumbnails are backed up to the `%temp%` directory.
   - After resetting, the script restores the backed-up user settings and thumbnails.
   - The AnyDesk service and application are restarted.

3. **Completion**:
   - Once the script finishes, it displays "Completed." in the console.
   - The AnyDesk application should launch automatically if installed in the default directories.

## Script Details
- **File Operations**:
  - Deletes `service.conf` files to reset AnyDesk configurations.
  - Backs up `user.conf` and the `thumbnails` folder to `%temp%`.
  - Restores `user.conf` and `thumbnails` after resetting.
- **Service Management**:
  - Uses `sc stop AnyDesk` to stop the AnyDesk service, looping until the service is stopped.
  - Uses `sc start AnyDesk` to restart the service, looping until the service is running.
  - Terminates the `AnyDesk.exe` process using `taskkill`.
- **Application Launch**:
  - Checks for AnyDesk executable in `Program Files` or `Program Files (x86)` and launches it.
- **Error Handling**:
  - Ensures the script runs with administrative privileges.
  - Loops until the AnyDesk service is fully stopped or started.
  - Verifies the presence of `ad.anynet.id` in `system.conf` before finalizing.

## Important Notes
- **Backup**: The script preserves user settings (`user.conf`) and thumbnails to prevent data loss.
- **Administrative Privileges**: Running without admin rights will cause the script to exit with a prompt.
- **AnyDesk Installation**: The script assumes AnyDesk is installed in the default directories (`Program Files` or `Program Files (x86)`).
- **Potential Risks**: Deleting configuration files may reset AnyDesk settings, including connection history or preferences. Use with caution.

## Troubleshooting
- **Script Exits Immediately**: Ensure you are running the script as an administrator.
- **AnyDesk Fails to Start**: Verify that AnyDesk is installed in the default directory and that the service is not disabled.
- **Files Not Found**: If configuration files or thumbnails are missing, the script will skip those steps and continue.

## Disclaimer
This script is provided as-is and should be used at your own risk. Modifying AnyDesk configurations may violate AnyDesk's terms of service. Ensure you have permission to modify the software's settings and that you understand the implications of resetting configurations.
