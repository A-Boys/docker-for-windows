<h1 align="center"> Docker Installation for Windows </h1>

![Image](https://github.com/user-attachments/assets/90872501-1c65-414c-b448-e0c9c6d764d5)

## Getting Started
### Step 1: Go to the docker official website at https://www.docker.com/

If you dont have a current docker account make sure to Sign-up or if you have, make sure to Sign-in first

 After You Sign-in or Sign-up you will be directed at https://app.docker.com/

Click the Docker Desktop , ` Go to download ` button 

After that click the download docker for your ` Windows `

For this Documentation we will use windows for it
##



### Step 3: Enable Window Features
On your desktop search for ` Windows Feature on or Off `

Once youre in, check the following:

* ✅ Hyper V or Windows Hypervisor Platform
* ✅ Windows Subsystem for Linux

Once you check the followings click ` Ok ` button then restart your desktop
##



### Step 4: Command Prompt Checking

Open your Command Prompt then check for your wsl default version, make sure the " Default Version " is 2, in order to check, Type:
```
wsl --status
```


if the ` Default Version ` is not set to ` 2 `, Type:
```
wsl --set-default-version 2
```
this will make the Default version to 2, to check it type ` wsl --status ` again and you will see the ` Default Version Changed `.

once the Default Version is 2, Find the Docker Desktop Installer then run it to perform installation
##




### Step 5: Docker Desktop

Once the docker desktop is installed , open Docker Desktop

Sign in your Docker Account and to make sure the docker is running find the ` ^ ` icon on your desktop taskbar then click on it


Once you click on it you will see a Docker icon and hover your mouse on it, you will see a pop up sayin, ` Docker Desktop is Running `.
##



### Step 6:  Check docker on CMD 

To make sure you have an installed docker, open command prompt then type:
```
docker version
```

this will show the full client docker version

Now to see the Docker images, type:
```
docker images
```

at first you will see 

` REPOSITORY   TAG       IMAGE ID   CREATED   SIZE `

this shows the table columns and will show a complete empty images as you didn't have one for now

now we will try to search or find some images, type:

```
docker search mysql
```

this command will show you the images related to ` mysql ` that indicated the ` STARS, OFFICIAL, AUTOMATED ` columns
##


> [ Note ♻️ ]  Once you find some errors make sure to post it on issue 🐳



