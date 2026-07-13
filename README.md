# 🚀 Tomcat Java Application Deployment

## 📌 Overview

This project demonstrates the deployment of a Java web application (`ROOT.war`) on an Apache Tomcat server as part of a DevOps/Linux administration lab. The objective is to install Tomcat, configure a custom HTTP port, deploy the application, and verify that it is accessible through the browser or `curl`.

---

## 🎯 Objectives

* Install Apache Tomcat on the target application server.
* Configure Tomcat to listen on a custom port.
* Deploy a Java web application (`ROOT.war`).
* Verify successful deployment using HTTP requests.
* Practice Linux server administration and application deployment.

---

## 🛠️ Technologies Used

* Linux (CentOS/RHEL)
* Apache Tomcat
* Java
* SSH
* SCP
* Systemd
* Git & GitHub

---

## 📂 Project Structure

```text
tomcat-java-app-deployment/
│
├── README.md
├── commands.md
├── screenshots/
│   ├── tomcat-install.png
│   ├── tomcat-status.png
│   ├── server-xml.png
│   ├── deployment.png
│   └── curl-output.png
└── .gitignore
```

---

## ⚙️ Deployment Workflow

### 1. Install Tomcat

```bash
sudo yum install -y tomcat
```

### 2. Configure the HTTP Port

Edit the Tomcat configuration file:

```bash
sudo vi /etc/tomcat/server.xml
```

Locate the HTTP Connector:

```xml
<Connector port="8080" ...
```

Update the port according to the lab requirement (for example: `8084`, `8086`, `8088`, or `8089`).

---

### 3. Start and Enable Tomcat

```bash
sudo systemctl enable tomcat
sudo systemctl start tomcat
```

Verify:

```bash
sudo systemctl status tomcat
```

---

### 4. Copy the Application

Copy the application from the Jump Host:

```bash
scp thor@jump-host:/tmp/ROOT.war /tmp/
```

Deploy it:

```bash
sudo cp /tmp/ROOT.war /var/lib/tomcat/webapps/
```

---

### 5. Restart Tomcat

```bash
sudo systemctl restart tomcat
```

---

### 6. Verify Deployment

```bash
curl http://<server-name>:<port>
```

Example:

```bash
curl http://stapp02:8088
```

---

## ✅ Validation Checklist

* [x] Tomcat installed successfully
* [x] Custom HTTP port configured
* [x] `ROOT.war` deployed
* [x] Tomcat service running
* [x] Application accessible using `curl`

---

## 📚 Key Concepts Learned

* Apache Tomcat installation
* Java WAR deployment
* Tomcat configuration (`server.xml`)
* Linux service management with `systemctl`
* Secure file transfer using `scp`
* Application verification using `curl`
* Basic DevOps deployment workflow

---

## 🔍 Troubleshooting

### Check Tomcat Status

```bash
sudo systemctl status tomcat
```

### Verify Listening Port

```bash
sudo ss -tulpn | grep tomcat
```

### Restart Tomcat

```bash
sudo systemctl restart tomcat
```

### View Logs

```bash
sudo journalctl -u tomcat
```

---

## 📖 Learning Outcomes

After completing this lab, you should be able to:

* Install and configure Apache Tomcat.
* Deploy Java web applications using WAR files.
* Configure custom ports for web services.
* Troubleshoot Tomcat startup issues.
* Validate application availability from the command line.

---

## 👨‍💻 Author

**Abhishek K**

DevOps | Cloud | Linux | AWS | Docker | Kubernetes | CI/CD Enthusiast

---

## ⭐ Repository Purpose

This repository is part of a hands-on DevOps learning journey and serves as documentation for Tomcat deployment, Linux administration, and Java application hosting tasks.
