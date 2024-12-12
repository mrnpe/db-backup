# db-backup

#  Database Backup Solution with Google Drive Integration

## **Project Overview**

Data is the backbone of any application, and losing it can have catastrophic consequences. Imagine waking up one day to find that your application’s database is corrupted, or worse, erased due to an unforeseen failure. Without a reliable backup strategy, such events could lead to significant downtime, loss of customer trust, and potentially irreparable damage to your business.

This project aims to provide a robust, automated, and easy-to-use solution for backing up your AWS RDS database and securely storing those backups on Google Drive with clear labeling for daily, weekly, biweekly, and monthly backups. The application ensures that only selected tables are backed up, providing flexibility and efficiency.

---

## **Features**

- **Automated Database Backups:** Backups are created for your specified tables using the `mysqldump` utility.
- **Google Drive Integration:** Backups are securely uploaded to Google Drive, ensuring off-site storage and easy access.
- **Custom Backup Schedules:**
  - Daily backups at 2 AM.
  - Weekly backups on Sundays at 3 AM.
  - Biweekly backups on the 1st and 15th of each month at 4 AM.
  - Monthly backups on the 1st of every month at 5 AM.
- **Selective Table Export:** Only specified tables are backed up, minimizing unnecessary storage usage.
- **Error Handling and Notifications:** Robust error handling to ensure backups are created and uploaded successfully. Logs provide clear feedback on success or failure.

---

## **Why Backups Matter**

- **Data Recovery:** A database backup is the first line of defense against data loss caused by accidental deletions, hardware failures, or cyberattacks.
- **Compliance and Audits:** Many industries require periodic backups to meet regulatory standards.
- **Business Continuity:** Regular backups ensure your business can recover quickly from a disaster without significant disruption.

Imagine a scenario where your database is wiped out due to a ransomware attack. Without a reliable backup, the recovery process could take days or weeks. With this solution, you’ll have peace of mind knowing that your data is securely stored and readily available for restoration.

---

## **How It Works**

1. **Database Backup:**

   - The application uses `mysqldump` to export the specified tables from your AWS RDS database.
   - Backup files are named based on the type of backup (daily, weekly, etc.) and the timestamp of their creation.

2. **Google Drive Upload:**

   - The backup files are automatically uploaded to Google Drive.
   - Files are organized with clear labels for easy identification and retrieval.

3. **Scheduled Tasks:**

   - Scheduled tasks ensure backups are created and uploaded at predefined intervals.

---

## **Setup Instructions**

### **1. Prerequisites**

- AWS RDS database with accessible credentials.
- Google Cloud project with the Drive API enabled.
- `mysqldump` installed and accessible on the server.
- Spring Boot environment setup.

### **2. Clone the Repository**

```bash
git clone <repository-url>
cd <repository-folder>
```

### **3. Configure Application Properties**

Edit the `application.properties` file to include your database and backup details:

```properties
rds.host=<RDS_HOST>
rds.username=<USERNAME>
rds.password=<PASSWORD>
rds.database=<DB_NAME>
backup.path=/path/to/backup/folder
```

### **4. Add Google Drive Credentials**

1. Download the `credentials.json` file from the Google Cloud Console.
2. Place the file in the `src/main/resources` directory.

### **5. Build and Run the Application**

```bash
mvn clean install
java -jar target/<application-name>.jar
```

---

## **Implementation Details**

### **1. Google Drive Integration**

- The application uses the Google Drive API to upload files securely.
- Files are labeled and stored in Drive folders for easy organization.

### **2. Backup Schedules**

- **Daily Backups:** Created every day at 2 AM.
- **Weekly Backups:** Created every Sunday at 3 AM.
- **Biweekly Backups:** Created on the 1st and 15th of every month at 4 AM.
- **Monthly Backups:** Created on the 1st of each month at 5 AM.

### **3. Selective Table Export**

- Only specified tables are backed up to ensure efficiency and save storage space.
- Update the `DatabaseBackupService` class to modify the tables to be exported.

---

## **Extending the Application**

- **Notifications:** Add email or Slack notifications to alert you when backups are successful or fail.
- **Restore Functionality:** Include functionality to restore backups from Google Drive.
- **Advanced Error Handling:** Enhance logging and alerting for better diagnostics.

---

## **Conclusion**

This application provides a seamless way to ensure the safety of your critical database data. With automated backups, cloud storage integration, and customizable schedules, you’ll be equipped to handle any data loss scenario with confidence. Remember, it’s not a matter of *if* data loss will happen, but *when*. Be prepared!

\
\
