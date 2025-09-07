The "ssh.service not found" message means that the OpenSSH server package is missing on the Ubuntu system, so the SSH daemon cannot be started or managed.

Installation Steps
Update Package List
Run:
//sudo apt-get update
This ensures the latest package information is available before installing new software.

Install OpenSSH Server
Execute:
//sudo apt-get install openssh-server
This installs the OpenSSH server, which provides the sshd service needed for remote SSH connections.

Start the SSH Service
After installation, start the service with:
//sudo systemctl start ssh

You can also enable it to start automatically on boot:
//sudo systemctl enable ssh

Check status with:
//sudo systemctl status ssh
If successful, there will now be an "ssh.service" and PuTTY SSH connections should work.
