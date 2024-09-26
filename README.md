# Phishing-Attack-Simulation
This repository contains a comprehensive guide and implementation of a phishing attack simulation tool using Gophish. The primary objective of this project is to enhance employee awareness of phishing threats within organizations by simulating real-world phishing attacks.

# Overview
Phishing is a prevalent and effective method used by attackers to gain access to sensitive information such as login credentials, financial records, and personal data. By utilizing Gophish, an open-source phishing framework, organizations can conduct phishing simulations to educate employees on identifying and reporting suspicious emails and communications.


[](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.cloudflare.com%2Flearning%2Faccess-management%2Fphishing-attack%2F&psig=AOvVaw21iFDC0zvDz7wOsS6hDKfi&ust=1727466897504000&source=images&cd=vfe&opi=89978449&ved=0CBQQjRxqFwoTCJDv8Omx4YgDFQAAAAAdAAAAABAE)![image](https://github.com/user-attachments/assets/193bec95-4800-4385-a896-b85f40aca967)



# We will be using Railway to host
Railway is a user-friendly app hosting platform that simplifies the deployment of production-ready applications. It supports various databases like PostgreSQL and MongoDB and allows you to deploy directly from a GitHub repository, automatically detecting the application runtime



[](https://alphasec.io/content/images/2022/07/Railway.png)![image](https://github.com/user-attachments/assets/fcfb4765-0f07-4b6c-a924-bedec24631c2)


# Deploy Gophish using forked repository
Start by logging into your GitHub account and forking the Gophish repository. Next, create an account on Railway using your GitHub credentials and authorize the Railway App when prompted. Make sure to review and accept Railway's Terms of Service and Fair Use Policy. Then, click on “+ New Project” and choose “Deploy from GitHub repo” to select your forked repository. The deployment process will begin right away, but additional configuration steps for Gophish will be necessary.




[
](https://alphasec.io/content/images/2022/07/Railway-new-project.png)![image](https://github.com/user-attachments/assets/7785cb08-f9f4-4574-97d7-c8056784aa0b)


Once the deployment is complete, go to Settings and select Domains to create a public-facing URL for your service. This will generate a default domain like xxx.up.railway.app. If you're interested in using a custom domain, check out my previous post for guidance.

Next, navigate to the Variables section and add a new variable named PORT, assigning it the value 3333, as this is the port the admin server will use. To find your admin server credentials, visit Deployments, click on View Logs, and look for the line that states, “Please login with the username admin and the password.”

Now, make the necessary edits in the config.json file of your forked Gophish repository:

Modify the listen_url from 127.0.0.1:3333 to 0.0.0.0:3333 to allow the service to accept connections from outside.
Change use_tls from true to false, as Railway will handle the TLS setup automatically.
Add your Railway domain to trusted_origins in the format "xxx.up.railway.app" (or your custom domain if you’ve set one up).
After committing these changes, Railway will trigger a new deployment. If all goes as planned, you should be able to access the service using the provided deployment URL.

# Then it should look like this

[
](https://alphasec.io/content/images/2023/01/Gophish-login.png)![image](https://github.com/user-attachments/assets/f3d48d29-a63e-46b7-a474-333e7c5e02bf)

# Run Phishing Attack Simulations with Gophish

[
](https://alphasec.io/content/images/2023/01/Gophish-dashboard.png)![image](https://github.com/user-attachments/assets/d1575a66-75fe-4da0-a05c-bac346224b44)

Login to the Gophish admin server using the temporary credentials found in the deployment logs, and change the password upon login.
Now that your setup is up and running, you can explore the various settings to create realistic phishing templates tailored to your needs. Start by configuring the following essential components:

Users & Groups: Define the recipients for your simulated phishing emails.
Phishing Email Templates: Create your email templates, including any necessary attachments (check supported formats).
Sending Profiles: Specify the SMTP relay details for sending your emails.
Landing Pages: Design the pages that users will see when they click on the phishing links.
After setting up these elements, it’s time to initiate a campaign. Go to the Campaigns section and select New Campaign. Most fields should be straightforward, allowing you to utilize the templates you previously configured. Ensure the URL points to your Gophish listener's domain, and then click Launch Campaign to start the simulation.


[
](https://alphasec.io/content/images/2023/01/Gophish-new-campaign.png)![image](https://github.com/user-attachments/assets/14fb041d-222f-4586-9eab-b503e0e39c30)

While it's ideal to expect that all users will be cautious and that any existing anti-phishing measures are effective, it's still important to monitor the results of your campaigns closely. Gophish allows you to track responses in near real-time from the campaign dashboard. Although it may lack some advanced features found in commercial phishing simulation tools, Gophish serves as a practical solution for organizations—especially startups—looking to evaluate their defenses against phishing attacks without breaking the bank. It’s a valuable tool for those just beginning to understand the impact of phishing simulations on their security awareness efforts.

[
](https://alphasec.io/content/images/size/w1600/2023/01/image-1.png)![image](https://github.com/user-attachments/assets/5e23f762-0f61-4351-9e80-1586dd577e17)



# Features
User-Friendly Setup: Deployed Gophish on Railway for easy management of phishing campaigns.
Customizable Templates: Created customizable phishing email templates and landing pages.
Real-Time Monitoring: Enabled near real-time tracking of phishing campaign responses and effectiveness.
Employee Training: Designed to test and improve employee resilience against phishing attacks.


