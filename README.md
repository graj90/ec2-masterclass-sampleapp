
# Learning

This is a companion repository for my [**Amazon EC2 course on Udemy**](https://www.udemy.com/aws-ec2-masterclass/?couponCode=GITHUB)

Happy learning!

<p align="center">
    <a href="https://www.udemy.com/aws-ec2-masterclass/?couponCode=GITHUB">
        <img src="https://udemy-images.udemy.com/course/480x270/1527740_a494.jpg" alt="AWS EC2 Course Logo"/>
    </a>
</p>

# Content

 - Companion Java Application we'll use for this course

 - # added the all step to run it locally on EC2 Intances
 - # Setup and Run Java Application on Ubuntu EC2 – Step-by-Step

## 1. Connect to Your Ubuntu EC2 Instance

```bash
ssh -i /path/to/your-key.pem ubuntu@<your-ec2-public-ip>
```

---

## 2. Install Java, Maven, and Git

```bash
sudo apt-get update -y
sudo apt-get install -y openjdk-8-jdk git maven
```

---

## 3. Prepare the Directory and Clone the Repository

```bash
cd ~
rm -rf ec2-masterclass-sampleapp      # (Optional) Remove old directory if exists
git clone https://github.com/simplesteph/ec2-masterclass-sampleapp.git
cd ec2-masterclass-sampleapp
git checkout 28b8699ad80959a41affa2d9cca69938b7b52a92
```

---

## 4. Build the Project with Maven

```bash
mvn clean package
```

---

## 5. Run the Application (Standalone JAR)

Find the JAR file in `target/` directory, then run:

```bash
java -jar target/ec2-masterclass-sample-app-1.0-jar-with-dependencies.jar
```

---

## 6. Open Port 4567 in Your AWS Security Group

- Go to the EC2 Console → Security Groups → Edit Inbound Rules.
- Add TCP rule for port 4567, source 0.0.0.0/0 (or restrict to your IP).

---

## 7. Access the CPU Endpoint from Browser

Visit:
```
http://<your-ec2-public-ip>:4567/cpu
```
- Refresh the page to see live CPU usage.

(Optional: Use an auto-refresh browser extension or a simple HTML file to auto-refresh.)

---

## 8. Check Live CPU Usage via SSH

Open a second SSH terminal and run:

```bash
top
```
- Shows live CPU usage and running processes.
- Press `Shift + P` to sort by CPU usage.
- Press `q` to quit.

---

**Done!**  
You now have a Java app running on EC2, serving CPU usage data on a web endpoint, and you can also monitor live CPU stats via SSH.
