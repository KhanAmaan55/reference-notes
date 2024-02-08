# Steps to get phpmyadmin on macos using apache and mysql

To install MySQL, PHPMyAdmin, and Apache on macOS, you can use Homebrew, a popular package manager for macOS. Follow the steps below:

### Step 1: Install Homebrew

If you don't have Homebrew installed, you can install it by running the following command in your terminal:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Step 2: Install MySQL

Use Homebrew to install MySQL:

```bash
brew install mysql
```

After the installation, start the MySQL service:

```bash
brew services start mysql
```

### Step 3: Install Apache

Apache is usually pre-installed on macOS. However, if you need to manage it with Homebrew, you can install or manage it using:

```bash
brew install httpd
```

After installation, start the Apache service:

```bash
brew services start httpd
```

### Step 4: Install PHP

Install PHP with the necessary extensions:

```bash
brew install php
```

### Step 5: Configure PHP

Edit the Apache configuration to load PHP. Open the Apache configuration file in a text editor:

```bash
nano /usr/local/etc/httpd/httpd.conf
```

Look for the following lines and uncomment (remove `#` at the beginning) or add them:

```apache
LoadModule php_module /usr/local/opt/php/lib/httpd/modules/libphp.so
AddType application/x-httpd-php .php
```
Save and exit the text editor.

### Step 6: Restart Apache server:

```bash
brew services restart httpd
```

Restart apache server and check whether you get *it works* text on  `http://localhost`
If not, check whether apache is configured at port 80 instead of 8000 or not, Also check if `index.html` file exists in `/usr/local/var/www`, if not present, create one and check


### Step 6: Install PHPMyAdmin

- Download zip file of phpmyadmin from its official website - https://www.phpmyadmin.net/downloads/
- Extract the zip file and rename folder as `phpmyadmin`
- Copy following folder to `/usr/local/var/www` folder using following command

```bash
cp -r ~/Downloads/phpmyadmin /usr/local/var/www
```

### Step 7: Configure Apache for PHPMyAdmin

Create a symbolic link to PHPMyAdmin in your Apache web root directory:

```bash
ln -s /usr/local/opt/phpmyadmin/share/phpmyadmin /usr/local/var/www/phpmyadmin
```

### Step 8: Restart Services

Restart Apache to apply the changes:

```bash
brew services restart httpd
```

### Step 9: Access PHPMyAdmin

You can now access PHPMyAdmin by opening your web browser and navigating to http://localhost/phpmyadmin/index.php.


# Error Debugging

## *"phpmyadmin is not showing or localhost is not hosted"*
If PHPMyAdmin is not showing up on localhost, there might be several reasons for this issue. Let's troubleshoot:

### 1. Verify Apache and PHP Installation:

Ensure that Apache and PHP are running properly. Open your browser and navigate to http://localhost. If you see the default Apache page, it means Apache is working. If you see any PHP info, PHP is also working.

### 2. Verify PHPMyAdmin Installation:

Make sure PHPMyAdmin is installed correctly. Check the installation path and verify that the symbolic link to PHPMyAdmin in the web root directory is correctly set. You should have a symbolic link like this:

```bash
ln -s /usr/local/opt/phpmyadmin/share/phpmyadmin /usr/local/var/www/phpmyadmin
```

Verify that the phpMyAdmin folder exists in the specified location.

### 3. Check Apache Configuration:

Make sure the Apache configuration is correctly set to allow access to the PHPMyAdmin directory. Open the Apache configuration file:

```bash
nano /usr/local/etc/httpd/httpd.conf
```

Ensure that there is a section allowing access to the PHPMyAdmin directory. It should look something like this:

```apache
<Directory "/usr/local/var/www/phpmyadmin">
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
```

If it's not there, add it, save, and restart Apache:

```bash
brew services restart httpd
```

### 4. Check PHP Configuration:

Ensure that PHP is correctly configured to work with Apache. Open the PHP configuration file:

```bash
nano /usr/local/etc/php/your-php-version/php.ini
```

Make sure the following lines are uncommented:

```apache
extension=mysqli
extension=pdo_mysql
```

Restart Apache after making changes:

```bash
brew services restart httpd
```

### 5. Check Logs:

Check Apache and PHP error logs for any issues:

- Apache error log: `/usr/local/var/log/httpd/error_log`
- PHP error log: `/usr/local/var/log/httpd/php_error.log`

Look for any error messages that might indicate the source of the problem.

### 6. Firewall Issues:

Ensure that your firewall is not blocking the connection. Check the system preferences to make sure Apache and PHP have the necessary permissions.

After going through these steps, you should be able to access PHPMyAdmin at http://localhost/phpmyadmin. If the issue persists, review the logs for error messages that may provide more details about the problem.


# Video Link For Tutorial
For video tutorial Click [Here](https://www.youtube.com/watch?v=SVNbRXUEDUg)
