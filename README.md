<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>
<h1 align = "center">osTicket - Prerequisites and Installation</h1>

## Platforms and Tools Used

- **Microsoft Azure** (Virtual Machines/Compute)
- **Remote Desktop Connection**
- **Internet Information Services (IIS)**

---

## Operating System

- **Windows 10** (Version 21H2)

---

## Requirements Checklist

1. Create an Azure Virtual Machine with Windows 10 (recommended: 4 vCPUs).
2. Download the necessary [osTicket installation files](https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6).
3. Activate IIS (Internet Information Services).
4. Install the Web Platform Installer.
5. Download and set up MySQL with a user account.
   - **For this tutorial:**
     - Username: `root`
     - Password: `Password1`
6. Install the required C++ Redistributable package.
7. Configure system permissions and proceed with the osTicket installation.
8. Optionally, keep a notepad handy for recording usernames and passwords.

---

## Step-by-Step Installation

### 1. Enabling IIS and Configuring HTTP Features

1. Open the **Control Panel** on your virtual machine and navigate to **Programs**.
2. Select **Turn Windows features on or off** under **Programs and Features**.
3. Check the box for **Internet Information Services (IIS)**.
4. Expand **Internet Information Services** > **World Wide Web Services** > **Application Development Features**, and enable **CGI**.
5. Ensure the options under **Common HTTP Features** are also selected.
6. Test the setup by entering `127.0.0.1` in your VM's browser. You should see the IIS welcome page.

---

### 2. Preparing Installation Files

1. Download the necessary files from the provided link, including **PHP Manager** and **Rewrite Module**.
2. Create a folder named `PHP` in the `C:` drive of your virtual machine.
3. Extract the contents of the **PHP 7.3.8** zip file into the `PHP` folder.
4. Install the **C++ Redistributable** and **MySQL 5.5.62** packages.
5. Launch the MySQL Configuration Wizard and:
   - Enable "Install As Window Service" with the default service name `MySQL`.
   - Set the password to `Password1` for this tutorial.

---

### 3. Configuring IIS with PHP

1. Open **IIS Manager** as an administrator.
2. Use the **PHP Manager** option to register the PHP version by pointing to the `php-cgi` file in the PHP directory.
3. Restart IIS for the changes to take effect.

---

### 4. osTicket Installation

1. Extract the `upload` folder from the osTicket zip file into `C:\inetpub\wwwroot` and rename it to `osTicket`.
2. In IIS Manager, navigate to **Default Web Site** > **osTicket** and launch the osTicket installer by selecting **Browse*.80 (http)**.
3. Enable necessary PHP extensions:
   - `php_imap.dll`
   - `php_intl.dll`
   - `php_opcache.dll`
4. Rename `ost-sampleconfig.php` to `ost-config.php` and update its permissions to allow full access.
5. Use a database management tool like **HeidiSQL** to create a new database named `osTicket`. Then configure the osTicket installer with:
   - Database: `osTicket`
   - Username: `root`
   - Password: `Password1`
6. Complete the installation and verify access to the help desk system.

---

### 5. Post-Installation Cleanup

1. Delete the `setup` folder from `C:\inetpub\wwwroot\osTicket`.
2. Set `ost-config.php` to "read-only" mode by adjusting its permissions.

---

## Final Notes

You have now successfully installed osTicket! If you encounter issues, verify that the required PHP extensions are enabled, database permissions are correctly set, and IIS settings are properly configured.


