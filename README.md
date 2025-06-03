# website-setup

A swift walk through on how to upload a website to a server using Vagrant

---

## 🧰 Prerequisites

- [Vagrant](https://www.vagrantup.com/) installed  
- VirtualBox or any compatible provider  
- Apache installed on the Vagrant box  
- A folder named `2135_mini_finance` containing your HTML, CSS, JS, and assets  

---


## 🚀 Step-by-Step Setup Instructions

### Tips

- Install a website template for test purpose from https://www.tooplate.com/ or use your website

---


### Run

- For the site
  
``` bash
wget https://www.tooplate.com/zip-templates/2135_mini_finance.zip
```

- To Unzip the file

  ``` bash
  unzip 2135_mini_finance.zip
  ```

- View to confirm

  ```bash
  ls
  ```

  ---


### 1. Go into your vagrant file, and enter your operating system and run all commands as a root user

```bash
vagrant up
vagrant ssh
sudo -i
```
---


### 2. Go to /tmp and Confirm your file was succefully downloaded

```bash
cd /tmp
ls
```
### Confirm to see:

```bash
2135_mini_finance
```

---


### 3. Copy Project Files to Apache's Web Directory
```bash
cp -r /tmp/2135_mini_finance/* /var/www/html/
```

Verify:

```bash
ls /var/www/html/
```
---


### 4. Ensure Apache is Running
Check Apache status:

```bash
sudo systemctl status httpd
```
If it's not running:

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```
---


### 5. Disable Firewall (If Applicable)
Check firewalld status:

```bash
sudo systemctl status firewalld
```

If it's active and blocking access:

```bash
sudo systemctl stop firewalld
sudo systemctl disable firewalld
```
---


### 6. Get Local IP Address for Access

```bash
ip a
```

Look for an IP like:

```text
192.168.56.11 (the IP address of your operating system)
```
---



### 🌐 Access the Site
Open your browser and visit:

```
http://192.168.56.11 (the IP address of your operating system)
```
---



### You should now see the Mini Finance dashboard.

- ✅ Directory Structure

- The following files should now exist under /var/www/html/:


---

About this template.txt
```
css/
fonts/
images/
js/
index.html
help-center.html
profile.html
setting.html
transation-detail.html
wallet.html
```
---


### 📌 For clarity sake

- This quick quick run through assumes you’re using a Network Address Translation or a Host-Only adapter that maps to 192.168.x.x.

- Apache serves from /var/www/html/ by default.

- If you make changes to HTML or CSS, refresh the browser (no restart needed), bye besties.

---



### Xoxo guys.
