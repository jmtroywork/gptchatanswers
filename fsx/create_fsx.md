# create FSX in the AWS console

Two security groups were created beforehand: FSx and launch-wizard-1

<img width="1438" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/a6e73f68-b566-4b01-b626-c106f7c17f68">

<img width="1445" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/1837adad-3b95-497a-9ebf-e36315ac696a">


Go to FSX console and press "Create File system"
<img width="1340" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/eebd2551-22cc-4e6f-90b7-8f6f5f2cc199">

Select FSx for Lustre as the file system type.

<img width="867" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/85d7fd17-1c06-4a23-bf41-2c1957902a1f">

File in the file system details as below. (note: I'm not sure if the default VPC security group is needed to be associated to the file system). Also I'm not sure if the file system needs to be in the same AZ as the EC2 instances that use it.

<img width="815" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/1144e707-719f-45b2-8723-4c45293cec3a">

<img width="821" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/f0c9192b-f90b-49f8-9edd-228c45f96743">

Do not set up the S3 data repostiory yet, we will set it up after the file system is created.

<img width="818" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/616ba9f4-5dae-473c-870b-2b36f71dae7d">

Then go to the Next page and press Create File System

<img width="355" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/445043c5-729e-4aa7-ade1-195d33d40cc0">

<img width="1372" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/4ccc7739-44c6-4eeb-a490-64ef033f3589">

It will take several minutes for the file system be become available. 

Create an S3 bucket to serve as the file system repostitory. The one I created is cw-fsx-test-jmt743 (s3 bucket names need to be globally unique)

Select the file system

<img width="1345" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/5d949c98-a8fd-41fc-a4de-7495c49b828e">

Then open the data repostitory tab and press the "Create data repository association" button

<img width="1319" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/66837986-340f-4238-aadd-83f571be3a38">

<img width="1279" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/a1eb6fdc-1906-4034-b4f0-9f28701d216c">

On the create data repository association page, choose a file path name (anything you wish), enter the S3 URI, and leave the other settings to the defaults.  Then press the "Create" button at the bottom.

<img width="822" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/b6b984ac-6cfc-423f-b8eb-d6d7c7469694">

<img width="667" alt="image" src="https://github.com/jmtroywork/gptchatanswers/assets/121819229/c1d672ad-2893-4edf-8d7a-ea36a33b1de2">

Create EC2 instances to test connection. Associate the FSx security group to the EC2
