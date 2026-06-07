
Problem 1: The target group showed Unhealthy

The website was not accessible through the Load Balancer.

#Root Cause: The application was not running on port 8000.

Fix:

Started the web server:

python3 -m http.server 8000

Learning: Health checks only succeed when the application is actively listening on the configured port.

---
Problem 2: Auto Scaling launched new instances, but the website did not work

Issue: Auto Scaling successfully created new EC2 instances, but the website was unavailable.

Root Cause:
The application was started manually through SSH
New instances did not automatically start the web server
The index file was not present in newly launched instance

Fix:

Used User Data in the Launch Template to start the application automatically.

#!/bin/bash
mkdir -p /home/ubuntu/website
cd /home/ubuntu/website

cat > index.html <<EOF
<html>
<head>
<title>Aman Verma AWS Project</title>
</head>
<body>
<h1>Aman Verma AWS Project</h1>
<p>Load Balancer + Auto Scaling + EC2</p>
</body>
</html>
EOF

nohup python3 -m http.server 8000 > server.log 2>&1 &


#Learning

Auto Scaling creates servers, but the application must also start automatically.

---

## Problem 3: NACL blocked website access

Issue: After restricting NACL rules, the website stopped working.

Root Cause: Only ports 80 and 8000 were allowed.

Ephemeral ports were blocked.

Fix: Allowed inbound ports:

1024-65535

Learning

NACLs are stateless and require ephemeral ports for return traffic.

---

How to access the Private Servers:
Access Bastian host >>> Copy the PEM file (linked to private servers) in Bastian host:
Copy Command: scp -i file_location file_path ubuntu@IPAddressofBastianhost
Access Private servers in Bastian: ssh -i Pemfilename ubuntu@privateIPAddress
