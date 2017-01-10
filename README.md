---
title: How to setup SAP HANA, Express Edition using the Cloud Appliance Library (CAL)
description: This tutorial will help you create an instance of SAP HANA, Express Edition in one of the two public cloud providers:  Amazon AWS or Microsoft Azure.
tags: [  tutorial>beginner, products>sap-hana\,-express-edition ]
---

## Prerequisites  
 - [Select the correct SAP HANA 2.0, express edition version](http://www.sap.com/developer/how-tos/2016/09/hxe-ua-version.html)

## Next Steps
 - Go to Step 4 on the [SAP HANA, Express Edition Developer Page](https://www.sap.com/developer/topics/sap-hana-express.tutorials.html)

## Details

### You will learn  
How to create a HANA Express Edition instance in your cloud provider, using the Cloud Appliance Library (CAL) system.
This tutorial provides step by step instructions to walk you through the CAL setup process.

### Time to Compete
This section takes about **10 minutes** to complete, and about **10 to 25 minutes** after completion to get the Virtual Machine started.

> ### Warning
>Both the Amazon AWS and Microsoft Azure accounts will charge you for time on those cloud systems.
>If you want to create a free developer account - with no cloud VM charges - on the HANA Cloud Platform, do not follow this tutorial. [Sign up for an account](http://www.sap.com/developer/tutorials/hcp-create-trial-account.html) here, and then proceed to the next tutorial.

---

1. Create a cloud account:

    - **Amazon AWS**:  To create an account, please visit [Amazon AWS](http://aws.amazon.com/account/)

    - **Microsoft Azure**:  To create an account, [sign up for a free one month trial](http://azure.microsoft.com/en-us/pricing/free-trial/).

2. To configure your HANA instance, go to the [Cloud Appliance Library](https://cal.sap.com/) page, and click the **login** link in the upper right hand corner.

    > ### Note
    >If you don't have an account on the sap.com website, you need to create one to access the Cloud Appliance Library.
    >Go to the [SAP website](http://www.sap.com/index.html) and click *login* in the upper right corner to create an account.

3. On the left, click on ***SOLUTIONS*** to see the systems available for use. Search for **express** in the search box to find  SAP HANA, Express Edition.

    ![Solution Selection](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/1.png)

4. Once you've found the instance through the search, you need to "activate" it. Activating an instance connects it to your account on Microsoft Azure or Amazon AWS. After the solution is activated, the link next to it should change to **Create Instance**.

5. Finally, click the "Create Instance" link on this solution to start the setup wizard. The wizard  will take you through a few simple steps and then you will have your instance up and running. These steps are outlined below.

    ![Simple Mode](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/2.png)

6. Choose your account, select your region, enter a name for your instance and password for your instance. This is the "simple" setup and only requires those couple of items to generate your instance.  

7. Optionally you can switch to the "Advanced" mode where you will have additional selections to make. Steps 8 through 11 will cover the "advanced" selection.  

8. From the advanced mode the first step is to select your account.  
	
	![Account Selection](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/3.png)

9. Next you will need to give details for this instance such as name and description as well as the network, subnet and whether you want the instance to have a static IP address.

	The network and subnet sections can use the default settings.  When you are ready, click **Step 3** to continue.

    ![Instance Details](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/4.png)

10. Choose the virtual machine size you want to use. Larger virtual machines can handle more data, and process faster, but cost more money. (The cost per hour on the screen is updated based on your selection.)

    ![Instance Size](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/5.png)

11. The next part of this section refers to the port addresses that are opened for the server, these are the standard ones that need to be opened for use of the majority of the server, later on you can reduce these to fit your specific needs.

	![Instance Ports](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/6.png)

12. Enter a password for your system.

    >The password rules can be confusing.  Choose a password between 8-9 characters, with at least one upper-case letter, one lower-case letter, and one number.
    >If your password does not follow the rules, a warning will appear on the screen.

    ![Password Rules](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/7.png)

13. Configure the schedule for the virtual machine. This option allows you to define a specific date when the machine will shut down, or a schedule when it should be running.  The virtual machine will suspend on the date you set.  

    >**Why do we require this?**  To prevent a virtual machine from running indefinitely. As you, the user, are paying for this VM by the hour, if it is left to run indefinitely you could have a huge bill at the end of the month.

    Click **Next** when you have set a run schedule, or a suspend date.

    ![Scheduling](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/8.png)

14. This screen shows all of your choices for review. To fix any problems, just click **Edit** that particular section. When you are done, click **Create**. The VM creation process will start.

    ![Review](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/9.png)

15. After the process of creating the VM starts, you will be prompted to download your "Key Pair".  This file will allow you to access your system using [SSH](http://en.wikipedia.org/wiki/Secure_Shell).

    > This feature is only for Amazon AWS.  Shell access is not yet available for Microsoft Azure.

	![PEM](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-setup-cloud/10.png)

    It will take about 10-25 minutes for your VM to start.  You can see your instance status by clicking on the **INSTANCE** tab of the Cloud Appliance Library main screen.

16. There are two ways to connect to your new HANA instance:

    - **Using a browser**.  Open your browser, and add the IP address of your instance to address bar.  Use the format:  `http://XXX.XXX.XXX.XXX`.  The web server (XSC) on the HANA instance has a getting started page with information, links to tools, and content. This also includes the links needed for accessing the XSA based tools.
    - **Using the HANA Studio**.  Install the [HANA Studio](https://tools.hana.ondemand.com/#hanatools) (which required Eclipse) on your local system.  Then, you can log in to HANA using the IP address, the username `SYSTEM`, and the password you specified in the setup process.

    ![Instanced](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-setup-cloud/11.png)

### Optional - Use SSH to log in to the Linux OS
Connecting to the underlying Linux OS in the cloud instances is different for each provider.  Follow the instructions for the cloud provider you have chosen to host HANA.

#### Amazon AWS
To connect to Amazon AWS, you **must** use the key-pair that was provided by Amazon when the instance was created.

**Connecting to AWS from Windows**

1. Open up the key-pair file (`*.pem`) that you downloaded previously copy the contents of the file to a new text file and save it. The file extension of this new file does not matter. Just save it to your local system.

    ![Review](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/12.png)

2. Google `PuTTY` and download both `putty.exe` and `puttygen.exe`

    ![Review](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/13.png)

3. Open `PuTTYgen` and select **Load**.

    ![Review](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/14.png)

    By default, only `.ppk` files will be selected. Change this to **All Files** and select the blank file you just saved which had the contents of the `.pem` file. After loading this, you will get the following message.

    ![Review](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/15.png)

4. Next, click on **Save Private Key** and say **Yes** to the alert. Save this to your system as a `.ppk` file. You can now close `PuTTYgen`

    ![Review](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/16.png)

5. Open `PuTTY`. Expand `SSH` and select `Auth` and then go to **Browse** and select the `.ppk` file you just saved.

    ![Review](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/17.png)

6. Under **Connection**, select **Data** and enter **root** as the Auto-login username.

    ![Review](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/18.png)

7. Select **Session** and enter the IP address of your instance and hit **Open**

    ![Review](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/19.png)
    
    You should get the following output.

    ![Review](https://github.com/AnnieSuantak/hxe-ua-installing-cal/blob/master/20.png)

8. You can now connect to your new HANA instance using HANA Studio. Please refer to the tutorial [How to download and install the HANA Eclipse plugin](http://www.sap.com/developer/how-tos/2016/09/hxe-howto-eclipse.html). You can log in to HANA using the IP address, the username `SYSTEM`, and the password you specified in the setup process.

For more detailed instructions, check out the [Amazon AWS guide to Connect Your Amazon EC2 Instance](http://docs.aws.amazon.com/gettingstarted/latest/computebasics-linux/getting-started-deploy-app-connect.html).

**Connecting to AWS from Mac or Unix**
From Linux or Mac OS-X, in terminal window, run this command: `ssh -i [hanakey].pem [IP Address] -l root` (Replace `[hanakey].pem` with the name of your key-pair file, and [IP Address] with the IP address of your instance.)

For more detailed instructions, check out the [Amazon AWS guide to Connect Your Amazon EC2 Instance](http://docs.aws.amazon.com/gettingstarted/latest/computebasics-linux/getting-started-deploy-app-connect.html).

#### Microsoft Azure
To connect from Windows, open puTTY, and enter the IP address.  The user name is `azureuser`, and the password is your master password.

To connect from Mac or Unix, use this command: `ssh azureuser@<ip address>` (Replace with the IP address of your Azure instance.)

For more detailed instructions, check out [Connecting to Microsoft Azure with SSH](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-use-ssh-key/).

### A few notes
- Some corporate firewalls may not allow SSH to Amazon cloud.  You may have to work with your IT organization to resolve this.
- User `hdbadm` owns sap software in the Linux instance. To restart the database without restarting the entire Linux instance, switch to user `hdbadm` and perform stop and start operations using the following commands:
  - `su – hdbadm` To switch user.
  - `./HDB stop` Command to stop HANA DB
  - `./HDB start` Command to start HANA DB
- The default password of user `hdbadm` is `HANAabcd1234`. You should change this password using the Linux command `passwd hdbadm` after creating your instance. Enter your new password (described above) when HANA Studio prompts you for the `<SID>adm` logon to perform administrative tasks.

## Next Steps
 - Go to Step 4 on the [SAP HANA, Express Edition Developer Page](https://www.sap.com/developer/topics/sap-hana-express.tutorials.html)
