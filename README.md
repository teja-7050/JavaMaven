# Mock Project Documentation

This is a sample Maven-based Java project created for demonstration purposes. The project includes placeholder modules that represent controllers, services, and repository components, which are commonly used in layered application structures. The intention of this mock content is to act as a filler for documentation tests, file conversions, or Markdown rendering checks within a Java Maven setup.

The project assumes typical behaviors found in enterprise applications. A controller would normally receive incoming requests, a service would execute the required business rules, and a repository would handle the data operations. In this mock environment, however, no actual external systems are connected. All operations are simulated to maintain simplicity while preserving the structure of a real application.

The project relies on Maven as the dependency manager and build tool. Common dependencies for logging and testing are usually included in the pom file, but in this mock version their presence is only implied. The project can theoretically be extended by developers who wish to add modules, utilities, or additional layers according to their requirements.

This text exists purely as placeholder documentation. It is not connected to any real implementation, business logic, or system integration. It is intended for testing Markdown display, conversion workflows, or sample content within a Java Maven directory.


































8. Jenkins Automation
Steps for MavenJava Automation
Step 1: Open Jenkins (localhost:8888)
Click on "New Item" (left side menu) and name it as maven_java > select freestyle project > click on
“OK”

Step 2: Configuration of maven_java project
Give the description

In the source code management select git and give the git repo link

In the build steps click on add build step > give maven version as MAVEN_HOME > select invoke top-
level maven targets > goals as clean

In the build steps click on add build step > give maven version as MAVEN_HOME > select invoke top-
level maven targets > goals as install

In the post build actions > click on add post build action > select the archive the artifacts > in the file to
archive give “*/”
For the second post build action,

In the post build actions > click on add post build action >select build other projects > give projects to
build as MavenJava_Test
Click on apply and save

If the build is success:

Step 3: Create Freestyle Project (e.g., MavenJava_Test)

Click on new item> give item name as mavaen_java_test or MavenJava_Test and select free style project
and click ok

Step 4: Configuration of maven_java project
Give the description

In the source code management select none and in environment select “delete workspace before build
starts”

In the build steps> select add a build step> select “copy artifacts from another project” > give project
name as Maven java and artifacts to copy as */

In the post build ac 3 ons> select archive the ar 3 facts and enter files as */
Click on apply and save

In the dashboard you will find MavenJava and MavenJava_Test

If you open the MavenJava file the following will be shown in case on no errors

If you open the MavenJava_Test file the following will be shown in case on no errors

MavenJava_pipeline

II. Maven Web Automation Steps:
Create Freestyle Project (e.g., MavenWeb_Build)
Step 1: Open Jenkins (localhost:8888)
Click on "New Item" (left side menu) and name it as maven_web_build> select freestyle project > click
on “OK”

Step 2: Configuration of maven_web_build project
Give the description

In the source code management select git and give the git repo link

In the build steps click on add build step > give maven version as MAVEN_HOME > select invoke top-
level maven targets > goals as clean
For the second build step,
In the build steps click on add build step > give maven version as MAVEN_HOME > select invoke top-
level maven targets > goals as install

In the post build actions > click on add post build action > select the archive the artifacts > in the file to
archive give “*/”
For the second post build action,
In the post build actions > click on add post build action >select build other projects > give projects to
build as maven_web_test
Click on apply and save

Create Freestyle Project (e.g., MavenWeb_Test):
Step 1: Open Jenkins (localhost:8888)
Click on "New Item" (left side menu) and name it as maven_web_test> select freestyle project > click on
“OK”

Step 2: Configuration of maven_web_test project
Give the description

In the source code management select none and in environment select “delete workspace before build
starts”

In the build steps click on add build step > select copy artifacts from another project > give project name
as maven_web_build > give artifacts to copy as */

In the build steps click on add build step > give maven version as MAVEN_HOME > select invoke top-
level maven targets > goals as test

In the post build actions > click on add post build action > select the archive the artifacts > in the file to
archive give */

