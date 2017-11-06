---
layout: page
permalink: /awsinstructions
---

# AWS Instructions

The following is an instruction for using AWS to launch instances of DIGITS for your students.

1. Login to `console.aws.amazon.com`, enter your `username` and `password`.
2. Click on `your name` in the top right and then on `My account`. Send your `Account Id` number to [t.karmakharm@sheffield.ac.uk](mailto:t.karmakharm@sheffield.ac.uk) to be added to the list of users the class image is made available to.
2. Next to `your name` in the top-right corner, make sure you're in the `Ireland` region. If not, click on the region name and select `EU (Ireland)`. <br/>![Ireland region](/img/aws/irelandregion.png)
2. Click on `Services` at the top-left of your screen and then on `EC2`. You will be taken to the EC2 dashboard.
    <br/>![EC 2](/img/aws/2-ec2.png)
3. Click on `AMIs` on the left menu. <br/>![AMIs](/img/aws/3-amis.png)
4. In the search bar, select `Public images` and type in `ami-0bed4f72`. <br/>![Search for AMI](/img/aws/4-amisearch.png)
5. `Right-click` on the image called `DIGITS AI in School` and select `Launch`. <br/>![Launch images](/img/aws/5-launchimg.png)
6. Select the `GPU Compute p2.xlarge` <br/>![Select p2.xlarge](/img/aws/6-p2xlarge.png)
7. Select `Next: Configure Instance Details`. You'll be taken to the `Configure Instance` page. <br/>![Config instance detail](/img/aws/7-configinstancedetail.png)
8. In the `Number of instances` box, enter the number equal to the `number of students` in the class. <br/>![EC 2](/img/aws/8-numinstances.png)
9. Click on the `Configure Security Group` tab. <br/>![Config security group](/img/aws/9-configsecuritygroup.png)
10. Select `Create a new security group`.  <br/>![Create new security group](/img/aws/10-createnewsecuritygroup.png)
11. Press `Add Rule`.  <br/>![Add rule](/img/aws/11-addrule.png)
12. In the `Port range` column type in `5000`, and in the `Source` column select `Anywhere`.  <br/>![Set port ranges](/img/aws/12-portrangeandsource.png)
13. Press `Review and Launch`.  <br/>![Review and launch](/img/aws/13-reviewandlaunch.png)
14. Then press `Launch` to start your instances.  <br/>![Launch](/img/aws/14-launch.png)
15. If this is the first time you've used this service you will be forced to create a keypair. Type in any `Key pair name` you like. Press `Download Key Pair` then press `Launch Instances`  <br/>![Add new keypair](/img/aws/15-keypair.png)
16. Click on `Services` at the top-left of your screen and then on `EC2` to go back to the main Dashboard. <br/>![EC 2](/img/aws/2-ec2.png)
17. Click on `Instances` on the left-hand menu to go to the `Instances page`. You'll notice a number of launched instances.  <br/>![Instance page](/img/aws/17-instancepage.png)
18. After the `Instance State` lights have gone green and status shows `Running`, under the `IPv4 Public IP` column, you will see the IP number, in this case it is `52.16.2.0` (You may need to scroll right if your browser window is too small).  <br/>![Instance running](/img/aws/18-instancerunning.png)
19. If the IP is `52.16.2.0`, the address to provide your student is `http://52.16.2.0:5000`. Assign a different instance for each one of your students.
