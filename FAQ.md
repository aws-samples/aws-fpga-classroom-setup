## FAQ

### What is the Amazon EC2 F1 Instance?

Amazon EC2 F1 is a compute instance with field programmable gate arrays (FPGAs) that you can program to create custom hardware accelerators and explore digital logic designs. 
F1 instances, and the associated FPGA Developer AMI and Hardware Development Kit (HDK), come with everything you need to develop, simulate, debug, and compile your custom hardware. 
Once your FPGA design is complete, you can register it as an Amazon FPGA Image (AFI), and deploy it to your F1 instance in just a few clicks. 
You can reuse your AFIs as many times, and across as many F1 instances, as you like.

### What can you do with F1 Instances?

F1 instances can accelerate many High Performance Computing (HPC) applications to solve complex science, engineering, and business problems that require high bandwidth, enhanced networking, and very high compute capabilities. 
F1 instances are particularly beneficial for applications that are time sensitive such as clinical genomics, real time video processing, and financial risk analysis. 
F1 instances can also be used for exploring digital logic designs, such as CPU architectures.

### Why use F1 Instances in classes?

* As many courses are being delivered remotely, educators are running into challenges setting up computer science and system design courses, which typically require access to on-campus facilities. Access to FPGAs in AWS provides a convenient and scalable solution for students.
* Educators can use programmable hardware (FPGA) on-demand without the need for purchasing expensive hardware that may not be fully utilized.
* AWS offers students access to the latest cloud technology, and experience with it can help them secure a job upon graduating.


### Why does the use of F1 instances in AWS Classroom require educators to create an AMI?

Users of AWS Educate Classrooms cannot access AWS Marketplace, which offers the
FPGA Developer AMI developed by AWS. Educators will need to create an AMI with the
FPGA developer tools and licenses themselves in order to use F1 instances inside AWS
Educate Classrooms.

### Is AWS Educate Classrooms mandatory if educators want to use F1 instances?

Use of F1 instances within AWS Educate Classrooms is not mandatory. Educators can
still choose to use standard AWS accounts with F1 instances and the FPGA Developer
AMI available from the AWS Marketplace. AWS Organizations can be leveraged to
benefit from consolidated billing and centralized access control to AWS services and
resources. The main differences when comparing to AWS Educate Classrooms are
summarized in the table below.

| | Standard AWS Account| Classroom Account |
|------|----------------|-------------------|
| F1 Instance Availability | Several Regions | Northern Virginia Only|
| AWS Marketplace Access | Yes | No |
| Account requires Credit Card | Yes | Yes|


### How to obtain licenses for Xilinx Vivado Design Suite

1. The course instructor will need to first create an account through Xilinx’s website: [http://www.xilinx.com](http://www.xilinx.com) 
2. The course instructor will then need to join the [Xilinx University Program](https://www.xilinx.com/member/forms/registration/xup.html) 
    * Registration may take 2 business days and requires a valid email address from an academic institution. 
3. Once the Xilinx University Program account has been approved, [submit a donation request for licenses](https://www.xilinx.com/member/forms/registration/xup_donation_request.html) (in multiples of 25) on behalf of the students taking the course.
    * ℹ️ **NOTE:** This process may take up to 3 weeks but usually completes within a few days.
    * Please email: `f1Educator@amazon.com` to inform the AWS Educate and Amazon EC2 F1 instance teams when facing any delay.

### How to delete the AMI once the course is over
There is a small cost associated with storing the AMI, and it is best practice to remove it when the course is complete. 
This avoids many small charges depleting credits in your AWS Classroom accounts.

To delete the AMI, follow these instructions: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/deregister-ami.html#clean-up-ebs-ami

⚠️**Note:** Once deleted an AMI cannot be restored. You will need to rebuild the AMI using these instructions. 
