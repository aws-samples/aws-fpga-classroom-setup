# AWS Educate Classrooms Quick Start Guide for Amazon EC2 F1 Instances

AWS Educate Classrooms now support Amazon EC2 F1 instances. 
Educators now no longer have to rely on students having to create their own AWS accounts for developing hardware accelerators. 

You can instead create no-cost AWS Educate classroom accounts for students to learn about the cloud in a hands-on environment. 

ℹ️ **NOTE:** AWS Classrooms are meant for instructional use only ([AWS Educate terms and conditions](https://www.awseducate.com/registrationtandc)). Faculty interested in using F1 instances for research should apply for [AWS Cloud Credits for Research](https://aws.amazon.com/government-education/research-and-technical-computing/cloud-credit-for-research/).

This guide covers how educators can request access to AWS Educate Classroom to enable students to develop custom hardware accelerators 
on field programmable gate arrays (FPGAs) as part of their coursework. Go through the following steps to get started:

### Step 1: Join AWS Educate and Apply for AWS Credits

If you have not done so already, you will need to join [AWS Educate](https://aws.amazon.com/education/awseducate/) 
and apply for AWS credits on behalf of your course.

Additionally, you will need to inform the AWS Educate and Amazon EC2 F1 instance teams of your application by emailing 
from your institution’s account with course details to f1Educator@amazon.com with the following details:

* Name and institution
* Course description
* Date by which F1 instance access is required
* Number of students
* Credits required per student

Credits cover the cost of the AWS services that students will be using, including F1 instances. 
The amount of credits required per students can be calculated by multiplying the hourly cost of F1 instances by 
the number of hours that students are expected to implement, run and debug their FPGA designs.

These steps must be performed by the course instructor.

### Step 2: Set up an AWS Educate Classroom to support F1 Instances

[AWS Educate Classrooms](https://aws.amazon.com/education/awseducate/classrooms/) let you create a no-cost virtual space for students to learn about the cloud in a hands-on environment. 
Each classroom can be tailored to allow for access to different AWS services, such as just cloud basics or building scalable websites. 

If the course requires the Xilinx Vivado Design Suite, then the course instructor will need to obtain a license on behalf of all students through the Xilinx University Program. 
The Xilinx Vitis Unified Software Platform does not require obtaining a license. 
However, downloading either Xilinx Vivado or Vitis will require creating a profile through Xilinx’s website: [http://www.xilinx.com](http://www.xilinx.com).

It is recommended to start the process of obtaining a license for Xilinx Vivado as soon as possible, and in parallel with creating the AWS Educate classroom. 
Additional information on requesting a license for Xilinx Vivado is available in the FAQ section.

Vocareum is a partner of AWS Educate and a Classrooms facilitator. Each student will need to accept Vocareum’s terms of service and sign into the AWS Educate classroom at least once. 
This will initiate the provisioning of the students' AWS Educate Classroom account that they will use for the course. 

ℹ️ **NOTE:** Accounts will only be provisioned once students sign in to the Vocareum account.

After all students have signed into the AWS Educate Classroom for the course, the course instructor will need to email a list of the students’ AWS account numbers to `f1Educator@amazon.com` in order to activate access to F1 instances.

> ℹ️ **INFO**  
> * You can find your students' AWS account numbers by logging into AWS Educate, clicking on "My Classrooms", then "Got to classroom", "Analytics", and then "Accounts".
> * Next, you can click "Export" to download all student account information. Enablement of access to F1 instances may take up to 4 business days.

### Step 3: Create the Amazon Machine Image (AMI) for the course

Since the AWS Educate Classroom accounts cannot subscribe to AWS Marketplace products, we cannot use the FPGA Developer AMI here.
The course instructor will need to create an AMI with all development tools and resources required for the course, and share it with students. 

We have provided an automated [Create your own FPGA Developer AMI solution](./src/dev_ami_build_recipes/al2/README.md) to create your own Developer AMI that you can modify for your own use-case.

ℹ️ **NOTE:** It is not mandatory to use the automated solution, it is provided to quickly set you up with an AMI recipe that works.

### Step 4: Share the AMI and Xilinx licenses with your course students

Using the list of account IDs from Step 2, follow the instructions available [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/sharingamis-explicit.html)

Licenses provided through the Xilinx University Program will also need to be shared with students. 
The node-locked licenses can be placed in a predefined location by the student. 

The automated AMI creation solution in Step 3 above sets the `XILINXD_LICENSE_FILE` environment variable to `/opt/Xilinx/license` by default. If you place your license in `/opt/Xilinx/license`, it will be picked up by Xilinx tools.

## Best Practices

### Student account cost reduction

* Students should develop their projects on `m5.2xlarge` instances and switch their instance type to `f1.2xlarge` **only** when ready to program the FPGA. 
Instructions on how to switch instance types are available [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-resize.html#resize-ebs-backed-instance).

* Stopped instances will still incur usage charges for EBS Volumes attached to the instances. 
  * To help with that, we suggest terminating build instances when done building your designs.
  * Terminating instances typically also releases the primary ENI(MAC) attached to the instance. Usually the Xilinx License will be linked to the ENI of your instance.
  * To prevent this from happening, we suggest using a secondary ENI. Create a [secondary ENI](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html) attached to your instance that you launch first.
  * Use the secondary ENI MAC Address to ask for the Xilinx license.
  * On instance termination, this ENI will stick around in your account and you can attach it to a new instance you start in the same subnet.
  * This way, your Xilinx licenses will always work even when you start a new instance.


## Resources

* AWS FPGA Developer Kit - https://github.com/aws/aws-fpga/
* AWS FPGA Developer Support Forums - https://forums.aws.amazon.com/forum.jspa?forumID=243&start=0
* Amazon EC2 F1 Instance Product Details - https://aws.amazon.com/ec2/instance-types/f1/
* FPGA Developer AMI
    * Centos 7: https://aws.amazon.com/marketplace/pp/B06VVYBLZZ
    * Amazon Linux 2: https://aws.amazon.com/marketplace/pp/B08NTMMZ7X
    
## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

