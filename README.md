# AWS-DLP-System
<p align="center">

  ![Screenshot 2024-11-12 164628](https://github.com/user-attachments/assets/27ae94a7-d37c-4c7f-a59b-7def146b3668)

</p>

In this project, I set up a real-time monitoring and alerting system using multiple AWS services to enhance security and data loss prevention (DLP) capabilities. This lab involved configuring Amazon GuardDuty and Amazon Macie to detect and monitor for high-severity security events and unusual data transfers in Amazon S3, particularly focusing on sensitive data protection and potential exfiltration.

To track and respond to incidents, I used Amazon CloudWatch for creating metric filters, alarms, and log queries that analyze findings from GuardDuty and Macie. For immediate notifications, Amazon SNS was configured to send alerts based on specific thresholds, such as high-severity security events, ensuring prompt responses to potential security threats.

Data from these findings was exported to Amazon S3 for centralized storage and periodic analysis. Using AWS QuickSight, I visualized the exported data, creating dashboards to showcase trends, alert frequency, and the overall effectiveness of DLP policies. This setup demonstrated a comprehensive security monitoring and alerting workflow that detects, tracks, and visualizes security events in real-time.




<h2>Environments and Technologies Used</h2>

- Amazon GuardDuty
- Amazon Macie
- Amazon CloudWatch
- Amazon SNS (Simple Notification Service)
- Amazon S3
- AWS QuickSight

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1 - Set Up AWS Macie for Data Classification and Sensitive Data Detection
- Step 2 - Enable GuardDuty for Threat Detection
- Step 3 - Set Up Monitoring and Reporting
- Step 4 - Validate DLP Policy Effectiveness

<h2>Deployment and Configuration Steps</h2>

- Step 1: Set Up AWS Macie for Data Classification and Sensitive Data Detection

AWS Macie helps identify and classify sensitive data within your S3 buckets, acting as the foundation for DLP.

![Screenshot 2024-11-10 193535](https://github.com/user-attachments/assets/fd87d81a-5e8e-4d1e-806d-beb021eb950e)

1. Configure Macie for S3 Bucket Scanning

![Screenshot 2024-11-10 195021](https://github.com/user-attachments/assets/4a7cff88-9a80-4056-9993-dc83b9e2c8de)
![Screenshot 2024-11-10 195328](https://github.com/user-attachments/assets/36d53e89-15a5-4f5f-bab4-17c49d55ac60)
![Screenshot 2024-11-10 195350](https://github.com/user-attachments/assets/f3324352-652b-48c4-937e-7e13236eb462)

- Step 2: Enable GuardDuty for Threat Detection

GuardDuty helps detect potential threats and unauthorized access attempts.

1. Create Alerts for GuardDuty Findings:

Go to Findings and set up filters for high-severity alerts, such as Unusual Data Transfer.

![Screenshot 2024-11-10 200623](https://github.com/user-attachments/assets/d75e9844-bdef-40a0-ab2f-52049d291458)

This setup will trigger the Lambda function whenever an unusual data transfer finding is detected by GuardDuty, allowing you to log the alert or take further automated action. Let me know if you need more help!
![Screenshot 2024-11-10 203035](https://github.com/user-attachments/assets/a5097680-4069-4fd9-9f52-0426c1862f1b)

![Screenshot 2024-11-10 203119](https://github.com/user-attachments/assets/e3f8d898-24d9-4031-9c76-911594f5de27)
![Screenshot 2024-11-10 203227](https://github.com/user-attachments/assets/1a43fb0f-ccd6-4091-87e6-0cb78ebced8d)

- Step 3: Set Up Monitoring and Reporting

- 1. Create a Metric Filter for GuardDuty Findings using Cloudwatch

![Screenshot 2024-11-12 151926](https://github.com/user-attachments/assets/af58eed9-04f9-4f5d-ab9a-61fed15be868)
![Screenshot 2024-11-12 152156](https://github.com/user-attachments/assets/342f6d22-f423-45ba-a81b-556ea5051294)
![Screenshot 2024-11-12 152455](https://github.com/user-attachments/assets/37a44188-77eb-420c-b6d9-e48ca3db4354)

- 2. Set Up a CloudWatch Alarm

![Screenshot 2024-11-12 153306](https://github.com/user-attachments/assets/7e7b2fd0-008e-4b6b-b902-638e35d7db76)

- 3. Automate Alerts with Amazon SNS

![Screenshot 2024-11-12 155513](https://github.com/user-attachments/assets/d35bab13-088b-4db6-9c12-e18f3918c669)
![Screenshot 2024-11-12 155653](https://github.com/user-attachments/assets/644893dc-1d2f-483b-a3db-76e89aaeb26d)

- 4. Add SNS as an Action in CloudWatch Alarms:

![Screenshot 2024-11-12 160141](https://github.com/user-attachments/assets/339e2578-1241-4929-8be1-679efeb668f0)

- 5. Periodic Reporting via AWS QuickSight

![Screenshot 2024-11-12 162300](https://github.com/user-attachments/assets/88c74171-df5b-46e8-a3e7-91c4cafd95b8)

Using these steps, I'll be able to query, filter, and export logs to S3, where QuickSight can then visualize the data for reporting and analysis. Let me know if you'd like more help setting up the automation. I wasn't able to document them yet because I had to wait for everything to update with the logs, which normally takes a few hours.

- Step 4: Validate DLP Policy Effectiveness

- 1. Simulate Data Exfiltration Attempts
     - Upload files with simulated sensitive data (like fake PII) to S3 buckets to test the sensitivity detection.
     - Monitor if Macie detects and classifies these appropriately.

![Screenshot 2024-11-12 163525](https://github.com/user-attachments/assets/d725063b-fe34-45cf-a6f5-46d0bb141b4d)
![Screenshot 2024-11-12 163536](https://github.com/user-attachments/assets/ac58b1fa-932f-4b75-8c41-22f6b9f7f390)

- 2. Generate Final Report
     - Use the data gathered from CloudWatch and QuickSight to prepare a report that highlights DLP effectiveness, with summaries of incidents, actions taken, and insights into potential policy adjustments.

![Screenshot 2024-11-12 163912](https://github.com/user-attachments/assets/aba08fa8-8d42-40ff-9913-f1e219484593)




















