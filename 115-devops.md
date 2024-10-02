Question: What are pipeline stages in your organization?
Answer: Pipeline stages in our organization include steps such as code checkout, build, unit testing, security scanning, artifact storage, deployment, and notification.

Question: What is the architecture of your application CICD deployment in the current organization?
Answer: The CICD architecture in my organization involves a Jenkins-based pipeline integrated with Git for version control, Docker for containerization, Kubernetes for orchestration, and Terraform for infrastructure provisioning. The pipeline also utilizes SonarQube for code quality checks and Prometheus/Grafana for monitoring.

Question: What is the issue have you faced in Jenkins non-prod to prod while building the Jenkins job?
Answer: Common issues include environment-specific configuration mismatches, inconsistent dependencies between non-prod and prod environments, and permission issues when promoting artifacts.

Question: Pipeline issues in Jenkins
Answer: Pipeline issues often involve failed stages due to timeout, incorrect configurations, dependency mismatches, and failed integrations with third-party tools like SonarQube or Docker registries.

Question: Production pipeline issues in Jenkins
Answer: Production pipeline issues include failed deployments due to incorrect environment variables, insufficient resource allocation, or untested edge cases in non-production environments.

Question: What are the build issues you have faced in your project?
Answer: Build issues often include dependency conflicts, versioning problems, missing libraries, and incorrect build configurations.

Question: Deployment strategies
Answer: Common deployment strategies used are blue-green deployment, rolling updates, and canary releases, depending on the criticality of the environment and risk tolerance.

Question: What are various plugins in your Jenkins Pipeline?
Answer: Plugins include Git, Docker, SonarQube, Pipeline (Declarative and Scripted), Kubernetes, Slack Notifications, and Email Extensions.

Question: How do you create a multi-branch Jenkins pipeline?
Answer: Multi-branch pipelines in Jenkins can be created by selecting "Multi-branch Pipeline" in Jenkins, configuring the SCM (e.g., Git), and defining the Jenkinsfile in each branch for the respective jobs.

Question: How do you upgrade Jenkins?
Answer: Jenkins can be upgraded either by downloading the new war file and replacing the existing one or using a package manager (e.g., apt-get or yum) if Jenkins was installed via package managers.

Question: What is a shared library?
Answer: A shared library in Jenkins is a reusable set of Groovy scripts that can be used across multiple pipelines to avoid redundancy and standardize pipeline code.

Question: What is Jenkins and security tools?
Answer: Jenkins can integrate with security tools like OWASP Dependency-Check, SonarQube, and Checkmarx for vulnerability scanning and code analysis during the build process.

Question: What is the Jenkinsfile, and how is it used in Jenkins pipelines?
Answer: A Jenkinsfile is a text file that defines the pipeline and stages in Jenkins, written in Groovy. It is used to automate the CI/CD process by defining build, test, and deployment stages.

Question: How to integrate SonarQube in a declarative pipeline?
Answer: SonarQube can be integrated by adding the SonarQube plugin to Jenkins, defining the sonar server in Jenkins, and using the sonarScanner block in the declarative pipeline to run the analysis.

Question: How to pass credentials in a pipeline?
Answer: Credentials can be passed in a pipeline using the Jenkins Credentials plugin, by storing credentials securely in Jenkins, and accessing them in the pipeline using the credentials() or withCredentials() method.

Question: What are the features of Jenkins?
Answer: Jenkins features include continuous integration and delivery, pipeline as code, scalability with master-slave architecture, extensive plugin support, and easy integration with various DevOps tools.

Question: What is Groovy in Jenkins?
Answer: Groovy is a scripting language used in Jenkins pipelines for writing both declarative and scripted pipelines, allowing users to define custom build logic and pipeline stages.

Question: Which command is used to start Jenkins?
Answer: The command java -jar jenkins.war is used to start Jenkins if running as a standalone service. Alternatively, Jenkins can be started as a system service.

Question: What are Declarative Pipelines in Jenkins?
Answer: Declarative pipelines are a simplified way of defining a Jenkins pipeline using a structured, predefined syntax that ensures better readability and error checking compared to scripted pipelines.

