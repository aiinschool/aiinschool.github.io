---
layout: page
permalink: /awsinstructions
---

# AWS Instructions

The following is an instruction for using AWS to launch instances of DIGITS for your students.

1. Login to `console.aws.amazon.com`, enter your `username` and `password`.
2. Next to `your name` in the top-right corner, make sure you're in the `Ireland` region. If not, click on the region name and select `EU (Ireland)`. <br/>![Ireland region](/img/aws/irelandregion.png)
3. Click on `Services` at the top-left of your screen and then on `EC2`. You will be taken to the EC2 dashboard.
    <br/>![EC 2](/img/aws/2-ec2.png)
4. **If running for the first time you will need to contact Amazon to enable the use of GPU instances. It can take Amazon a few hours to respond.** 
	1. Click on `Support` on the top right corner of the page and select `Support Center`. <br/>![Go to support centre](/img/aws/supportcentre.png)
	2. Click on `Create case` <br/>![Support centre case](/img/aws/supportcentrepage.png)
	3. On the `Create case` page, enter the following details: <br/>![Creating a support case](/img/aws/supportcase.png)
		* For `Regarding*` choose `Service Limit Increase`
		* For `Limit Type*` choose `EC2 Instances`
		* For `Region*` choose `EU (Ireland)`
		* For `Primary Instance Type*` choose `p2.xlarge`
		* For `Limit*` choose `Instance Limit`
		* For `New Limit Value*` put in the number of students that will be running this exercise.
		* For `Use Case Description*` enter `Used as part of a course for introducing students to deep learning.`
		* For `Contact method*` select `Web`
		* Press the `Submit` button.
	4. You will be taken to the support ticket page and should also receive an e-mail with updates. **It may take a few hours for Amazon to respond.**
	5. To check the status of your ticket you can click on `Support` on the top right of your page and click `Support centre` the `Limit Increase: EC2 Instance` ticket will have been created. Click on it to see the correspondance.  <br/>![Support ticket](/img/aws/supportticket.png)
5. Click on `AMIs` on the left menu. <br/>![AMIs](/img/aws/3-amis.png)
6. In the search bar, select `Public images` and copy and paste `ami-d953eda0` in to the text box and press enter. <br/>![Search for AMI](/img/aws/4-amisearch.png)
7. `Right-click` on the image called `DIGITS AI in School` and select `Launch`. <br/>![Launch images](/img/aws/5-launchimg.png)
8. Select the `GPU Compute p2.xlarge` <br/>![Select p2.xlarge](/img/aws/6-p2xlarge.png)
9. Select `Next: Configure Instance Details`. You'll be taken to the `Configure Instance` page. <br/>![Config instance detail](/img/aws/7-configinstancedetail.png)
10. In the `Number of instances` box, enter the number equal to the `number of students` in the class. <br/>![EC 2](/img/aws/8-numinstances.png)
11. Click on the `Configure Security Group` tab. <br/>![Config security group](/img/aws/9-configsecuritygroup.png)
12. Select `Create a new security group`.  <br/>![Create new security group](/img/aws/10-createnewsecuritygroup.png)
13. Press `Add Rule`.  <br/>![Add rule](/img/aws/11-addrule.png)
14. In the `Port range` column type in `5000`, and in the `Source` column select `Anywhere`.  <br/>![Set port ranges](/img/aws/12-portrangeandsource.png)
15. Press `Review and Launch`.  <br/>![Review and launch](/img/aws/13-reviewandlaunch.png)
16. Then press `Launch` to start your instances.  <br/>![Launch](/img/aws/14-launch.png)
17. You will be taken to a key pair screen. In the combo box select `Proceed without a key pair` and tick the acknowledgement box below.  <br/>![Add new keypair](/img/aws/15-keypair.png)
18. Click on `Services` at the top-left of your screen and then on `EC2` to go back to the main Dashboard. <br/>![EC 2](/img/aws/2-ec2.png)
19. Click on `Instances` on the left-hand menu to go to the `Instances page`. You'll notice a number of launched instances.  <br/>![Instance page](/img/aws/17-instancepage.png)
20. After the `Instance State` lights have gone green and status shows `Running`, under the `IPv4 Public IP` column, you will see the IP number, in this case it is `52.16.2.0` (You may need to scroll right if your browser window is too small).  <br/>![Instance running](/img/aws/18-instancerunning.png)
21. If the IP is `52.16.2.0`, the address to provide your student is `http://52.16.2.0:5000`, **it is important to add the `:5000` to the end of the address**. Assign a different instance for each one of your students.
