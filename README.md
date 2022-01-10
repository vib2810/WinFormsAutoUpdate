# WinFormsAutoUpdate
A repository demonstrating the usage of ClickOnce to deploy auto update features to your Windows Forms Code for FREE (hosting on raw github). Works for both .NET framework and .NET core.

A good article to follow: https://www.jeeshenlee.com/2020/10/how-to-host-clickonce-installer-on.html <br><br>
**Video Demonstration available here:**  <br>
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/iMEGtrjMXPU/0.jpg)](https://www.youtube.com/watch?v=iMEGtrjMXPU) <br>

In the clickonce installer
Follow the following steps:
1. If your project isn't on github, create a repository and push your code there. It has to be public.
2. On your computer, create a folder called 'published' in the root of your repository. Make sure this folder is not ignored in the .gitignore
3. Create a file called .gitattributes in this /published folder. Add the following contents
```
*.manifest binary
*.application binary
*.deploy binary
*  -text
```
4. How commit and push to the github repository. Navigate to this file in the repository click on the RAW button. Copy the URL address till '/publish/'. It will look like this <br>
```https://raw.githubusercontent.com/{your-account-name}/{your-repo-name}/{branch}/published/```
5. In the clickonce installer enter the following paths
    1. <b>Publish Path:</b> 
    ```{repo-path}/pubhished```
    2. <b>Install Path:</b> 
    ```https://raw.githubusercontent.com/{your-account-name}/{your-repo-name}/{branch}/published/```
    This the the server address from where the setup will install your application from. 
    3. <b>Update Path:</b> 
    ```https://raw.githubusercontent.com/{your-account-name}/{your-repo-name}/{branch}/published/``` 
    This the the server address from where the setup will check for updates. <br>
**NOTE:** Use this link to navigate through the clickonce installer: <br> 
https://docs.microsoft.com/en-us/visualstudio/deployment/quickstart-deploy-using-clickonce-folder?view=vs-2022. <br>
Make sure the check the 'Create Desktop Shortcut' option before publishing. Now commit and push your code.
6. Now in the /published folder click on the setup to install the application. This will connect the the github servers to download and install the required files on your computer in the directory ```C:\Users\vib28\AppData\Local\Apps\2.0```. 
7. To publish an update for the application follow these steps
    1. Make the changes to your c# applicaiton.
    2. Publish the application again (to the same folder /published). The revision number should increase, and there should be a new folder added to the location ```/published/Application Files```
    3. Commit and push your code to github. Now the raw files have been updated. So whenever the client runs his application, it will automatically prompt for downloading the update.