Question: How can you set up a Jenkins job?
Answer: A Jenkins job can be set up by selecting "New Item," configuring the job type (freestyle, pipeline, etc.), defining the build steps, triggers, and post-build actions, and integrating it with version control tools.

Question: How to create a backup and copy files in Jenkins?
Answer: Backup in Jenkins can be done by copying the Jenkins home directory ($JENKINS_HOME) and using plugins like the ThinBackup plugin to automate backups and restoration.

Question: How can you secure Jenkins?
Answer: Jenkins security can be ensured by enabling authentication (LDAP, Active Directory), role-based access control (RBAC), securing Jenkins with SSL, and using plugins like the "Matrix Authorization Strategy."

Question: What is the use of Backup Plugin in Jenkins? How to use it?
Answer: The Backup Plugin in Jenkins automates the backup process of Jenkins configurations, jobs, and plugins. It can be configured by installing the plugin, specifying the backup location, and scheduling periodic backups.

Question: What is the difference between a hard link and a soft link in Linux?

Answer: A hard link is a direct reference to the physical data on the disk, and multiple hard links can reference the same file. A soft link (symbolic link) is a pointer to another file's pathname. Deleting the original file breaks the soft link, but hard links remain intact.

Question: How can you check the memory usage of a Linux system?

Answer: You can check memory usage in Linux using commands like free -m, vmstat, or by checking /proc/meminfo. Additionally, tools like htop or top can provide real-time memory usage information.

Question: How do you find the IP address of a Linux system?

Answer: You can find the IP address using commands like ip addr show, hostname -I, or ifconfig. These commands display the system's network interfaces and associated IP addresses.

Question: What is the purpose of the "chmod" command in Linux?

Answer: The chmod command is used to change the file permissions in Linux. It allows you to define who can read, write, or execute a file (owner, group, or others).

Question: What is the purpose of the "grep" command?

Answer: The grep command is used to search for specific patterns or text within files. It is commonly used in conjunction with other commands to filter output based on a regular expression or string match.

Question: How do you change the password for a user in Linux?

Answer: You can change a user's password using the passwd command followed by the username. For example, passwd username will prompt for a new password.

Question: What is the purpose of the "crontab" in Linux?

Answer: The crontab command is used to schedule jobs (tasks) to run at specific times or intervals in Linux. It is part of the cron system for automating recurring tasks.

Question: How do you schedule a cron job in Linux?

Answer: To schedule a cron job, use the crontab -e command to edit the user's crontab file, then add a line specifying the time and the command to be executed in the format:

javascript
Copy code
* * * * * /path/to/command
where the five asterisks represent minute, hour, day of the month, month, and day of the week.

Question: Disk space full issue?

Answer: To resolve disk space full issues, you can check disk usage with the df -h and du -sh commands, then remove unnecessary files or clear log files. You might also need to clean up package caches or delete old backups.

Question: Running out of memory?

Answer: To troubleshoot running out of memory, use tools like top, htop, or free -m to identify processes consuming memory. You can then kill memory-intensive processes, add swap space, or upgrade physical RAM.

Question: How do you troubleshoot high CPU usage on a Linux server?

Answer: To troubleshoot high CPU usage, use the top or htop commands to identify processes consuming excessive CPU resources. You can then investigate or kill the processes, check for system misconfigurations, or optimize resource usage.

Question: Describe the boot process of a Linux system?

Answer: The Linux boot process involves:

BIOS/UEFI initialization.
The bootloader (e.g., GRUB) loads the kernel.
The kernel initializes hardware and mounts the root filesystem.
init (or systemd) starts and manages services.
The user is presented with a login prompt or graphical environment.
Question: You need to transfer a large file securely between two Linux servers. What tools or protocols would you use, and why?

Answer: To transfer a large file securely, you can use scp (secure copy) or rsync over SSH, as both encrypt the data during transmission. For large transfers, rsync is preferred because it supports resuming interrupted transfers and bandwidth control.

Question: A user accidentally deleted an important file, and you need to recover it from the backup. Explain the steps you would take to restore the file.

