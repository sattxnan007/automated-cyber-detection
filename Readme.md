🚀 How to Run
🐳 Docker Commands Reference
1. Victim Environment Setup (การตั้งค่าระบบจำลอง)
Deploy a vulnerable web application (DVWA) as a target for security testing.

Bash
# Run DVWA Server on Port 80
docker run --rm -it -p 80:80 vulnerables/web-dvwa
Note: This command pulls the image and starts the server on http://localhost.

2. Automated Attack Simulation (การโจมตีอัตโนมัติ)
Utilize sqlmap to automatically scan for SQL injection vulnerabilities and enumerate databases.

Bash
# Run SQLmap to list available databases
docker run --rm -it secsi/sqlmap \
  -u "http://host.docker.internal/vulnerabilities/sqli/?id=1&Submit=Submit" \
  --cookie="PHPSESSID=your_cookie_here; security=low" \
  --dbs --batch
Important: Replace your_cookie_here with your actual PHPSESSID from the browser's Developer Tools.

3. Data Extraction & Logging (การจัดการข้อมูลและไฟล์ Log)
Extract raw Apache access logs for behavioral analysis and machine learning training.

Identify the Container ID:

Bash
docker ps
Copy Access Logs to Host Machine:

Bash
docker cp <container_id>:/var/log/apache2/access.log ./dvwa_access.log
Data Mining Tip: This access.log file is the primary dataset used for our Anomaly Detection model in Google Colab.