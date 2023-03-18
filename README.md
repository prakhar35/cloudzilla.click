# cloudzilla.click
Hosting this static website on S3 bucket using Route 53 as a DNS and Cloudfront and SSL certification to perform https.

1. Creating a Domain name using Route 53
![image](https://user-images.githubusercontent.com/70505201/226093505-5b281467-0d85-42cf-a29e-2d38b25ed51c.png)


2. Create an S3 bucket with same name as our domain name, and give it public access with a public policy
![image](https://user-images.githubusercontent.com/70505201/226092447-6a10fe2c-f25c-4190-9092-066ef3aaae59.png)

policy for S3:
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Statement1",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::cloudzilla.click/*"
        }
    ]
}


3. created a record in Route 53, 
![image](https://user-images.githubusercontent.com/70505201/226092244-ef9fdccd-c9e6-4dad-af72-a5a35e4fd4b9.png)

alias as s3, to access the web site from browser
![image](https://user-images.githubusercontent.com/70505201/226092677-25a52097-bc83-498b-8243-9d7705ce7a09.png)

accessing the website:
![image](https://user-images.githubusercontent.com/70505201/226092709-c0d7063a-7e81-49e1-877f-101910b8beb9.png)

4. To secure the website, we will use cloudfront and SSL certificate
![image](https://user-images.githubusercontent.com/70505201/226092733-de7387e3-4e5e-40c5-b6cb-703b11dbfe87.png)

remember giving your index.html as default landing page while creating distribution

give the domain name as CNAME to generate the SSL and then create cloudfront distribution.

5. edit the previous record in Route 53 having S3 as an alias, make it alias as cloudfront.
![image](https://user-images.githubusercontent.com/70505201/226092870-3348eaa0-d328-4a5a-b3ad-d33fd7dd6e5d.png)

6: run  the website securely, cheers!
![image](https://user-images.githubusercontent.com/70505201/226093417-448534ae-f5d3-4d2f-a109-3b6a1a66a2db.png)
