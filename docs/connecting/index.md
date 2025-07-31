# Establishing Connections to REPACSS

This document provides detailed instructions on establishing secure remote connections to the REPACSS high-performance computing system at Texas Tech University.

---

## System Access Requirements

Before attempting to connect to the REPACSS environment, users must confirm the following prerequisites:

- A valid and active TTU eRaider account
- A properly configured password and Multi-Factor Authentication (MFA)
- A secure connection to the Texas Tech University (TTU) network, either via wired Ethernet or the GlobalProtect VPN

<!-- The fully qualified domain name (FQDN) of the system is: -->

<!-- ```
repacss.ttu.edu
``` -->

---

## TTUnet & VPN Requirement

Access to REPACSS is restricted to users connected to the TTUnet network. Off-campus users, and users in buildings with known network limitations (e.g., the Computer Science Department), must use the **GlobalProtect VPN**.

For assistance configuring VPN access, refer to the following guide:

- [TTU GlobalProtect VPN Setup Guide](vpn.md)
- For further assistance please contact [**IT Help Central**](https://www.askit.ttu.edu/vpn)

!!! note "DNS Configuration Requirement"
    We noticed a common issue reported by many on-campus users. Even if you connect to TTUnet, please ensure your DNS is set to the default one rather than providers like Google (8.8.8.8). Otherwise, connecting to `repacss.ttu.edu` will fail, probably because it is not registered in public DNS.

!!! warning "VPN Required"
    **On Campus**:   
        **-** You must be connected to **TTUnet**, either via wired Ethernet or the TTUnet Wi-Fi network.    
        **-** Other networks on campus (such as TTUguest or EduRoam) are not supported for direct access.  
    **Off Campus**:   
        **-** If you are connecting from any other network, including TTUguest, EduRoam, or external internet connections, you must use the TTU GlobalProtect Virtual Private Network (VPN).   
        **-** Instructions are available on the [VPN Setup Guide](vpn.md).   
    **Authentication**: All system access requires secure login via SSH or authorized web-based interfaces.  
    <br> 
    *Note: Users located within the Computer Science Department building may experience restricted access when using TTUnet Wi-Fi. If you encounter connectivity issues, connect via wired Ethernet or enable the VPN to ensure uninterrupted access.*

---

## Connecting via Secure Shell (SSH)

### Instructions for Windows Users

For users operating Microsoft Windows, it is recommended to install and configure **MobaXterm**:

1. Download the installer from [https://mobaxterm.mobatek.net](https://mobaxterm.mobatek.net)
2. Launch MobaXterm and create a new SSH session with the following details:
   - **Remote Host**: `repacss.ttu.edu`
   - **Username**: Your TTU eRaider username
3. Save and initiate the connection

---

### Instructions for macOS and Linux Users

Users operating macOS or Linux systems can connect via the built-in terminal application:

```bash
ssh <your_eRaider_username>@repacss.ttu.edu
```

Upon successful authentication, the system will display a standard login banner.

---

## Troubleshooting SSH Connections

### Authentication Errors

Users may encounter "Permission denied" or "Too many authentication failures" messages due to the following:

- Incorrect credentials (eRaider username or password)
- VPN not active or improperly configured
- SSH client sending too many private keys

<!-- In the case of excessive key attempts, add the following SSH option:

```bash
ssh -o IdentitiesOnly=yes <your_eRaider_username>@repacss.ttu.edu
``` -->

---

### Host Key Verification Failed

If you receive a warning that the remote host identification has changed:

1. Open the file `~/.ssh/known_hosts`
2. Delete the line containing `repacss.ttu.edu`
3. Reconnect to the system and manually verify the new host fingerprint when prompted

---

### Additional Assistance

If all configuration steps have been completed and you are still unable to establish a connection, contact the system administrators. Be prepared to provide diagnostic output for further review:

- **Email**: [repacss.support@ttu.edu](mailto:repacss.support@ttu.edu)
- **Diagnostic Output**: Include the result of running the SSH command with the verbose flag:
  ```bash
  ssh -vvv <your_eRaider_username>@repacss.ttu.edu
  ```

---