In the post build actions > click on add post build action >select build other projects > give name as
maven_web_deploy> select “trigger only if build is stable”

If the build is success:

Create Freestyle Project (e.g., MavenWeb_Deploy):
Step 1: Open Jenkins (localhost:8888)

Click on "New Item" (left side menu) and name it as maven_web_deploy > select freestyle project > click
on “OK”

Step 2: Configuration of maven_web_deploy project

Give the description

In the source code management select none and in environment select “delete workspace before build
starts”

In the build steps click on add build step > select copy artifacts from another project > give project name
as maven_web_test > give artifacts to copy as */

In the post build actions > click on add post build actions > select deploy war/ear to a container > enter
war/ear files as */.war> context path as webpath > give the credentials and tomcat URL

If the build is success:

Create Pipeline View for MavenWeb
Click "+" beside "All" on the dashboard and Enter name as maven_web_pipeline

Select type as build pipeline view

Give the descrip 3 on and in the upstream directly the maven_web_build will be shown

Click on apply and save

In the stage view it we be shown as:

9.Pipeline Creation using script

Step 1: In the Jenkins select the new item and give the name as pipeline_script and select pipeline and
click ok

Step 2: In the configuration, give the description

Step 3: In the pipeline section give definition as pipeline script and enter the script with git reop link and
project name

Step 4: click on apply and then save

Step 8: Check the stage view. If is successful.

10. Kubernetes Using Minikube:

Step -1:
Start Minikube : Command- minikube start

First, you need to start your Kubernetes cluster using Minikube.
When you start it, Minikube sets up a lightweight virtual machine on your system and runs a
local Kubernetes node inside it.
Step-2: Then check for the status Minikube status
Step- 3:Create an image

Step-4: Check the NGINX Service Details

APer crea 3 ng the service, check its details to see which port Kubernetes assigned to it.
Step-5 :check the detail of the kubectl.

Step-6:Check the NGINX Service Details

APer crea 3 ng the service, check its details to see which port Kubernetes assigned to it.
Step-7: Open NGINX in the Browser

Now that your service is exposed, you can open NGINX in your browser.
11. Jenkins-CI/CD
SeLng Up Jenkins CI------using GitHub Webhook with Jenkins
Step 1: Take the authen 3 ca 3 on key from the ngrok and setup in ngrok terminal

Step-2: Execute the following command using the port number on which Jenkins is running

Following output will be given:
Go to Jenkins:
Step-3: Create the Jenkins job in the source code management select the git and enter git repo url and
make sure the branch is same (i.e., main)

Step-4: In the triggers sec 3 on select “Github hook trigger for GITScm polling”

Click on apply and save

Step-6: open the git hub repo open se]ng of repo and then go to webhooks

Step-7: Click on add a webhook and take the forwarding URL from ngrok and paste in payload URL and
add /github-webhook/ along with the forwarding url
Forwarding URL: hbps://corkier-darla-handsome.ngrok-free.dev
Payload url: hbps://corkier-darla-handsome.ngrok-free.dev/github-webhook/

Step 8: make changes in the files in github

Step 9: click on commit changes

Step 10: open Jenkins the build will start automa 3 cally

You can check status : started by git hub push

SeLng Up Jenkins Email NoQficaQon Setup (Using Gmail with AppPassword)
Step-1: CreaQon of app password

Gmail: Enable App Password (for 2-Step VerificaQon)
ii. Enable 2-Step VerificaQon
iii. Generate App Password for Jenkins

Go to:
o Security → App passwords
Select:
o App : Other (Custom name)
o Name : Jenkins-Demo
Click Generate
Copy the 16-digit app password
o Save it in a secure loca 3 on (e.g., Notepad)
2. Jenkins Plugin InstallaQon
i. Open Jenkins Dashboard
ii. Navigate to:
Manage Jenkins → Manage Plugins
iii. Install Plugin:

Search for and install:
o Email Extension Plugin
3. Configure Jenkins Global Email SeLngs
Go to:
- Manage Jenkins → Configure System

