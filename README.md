# Day-29-Integrating-Elastic-Defend-for-Incident-Response

Today, we’re integrating Elastic Defend, a robust endpoint detection and response (EDR) solution, into our Elastic Stack for enhanced endpoint protection. 

Let's dive in!

## Step 1: Installing Elastic Defend

1. **Access the Integrations Menu**: Navigate to Integrations and select Elastic Defend.
2. **Add Elastic Defend**.
3. **Choose Configuration Type**: Select Complete EDR to unlock full telemetry and advanced protection features.
4. **Select Endpoint Type**: Choose traditional endpoints.
5. **Add the Integration**: Attach it to an existing host policy (e.g., Windows — Policy).
6. **Fleet Server**: If using a Fleet Server, manage multiple agents seamlessly.
7. **Save and Deploy Changes** to complete the setup.

![Alt text](path/to/image.png)

## Step 2: Verify Installation and Endpoint Status

1. **Navigate to Security > Manage Endpoints**.
2. You should see your endpoint listed as active, indicating that Elastic Defend is running correctly.
   
  ![Alt text](path/to/image.png)

3. **Host Isolation (For Paid Users)**: Host isolation is unavailable in the free tier but is accessible for trial or paid versions. 

   **Note**: Free-tier users won't have access to host isolation, but Elastic Defend will still detect and quarantine malware effectively.

## Step 3: Testing Elastic Defend with Malware Detection

1. **Simulate Malware Activity**: On your Windows server, terminate the process for `svc-aurora.exe`. Then attempt to run it again—Elastic Defend blocked the action, displaying:
   - "Operation did not complete successfully because the file contains a virus or potentially unwanted software."
![Alt text]()
   
2. **View Telemetry in Elastic**: Navigate to Discover and search for malware. You should see a malware prevention alert, confirming that Elastic Defend blocked the file.

![Alt text](path/to/image.png)

## Step 4: Investigating Malware Prevention Alerts

1. **View the Alert**: Go to Security > Alerts and locate the malware prevention alert. View Details to get more insights.
   
   You’ll find critical details like:
   - Process Executable
   - File Path
   - File Hash
  
   ![Alt text](path/to/image.png)

2. **Set Up a Response Action**: 
   - Scroll to the Response section and click Edit Rule Settings.
   - Configure an automated response action, such as isolating the host when malware is detected.
   - Add a comment (e.g., "Testing response actions") and save changes.
   
  ![Alt text](path/to/image.png)

3. **Re-Test the Response**: Configure host isolation, and Elastic Defend isolates the server upon malware detection, blocking further malicious actions.

## Step 5: Downloading the Mythic C2 Agent

After `svc-aurora.exe` is quarantined, attempt to download the file again. Elastic Defend recognized the threat and immediately deleted the file.
