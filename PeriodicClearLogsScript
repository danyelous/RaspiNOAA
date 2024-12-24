# Clear Logs Script for Raspberry Pi
THe idea is to avoid to gfet the Raspberry Pi disk full with logs.

# Created with help of ChatGPT

This repository contains a script to clear system logs on a Raspberry Pi running Raspbian and a scheduled task to automate the process.

## Description
The script:
- Clears all log files in the `/var/log` directory.
- Removes rotated logs, including compressed (`*.gz`) and older (`*.1`) log files.

The schedule is set to run the script once a week using `cron`.

---

## Script Details
### Script: `clear_logs.sh`
```bash
#!/bin/bash

# Clear all log files
sudo find /var/log -type f -exec truncate -s 0 {} \;

# Remove rotated logs (compressed and `.1` files)
sudo find /var/log -type f -name "*.gz" -exec rm -f {} \;
sudo find /var/log -type f -name "*.1" -exec rm -f {} \;
```

### Steps to Create the Script
1. Create the script file:
   ```bash
   sudo nano /usr/local/bin/clear_logs.sh
   ```
2. Copy the script code above into the file.
3. Save and exit the editor.
4. Make the script executable:
   ```bash
   sudo chmod +x /usr/local/bin/clear_logs.sh
   ```

---

## Automating with Cron
### Schedule the Script to Run Weekly
1. Open the `crontab` editor:
   ```bash
   sudo crontab -e
   ```
2. Add the following line to schedule the script to run every Sunday at 2:00 AM:
   ```bash
   0 2 * * 0 /usr/local/bin/clear_logs.sh
   ```
3. Save and exit the `crontab` editor.

### Verify the Cron Job
To confirm the task is scheduled:
```bash
sudo crontab -l
```

---

## Testing the Script
To manually test the script, run:
```bash
sudo /usr/local/bin/clear_logs.sh
```

Check the `/var/log` directory to verify the logs have been cleared.

---

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
