# PHPSetup

# Setting Up WAMP, LAMP, and MAMP Servers

This tutorial will guide you through the setup of WAMP (Windows), LAMP (Linux), and MAMP (macOS) servers for local web development.

---

## 1. WAMP (Windows)

### Prerequisites:
- A Windows PC
- Administrator privileges

### Steps:
1. **Download WAMP:**
   - Visit the [WampServer website](https://www.wampserver.com/) and download the appropriate version for your system (32-bit or 64-bit).

2. **Install WAMP:**
   - Run the installer and follow the on-screen instructions.
   - Choose a directory for installation (default is usually fine).
   - When prompted, select the default browser and PHP editor.

3. **Start WAMP:**
   - Launch WampServer from the Start menu.
   - The WAMP icon in the system tray should turn green, indicating the server is running.

4. **Test the Server:**
   - Open a browser and navigate to `http://localhost/`.
   - You should see the WAMP homepage.

5. **Add Your Website Files:**
   - Place your files in the `www` directory (default: `C:\wamp64\www`).
   - Access your site by visiting `http://localhost/your-folder-name/`.

---

## 2. LAMP (Linux)

### Prerequisites:
- A Linux distribution (e.g., Ubuntu, Fedora, or Debian)
- Terminal access

### Steps:
1. **Update the System:**
   ```bash
   sudo apt update
   sudo apt upgrade
   ```

2. **Install Apache:**
   ```bash
   sudo apt install apache2
   ```
   - Verify installation: Navigate to `http://localhost/` in a browser. You should see the Apache default page.

3. **Install PHP:**
   ```bash
   sudo apt install php libapache2-mod-php php-mysql
   ```
   - Restart Apache:
     ```bash
     sudo systemctl restart apache2
     ```

4. **Test PHP:**
   - Create a test file:
     ```bash
     sudo nano /var/www/html/info.php
     ```
   - Add the following content:
     ```php
     <?php
     phpinfo();
     ?>
     ```
   - Navigate to `http://localhost/info.php` in a browser.

5. **Add Your Website Files:**
   - Place your files in `/var/www/html`.
   - Access your site via `http://localhost/`.

---

## 3. MAMP (macOS)

### Prerequisites:
- A macOS system

### Steps:
1. **Download MAMP:**
   - Visit the [MAMP website](https://www.mamp.info/) and download the latest version.

2. **Install MAMP:**
   - Run the downloaded installer and follow the instructions.
   - By default, MAMP is installed in `/Applications/MAMP`.

3. **Start MAMP:**
   - Launch MAMP from the Applications folder.
   - Click "Start Servers."

4. **Test the Server:**
   - Open a browser and navigate to `http://localhost:8888/`.
   - You should see the MAMP start page.

5. **Configure PHP:**
   - Open MAMP preferences to switch PHP versions.

6. **Add Your Website Files:**
   - Place your files in the `htdocs` directory (default: `/Applications/MAMP/htdocs`).
   - Access your site via `http://localhost:8888/your-folder-name/`.

---

## PHP Programs to Test

Here are some simple PHP programs to execute after setting up your server:

1. **Hello, World!**
   - Create a file named `hello.php` in the respective web root directory (e.g., `www`, `htdocs`, or `/var/www/html`).
   - Add the following code:
     ```php
     <?php
     echo "Hello, World!";
     ?>
     ```
   - Access it in your browser: `http://localhost/hello.php`

2. **Basic Calculator:**
   - Create a file named `calculator.php`:
     ```php
     <?php
     $a = 10;
     $b = 20;
     echo "Sum: " . ($a + $b) . "<br>";
     echo "Difference: " . ($a - $b) . "<br>";
     echo "Product: " . ($a * $b) . "<br>";
     echo "Quotient: " . ($a / $b);
     ?>
     ```
   - Access it in your browser: `http://localhost/calculator.php`

3. **Form Handling:**
   - Create a file named `form.php`:
     ```php
     <!DOCTYPE html>
     <html>
     <body>
     <form method="post">
       Name: <input type="text" name="name"><br>
       <input type="submit">
     </form>
     <?php
     if ($_SERVER["REQUEST_METHOD"] == "POST") {
         $name = htmlspecialchars($_POST['name']);
         echo "Hello, " . $name;
     }
     ?>
     </body>
     </html>
     ```
   - Access it in your browser: `http://localhost/form.php`

4. **Factorial Calculation:**
   - Create a file named `factorial.php`:
     ```php
     <?php
     function factorial($n) {
         if ($n <= 1) {
             return 1;
         }
         return $n * factorial($n - 1);
     }

     $number = 5;
     echo "Factorial of $number is: " . factorial($number);
     ?>
     ```
   - Access it in your browser: `http://localhost/factorial.php`

5. **Prime Number Check:**
   - Create a file named `prime.php`:
     ```php
     <?php
     function isPrime($n) {
         if ($n <= 1) return false;
         for ($i = 2; $i <= sqrt($n); $i++) {
             if ($n % $i == 0) return false;
         }
         return true;
     }

     $number = 7;
     echo $number . (isPrime($number) ? " is a prime number." : " is not a prime number.");
     ?>
     ```
   - Access it in your browser: `http://localhost/prime.php`

---

## Troubleshooting
- Ensure the ports used by the server (e.g., 80 for WAMP/LAMP, 8888 for MAMP) are not blocked or used by other applications.
- Check logs for specific errors (e.g., Apache logs).
- Restart the server if changes are not reflected.

By following these steps, you can set up a local development environment tailored to your operating system and test basic PHP functionality.

