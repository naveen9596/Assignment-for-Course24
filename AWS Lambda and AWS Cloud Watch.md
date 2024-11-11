Here's a sample assignment focused on using AWS Lambda and AWS CloudWatch for monitoring and automation:

---

**Assignment: Automating Monitoring and Alerting with AWS Lambda and CloudWatch**

**Objective:**
To understand how AWS Lambda can be used in conjunction with AWS CloudWatch for automated monitoring, alerting, and response.

**Scenario:**
You are a cloud engineer responsible for maintaining application uptime and performance on AWS. Your application runs on Amazon EC2 instances, and you want to monitor the CPU utilization and receive alerts when it crosses a certain threshold. Additionally, you want to automate the response when the threshold is exceeded by stopping and restarting the EC2 instance.

**Tasks:**

1. **Set Up the Infrastructure**
   - Create a new EC2 instance and ensure it is tagged appropriately for identification (e.g., `Environment: Development`).
   - Configure the EC2 instance security group to allow SSH access.

2. **Create a CloudWatch Alarm**
   - In AWS CloudWatch, create an alarm that triggers when the **CPU utilization** of the EC2 instance goes above 80%.
   - Configure the alarm to send a notification to an **SNS (Simple Notification Service) topic**. Set up an email subscription for this SNS topic.

3. **Develop the AWS Lambda Function**
   - Create an AWS Lambda function that performs the following actions:
     - Checks the CPU utilization of the EC2 instance when invoked.
     - If the CPU utilization exceeds 80%, the Lambda function should stop and then start the EC2 instance (simulating an automated recovery action).
   - Ensure the Lambda function has the appropriate IAM permissions to access EC2 instances and CloudWatch metrics.

4. **Configure CloudWatch Event to Trigger Lambda**
   - Set up a CloudWatch Event (EventBridge Rule) that triggers the Lambda function whenever the alarm state changes to `ALARM`.
   - Ensure that the EventBridge Rule is targeting the Lambda function correctly.

5. **Test the Lambda and CloudWatch Integration**
   - Simulate high CPU usage on the EC2 instance by running CPU-intensive commands.
   - Observe the CloudWatch alarm triggering when the CPU utilization exceeds 80%.
   - Verify that the Lambda function is invoked by checking the CloudWatch Logs associated with the Lambda function.
   - Confirm that the EC2 instance is stopped and then restarted automatically by the Lambda function.

6. **Document and Explain**
   - Document each step you followed, providing screenshots where necessary.
   - Explain how the CloudWatch alarm, SNS topic, Lambda function, and EventBridge Rule work together for automated monitoring and response.
   - Discuss potential improvements, such as adding custom error handling or incorporating additional monitoring metrics.

**Bonus Task (Optional):**
- Modify the Lambda function to write logs to CloudWatch whenever it performs a stop or start action on the EC2 instance.
- Set up a CloudWatch Dashboard to display real-time metrics (e.g., CPU utilization, memory usage) for the EC2 instance.

---

**Expected Outcome:**
- A working monitoring and automated response system where an alarm triggers the Lambda function to take action when CPU utilization is high.
- A detailed understanding of how AWS Lambda can be used in combination with CloudWatch for real-time monitoring and automation.