Answer:

Identify the backup system (e.g., rsync, tar, snapshot).
Locate the backup containing the deleted file.
Use the appropriate restore command (rsync, cp, or other) to recover the file to its original or new location.
Verify file integrity after restoration.
Question: A user reports that they are unable to connect to a remote Linux server using SSH. How would you troubleshoot and resolve this connectivity issue?

Answer:

Verify network connectivity using ping.
Check if the SSH service is running with systemctl status sshd.
Ensure the correct IP and credentials are being used.
Check for firewall rules or security groups blocking SSH (e.g., ufw, iptables, AWS security groups).
Review SSH logs (/var/log/auth.log or /var/log/secure).
Question: You need to find all files larger than 100MB in the /home directory and its subdirectories. How would you accomplish this task?

Answer: Use the find command:

arduino
Copy code
find /home -type f -size +100M
This will search for files in /home larger than 100MB.

Question: What is inode?

Answer: An inode is a data structure in Linux that stores metadata about a file or directory, such as permissions, ownership, size, and timestamps, but not the filename or its actual data.

Question: What is the booting process in Linux?

Answer: The booting process involves the BIOS/UEFI starting the bootloader, loading the kernel into memory, initializing the hardware, mounting the root filesystem, and starting the init or systemd process to manage services and users.

Question: How do you clear the server if you continuously get "Space not available"?

Answer: To clear space, identify large files using du -sh, clean up log files (/var/log), remove unused packages, clear cache (apt clean or yum clean), and delete old backups or temporary files.

Question: What are the Linux commands you use daily?

Answer: Common daily Linux commands include ls, cd, pwd, grep, chmod, chown, ssh, scp, rsync, systemctl, top, htop, df, du, ps, kill, nano, vim.

Question: Linux file permissions types?

Answer: Linux file permissions include:

r (read)
w (write)
x (execute) These can be set for the file owner, group, and others.
Question: How do you clear the server if you continuously get "Space not available"?

Answer: You can clear space by:

Checking disk usage (df -h).
Removing unnecessary or large files (du -sh).
Clearing log files.
Deleting old backups.
Cleaning package caches (apt-get clean or yum clean).

Question: What is CRONTAB?
Answer: CRONTAB is a file that contains the schedule of cron jobs, which are commands or scripts that are executed at specified times or intervals in Unix-like operating systems. Each line in the CRONTAB file represents a task that is to be run and includes the time and date fields followed by the command to be executed.

Question: How would you know the disk usage using the shell script commands?
Answer: You can use the df -h command to check the disk usage in a human-readable format. For specific directory usage, the du -sh <directory> command shows the total size of a given directory.

Question: Give the purpose of the shebang line?
Answer: The shebang (#!/bin/bash) at the start of a script specifies the path to the interpreter that should be used to execute the script. It ensures the script is executed in the correct environment.

Question: Tell us about the ‘$#’ use in shell scripting?
Answer: The $# variable in shell scripting represents the number of positional parameters passed to the script. It can be used to check how many arguments were provided when the script was run.

Question: Write a script to check vowels in a string
Answer:

bash
Copy code
#!/bin/bash
echo "Enter a string:"
read str
vowels=$(echo $str | grep -o -i "[aeiou]" | wc -l)
echo "Number of vowels: $vowels"
Question: Differentiate between @ and * in shell scripting?
Answer:

@: When used in double quotes, "$@" treats each argument as a separate string.
*: When used in double quotes, "$*" treats all arguments as a single string.
Question: How can you determine if a Linux server is virtualized or bare-metal?
Answer: You can use commands like lscpu, dmesg | grep -i hypervisor, or systemd-detect-virt. If the system is virtualized, it will show details about the hypervisor.

Question: Explain special variables in Shell
Answer:

$0: The name of the script.
$1, $2, ...: Positional parameters representing arguments passed to the script.
$#: The number of arguments passed to the script.
$@: All arguments passed to the script as separate quoted values.
$*: All arguments passed to the script as a single string.
$$: The process ID of the script.
$?: The exit status of the last executed command.
$!: The process ID of the last background command.