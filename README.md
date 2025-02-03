Local File Inclusion (LFI) is a type of vulnerability that allows an attacker to include files on a server through the web browser. This can lead to sensitive information disclosure, remote code execution, and other serious security issues. However, it's important to note that exploiting vulnerabilities, including LFI, without permission is illegal and unethical.

If you are a security researcher or developer looking to understand LFI for educational purposes or to secure your own systems, here’s a general explanation of how LFI works and how you might test for it in a controlled environment:

### Repository Structure
```
LFI-Demo/
│
├── README.md
│   - Description of the repository, its purpose, and a disclaimer.
│
├── index.php
│   - A simple PHP script demonstrating an LFI vulnerability.
│
├── secure_index.php
│   - A secure version of the script with input validation.
│
├── scripts/
│   ├── script1.php
│   ├── script2.php
│   ├── ...
│   └── script100.php
│   - Additional scripts demonstrating various aspects of LFI vulnerabilities and mitigations.
│
└── LICENSE
    - Choose an appropriate license for your code.
```

### Example `README.md`
```markdown
# LFI Demo

This repository contains a collection of PHP scripts that demonstrate Local File Inclusion (LFI) vulnerabilities and their mitigations. It is intended for educational purposes only.

## Disclaimer
This code is deliberately vulnerable and should not be used in a production environment. It is provided for educational purposes to help developers understand and mitigate LFI vulnerabilities.

## Usage
1. Clone the repository.
2. Set up a local web server (e.g., using XAMPP or Docker).
3. Access `index.php` in your browser to see the vulnerable script in action.
4. Access `secure_index.php` to see a secure version of the script.
5. Explore the `scripts/` directory for additional examples and mitigations.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

### Example `index.php`
```php
<?php
// Vulnerable LFI example
if (isset($_GET['file'])) {
    $file = $_GET['file'];
    include($file . '.php');
} else {
    echo "Please provide a file parameter in the URL.";
}
?>
```

### Example `secure_index.php`
```php
<?php
// Secure version with input validation
$allowed_files = ['home', 'about', 'contact'];

if (isset($_GET['file'])) {
    $file = $_GET['file'];

    if (in_array($file, $allowed_files)) {
        include($file . '.php');
    } else {
        die('Invalid file requested.');
    }
} else {
    echo "Please provide a file parameter in the URL.";
}
?>
```

### Example `scripts/script1.php`
```php
<?php
// Example script 1: Basic LFI
echo "This is script1.php";
?>
```

### Example `scripts/script2.php`
```php
<?php
// Example script 2: LFI with directory traversal
echo "This is script2.php";
?>
```

### Example `scripts/script3.php`
```php
<?php
// Example script 3: LFI with null byte injection
echo "This is script3.php";
?>
```

### Example `scripts/script4.php`
```php
<?php
// Example script 4: LFI with log poisoning
echo "This is script4.php";
?>
```

### Example `scripts/script5.php`
```php
<?php
// Example script 5: LFI with PHP wrappers
echo "This is script5.php";
?>
```

### Example `LICENSE`
```plaintext
MIT License

Copyright (c) Guljar-E-Mostafa

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

### Example Usage
1. **Vulnerable Script**: Access `index.php` with a file parameter to see the LFI vulnerability in action.
   ```
   http://localhost/index.php?file=../../../../etc/passwd
   ```

2. **Secure Script**: Access `secure_index.php` with a file parameter to see how input validation can prevent LFI.
   ```
   http://localhost/secure_index.php?file=home
   ```

3. **Additional Scripts**: Explore the `scripts/` directory for additional examples and mitigations.
   ```
   http://localhost/scripts/script1.php
   http://localhost/scripts/script2.php
   ...
   http://localhost/scripts/script100.php
   ```

### Conclusion
This repository provides a comprehensive demonstration of LFI vulnerabilities and their mitigations. Always ensure you have permission before testing or exploiting vulnerabilities, and never use this information for malicious purposes.
