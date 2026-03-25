# Create Your Own VPN

Deploy a secure, private VPN using **OpenVPN Access Server on AWS EC2**.  
This project demonstrates how to build, configure, and use your own VPN for encrypted communication and full control over your network traffic.
📄 [View Full Step-by-Step Guide](./create-your-own-vpn.pdf)
---

## Overview

A VPN (Virtual Private Network) creates an encrypted tunnel between your device and a remote server, ensuring:

- Secure data transmission
- IP address masking
- Safe access over public networks

Instead of relying on third-party VPN providers, this project helps you build and manage your own VPN infrastructure.

---

## Features

- Self-hosted VPN on AWS
- OpenVPN Access Server deployment
- Secure SSL/TLS encryption
- Admin & client web interfaces
- Multi-device client support
- Full control over users and access

---

## Tech Stack

- **Cloud:** AWS EC2  
- **VPN Server:** OpenVPN Access Server  
- **Client:** OpenVPN Connect  
- **Protocol:** SSL/TLS  

---

## Prerequisites

- AWS account
- Basic knowledge of EC2 and networking
- SSH access (key pair)
- OpenVPN Access Server AMI (AWS Marketplace)
- OpenVPN Connect installed on your device

---

## Architecture

```
        +----------------------+
        |   Client Device      |
        | (Laptop / Mobile)    |
        +----------+-----------+
                   |
                   | Encrypted VPN Tunnel (SSL/TLS)
                   |
        +----------v-----------+
        |   AWS EC2 Instance   |
        | OpenVPN Access Server|
        +----------+-----------+
                   |
                   | Decrypted Traffic
                   |
        +----------v-----------+
        |     Internet         |
        | (Web / Services)     |
        +----------------------+
```

### Flow

1. Client initiates VPN connection  
2. Traffic is encrypted before leaving the device  
3. OpenVPN server decrypts and forwards requests  
4. Internet sees VPN server IP instead of client IP  
5. Response returns through encrypted tunnel  

---

## Deployment Steps (High-Level)

1. Launch EC2 with OpenVPN Access Server AMI  
2. Configure instance (key pair, security group)  
3. SSH into the server (`openvpnas` user)  
4. Complete OpenVPN initial setup  
5. Access Admin Web UI  
6. Download client profile  
7. Connect using OpenVPN client  

> 📄 **For detailed step-by-step instructions, refer to the project PDF.**

---

## Connection Verification

After connecting:

- VPN status shows **connected**
- Traffic is routed through VPN tunnel
- Public IP changes to server IP
- Data usage visible in client dashboard

---

## Security Best Practices

- Use strong passwords
- Restrict security group access (avoid 0.0.0.0/0 where possible)
- Rotate credentials regularly
- Monitor login and usage logs
- Keep instance and packages updated

---

## Common Issues

**Connection failed**
- Check EC2 instance status
- Verify inbound rules (ports)
- Ensure correct public IP

**Admin UI not accessible**
- Confirm correct port and URL
- Check security group rules

**Client not connecting**
- Re-download profile
- Verify credentials
- Restart OpenVPN service

---

## Future Improvements

- Automate deployment using Terraform
- Add multi-user authentication
- Integrate logging/monitoring (CloudWatch)
- Implement MFA for admin access
- Add CI/CD for configuration updates

---

## Project Structure

```
.
├── README.md
├── create-your-own-vpn.pdf
└── docs/
```

---

## Conclusion

This project provides hands-on experience in:

- VPN fundamentals
- Secure network design
- AWS infrastructure deployment
- Client-server encrypted communication

---

## Author

**Soumya Ranjan Mohanty**