A. E-mail NoQficaQon SecQon

➤ Test ConfiguraQon

Click: Test configura 3 on by sending test e-mail
Provide a valid email address to receive a test mail
✅ Should receive email from Jenkins
Field Value
SMTP Server smtp.gmail.com
Use SMTP Auth ✅ Enabled
User Name Your Gmail ID (e.g., archanareddykmit@gmail.com)
Password Paste the 16-digit App Password
Use SSL ✅ Enabled
SMTP Port 465
Reply-To
Address Your Gmail ID (same as above)
•
B. Extended E-mail NoQficaQon SecQon

Field Value
SMTP Server smtp.gmail.com
SMTP Port 465
Use SSL ✅ Enabled
CredenQals Add Gmail ID and App Password as Jenkins creden 3 als
Default Content
Type text/html or leave default
Default Recipients Leave empty or provide default emails
Triggers Select as per needs (e.g., Failure)
4. Configure Email NoQficaQons for a Jenkins Job
i. Go to:
- Jenkins → Select a Job → Configure

•
ii. In the Post-build AcQons secQon:

Click: Add post-build ac 3 on → Editable Email NoQficaQon
A. Fill in the fields:
Field Value
Project Recipient
List
Add recipient email addresses (comma-
separated)
Content Type Default (text/plain) or text/html
Triggers Select events (e.g., Failure, Success, etc.)
Aaachments (Op 3 onal) Add logs, reports, etc.
iii. Click Save

TUNEORA – A Music Web

App

1. Sequence Diagram:
A sequence diagram shows how objects interact in a particular scenario of a use case.
It focuses on the time order of messages exchanged between different components in a system.
2. Class Diagram:
A class diagram represents the static structure of a system by showing classes, their attributes, methods,
and relationships.
It is mainly used for object-oriented design and modeling data structures.

3. Component Diagram:
A component diagram illustrates how different software components are connected and interact to form a
complete system.
It helps visualize the organization and dependencies among modules or subsystems.

12.Creation of virtual machine for Ubuntu OS and Deploying the web application
DEPLOYMENT OF INDEX.HTML USING EC2 INSTANCE in AWS

Step 1: Click on Modules.

Step 2: Scroll down and select Lunch AWS Academy Lab

Step 3: click on start lab

Step 4: click on AWS and in the services select EC2

Step 5: select instances and select instance click on launch instance

Step 6: Give the name of the machine “week-122”

Step 6: Select the ubuntu server

Step 7: select architecture as 64-bit and instance type as t3.micro(i.e., they are free)

Step 8: Create a new keypair and select type as RSA and .pem op 3 on and click on create key pair

Step 9: In network se]ngs select “create security group” and give the security group name

Step 10: Click on edit bubon on the top right corner and select
Type: ssh
Source: anywhere

Step 11: in configure storage give 8GB and give number of instances as 2 and click on launch instance

Step 12: The launching of instance will start and successful message will be shown

Step 13: In the instances the created ones will be shown, you can also rename the instance , changed
week-1222 to “webapp”

Step 14: click on connect and select “SSH Client” and copy the ssh command

Step 15: Navigate to the path where the file with .pem extension is present(week-122.pem) and paste
the command

Step 16: check the docker and git version
If they are not present, then go to administra 3 ve terminal using command
“sudo su”
Then update using the command “sudo apt-get update”

Step 17: use command “sudo apt-get install docker.io” to install docker

Step 18: Clone the git repo that has maven project and change to that directory

Step 19: change to the project directory and check for Dockerfile, if not present create the Dockerfile –
“nano Dockerfile” and then build the image
“sudo docker build -t image_name .” name of image:img1

Step 20: Run the image “sudo docker run -d -p 8081:8080 img1”

Step 21: Chcek the images and the containers

Step 22: Take the public IP address from the instances in AWS and open it in chrome along with the port
number mapped.
Public IP- 13.222.21.231
Port used: 8081
Use: 13.222.21.231:8081, you will find your applica 3 on that is deployed
