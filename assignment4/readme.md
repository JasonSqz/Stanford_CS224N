# Assignment 4

### 1. Challenge: How to train on GPU?
Assignment 4 requires training on GPU provided by Microsoft Azure. The course provided credits and quotas to GPU instances which you will not have if you are self learning the course. There are several ways to get around:

#### 1.1 Use AWS EC2 (Recommended) (Not free but affordable)

To use AWS, you will need apply for an account (credit card required) and create an EC2 GPU instance.

I assume that readers have some exposure to AWS. If not, Google. I will still provide a somewhat detailed instruction here.

-- Note: You will probably not have GPU instance limits (G/P instances) and need to submit a request to increase your limits. You can refer [here](https://aws.amazon.com/premiumsupport/knowledge-center/ec2-instance-limit/). If your request is not approved, try request for other type and provide detailed explanations on why you need the instances.

**STEP 1 Configure you EC2 instance**

Suppose you just logged in and at the Console home, search for EC2 in top search bar. After getting in, select `Launch instance`.

Search for `deep learning` at AMI and select `Deep Learning AMI GPU PyTorch 1.12.0`.

<img width="752" alt="image" src="https://user-images.githubusercontent.com/91235078/189548302-ead36516-056a-40df-908f-35f5330ed219.png">

Choose an approriate type (Check price, I used g5.xlarge at $1.006/hr).

Then create a key-pair, which will be used to log in your instance later.

<img width="761" alt="image" src="https://user-images.githubusercontent.com/91235078/189548385-33745678-9e09-4b86-ad15-d54d6f098216.png">

Leave everything else as is.

**STEP 2 Upload your files and log into your instance**

Take macOS as an example, SSH into your instance.

Use the following codes in your terminal to upload files. 

```
scp -r -i [key] [local_location] [instance_location]      
```
Replace [key] with the .pem you just created and downloaded.

Replace [local_location] as your local file path

Replace [instance_location] as ubuntu@[ip_address].compute-1.amazonaws.com:~/  

[ip_address] can be found in your instance summary under `Public IPv4 address`

If you encounter any secrutiy problem, Google.

#### 1.2 Use Azure

You can set up your Azure account and you will generally be granted $200 upon registration (Student account $100). Before you can follow the [Azure guide](https://github.com/daviddwlee84/Stanford-CS224n-NLP/blob/master/Assignments/AzureGuide.pdf) to set up your VMs, you probably will find that you have no quotas for any of the GPU instances. You will need to file a request to increase the limit. I had really bad experience on this part and AWS approved my request. So, I just went on using AWS.

#### 1.3 Train locally 

This is mostly plausible for Windows users who have good GPUs. There are many good tutorials online to set up your environments and I will not illustrate here.



