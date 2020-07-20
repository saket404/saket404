---
layout: single
title: "Remote SSH using Visual Studio Code"
excerpt: "Learn how and why to use Vscode for connecting to remote servers"
date: 2020-07-20
last_modified_at: 2020-07-20
header:
  overlay_image: /assets/images/posts/ssh/1.png
  overlay_filter: 0.8
tags:
  - Ssh
  - Vscode
category:
  - Ssh
share: true
---
When working on a development project in the tech field, you often interact with remote servers. I ofen used to face difficulties in moving files and connecting to remote servers on Windows or Mac OS then I came across [**Visual Studio Code Remote - SSH**](https://code.visualstudio.com/docs/remote/ssh){:target='_blank'}. In this post I will show you how to connect to a remote server using SSH with Vscode and move files easily between your local computer and the remote server.

Content:
- [Connect SSH with Vscode](#ssh-with-vscode)
- [Moving files with Vscode between local and remote](#moving-files)

From Vscode docs:
>The Visual Studio Code Remote - SSH extension allows you to open a remote folder on any remote machine, virtual machine, or container with a running SSH server and take full advantage of VS Code's feature set. Once connected to a server, you can interact with files and folders anywhere on the remote filesystem.

![image-center](/assets/images/posts/ssh/official.png){: .align-center}

<sup>**Source**: [Vscode docs](https://code.visualstudio.com/docs/remote/ssh){:target='_blank'}.</sup>

I have created an instance on my univeristy's (unimelb) cloud platform as illustrated in the figure below. I will be using the `test` instance for today where we will connect to the instance using vscode remote ssh. I have setup the instance with my public ssh key. 
> **Note:**
> You can use any cloud platform as the basics would be the same. You would need your public key on the remote server (under authorized keys)
{: .notice--info}

![dashboard](/assets/images/posts/ssh/0.png "University of Melbourne Research Cloud")

***

### SSH with Vscode
At this stage, I assume you have an instance you want to connect and your public key resides on the server gaining you acess to it. Now using vscode to connect to the server can be done in 3 simple steps as shown below.

#### Step 1: Install extension
You have to first install the vscode extension for remote-ssh. You can do so by search for `ssh` in the extensions and installing the extension as shown below.

![install](/assets/images/posts/ssh/1.png)

#### Step 2: Add host to ssh config
Once the extension has been installed an icon will be pop up on the left side menu where you can establish a new connection to a remote server (host) as shown below.

![host](/assets/images/posts/ssh/2.png)

Now click on add new host and enter the ssh command for connecting to the remote server and pointing to your ssh key. Choose the config file you want to add the host to.

![connect](/assets/images/posts/ssh/3.png)

#### Step 3: Connect to host
The remote server (host) should be added to the list. In order to connect you an right-click and choose from the options based on you preference. 

![choose](/assets/images/posts/ssh/6.png)

Done! you can now connect your remote server and use its terminal in vscode.

![done](/assets/images/posts/ssh/5.png)

***

### Moving files
One of the great features of this extension is not requiring the use of another tool to move files between the remote server and your local machine.

#### Uploading files to remote server
Uploading files to remote servers can be easily done by simply dragging files to the vscode ui (under ssh) as shown below.

![png-up](/assets/images/posts/ssh/move1.gif)

#### Downloading files from remote server
Downloading files from remote servers can be easily done too by simply right-clicking and choosing download from the vscode ui as shown below.

![png-up](/assets/images/posts/ssh/download.gif)

***

<iframe src="https://giphy.com/embed/3o7btNa0RUYa5E7iiQ" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/latenightseth-boom-3o7btNa0RUYa5E7iiQ">via GIPHY</a></p>

You can check out additional features from the docs ([link here](https://code.visualstudio.com/docs/remote/ssh){:target="_blank"}).

Happy remote coding!











