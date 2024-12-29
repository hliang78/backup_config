### README

#### 1. Program Overview  
This program is designed to **automate the backup of network device configurations**. It reads a JSON file containing device information, connects to the specified network devices, and executes predefined commands to retrieve the current configurations. These configurations are then saved to a designated output directory for future reference or recovery.

##### What Can It Do?  
- **Automated Backups**: You can schedule or manually run the program to automatically connect to multiple network devices and back up their configurations, saving time and reducing manual errors.  
- **Multi-Device Support**: It supports various types of network devices (e.g., routers, switches, firewalls), ensuring compatibility across different brands and models.  
- **Multiple Connection Methods**: Supports both SSH and Telnet connections, adapting to different network environments and security requirements.  
- **Custom Commands**: You can specify the commands to execute in the JSON configuration file, allowing you to retrieve specific configuration details or device statuses.  
- **Smart Backup Management**: Backup results are organized by date and saved as text files named after the device, making it easy to manage and locate backups.  

##### Use Cases  
- **Routine Maintenance**: Network administrators can regularly back up device configurations to ensure quick recovery in case of device failures or misconfigurations.  
- **Change Management**: Before making network changes, back up the current configuration as a snapshot for easy comparison or rollback.  
- **Audit and Compliance**: Meet internal or external audit requirements by maintaining a complete history of configuration changes, ensuring compliance with relevant regulations.  
- **Disaster Recovery**: In the event of a major network failure, quickly restore device configurations from backup files to minimize downtime.  

#### 2. Configuration File Format  
The configuration file is in JSON format. Here’s an example:  

```json
[
    {
        "name": "device1",
        "device_type": "IOS",
        "ip": "192.168.1.1",
        "username": "admin",
        "password": "password",
        "auth_pass": "secret",
        "ssh": true,
        "commands": ["show version", "show running-config"]
    }
]
```

#### 3. Command-Line Arguments  
The program supports the following command-line arguments:  
- `-json`: Specifies the path to the JSON configuration file (default: `data.json`).  
- `-output`: Specifies the output directory (default: `./output/`).  
- `-filter`: Specifies filtering criteria. Can be used multiple times to add multiple filters. Example: `--filter conf --filter shut`.  

#### 4. Running the Program  
To start the program, run the following command in your terminal:  

```bash
config_backup -json=path/to/config.json -output=path/to/output/ --filter conf --filter shut
```

#### 5. Output Results  
The program creates a subdirectory based on the current date (e.g., `20231010`) and saves the command output for each device as a text file. The files are named after the device and stored in the specified output directory.  

#### 6. Supported Device Types  
Currently supported device types include:  
- IOS  
- SRX  
- ASA  
- HuaWei  
- Comware  
- F5  
- HillStone  
- NEXUS  

If an unsupported device type is encountered, the program will log an error and skip that device.  

#### 7. Error Handling  
- If reading or parsing the JSON file fails, the program will terminate and display an error message.  
- If creating the output directory fails, the program will terminate and display an error message.  
- If an unsupported device type is encountered, the program will skip the device and log an error.  
- If a command fails to execute, the program will continue processing the next device and log an error.  

#### 8. Notes  
- Ensure the IP addresses, usernames, and passwords in the configuration file are correct.  
- Ensure the target devices allow SSH or Telnet connections.  
- Ensure the output directory path exists and you have write permissions.  

#### 9. Support  
If you encounter any issues or need further assistance, please contact our technical support team.  

---  