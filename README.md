# Deploy Static Website on AWS

This project demonstrates how to deploy a static website to Amazon Web Services (AWS) using S3, CloudFront, and IAM. The website includes HTML, CSS, images, and JavaScript files, and leverages AWS services for secure, scalable, and fast delivery of content.

## Project Overview

The goal of this project is to host a static website on AWS using the following services:

- **Amazon S3**: Used for storing the static files (HTML, CSS, JS, and images) and configuring the bucket to serve the content as a static website.
- **AWS CloudFront**: Used as a Content Delivery Network (CDN) to distribute the website content globally with low latency and high transfer speeds.
- **AWS IAM**: Used to manage permissions and ensure that the S3 bucket is securely accessible only to the appropriate users and services.

## Files Included

- **index.html**: The main HTML file that serves as the homepage for the website.
- **/img**: Contains the background image used in the website.
- **/vendor**: Contains the Bootstrap CSS framework, fonts, and JavaScript libraries required for the website to function correctly.
- **/css**: Contains the custom CSS files used for styling the website.

## Steps to Deploy the Website

### 1. Create an S3 Bucket

1.1 Log in to the AWS Management Console and navigate to the S3 service.

1.2 Create a new S3 bucket with a unique name (e.g., `my-static-website-bucket`).

1.3 Upload all project files (`index.html`, `/img`, `/vendor`, `/css`) to the S3 bucket.

1.4 Configure the bucket for static website hosting by setting the `index.html` as the index document.

1.5 Set up the appropriate bucket policy to make the website files publicly accessible.

### 2. Set Up CloudFront Distribution

2.1 Go to the CloudFront service in the AWS Management Console.

2.2 Create a new CloudFront distribution and set the S3 bucket as the origin.

2.3 Configure the distribution to use HTTPS by associating it with an SSL certificate (you can obtain one through AWS Certificate Manager).

2.4 Optionally, set up a custom domain and configure Route 53 to route traffic to the CloudFront distribution.

### 3. Configure IAM Policies

3.1 Create an IAM policy that grants the necessary permissions to access the S3 bucket and manage CloudFront distributions.

3.2 Attach the policy to an IAM user or role that will manage the deployment.

### 4. Access the Website

4.1 Once the CloudFront distribution is deployed, you can access the website via the CloudFront domain name.

4.2 The website should be globally accessible with fast load times due to CloudFront's CDN capabilities.

---

## GitHub Workflow for Continuous Deployment (CD)

This project includes a GitHub Actions workflow file that automates the deployment process to AWS. The workflow triggers upon pushes to the `main` branch, synchronizing the static website files to the S3 bucket and invalidating the CloudFront cache to ensure that the latest content is served globally.

To use the workflow, ensure that you configure the required secrets (AWS credentials, S3 bucket name, and CloudFront distribution ID) in your GitHub repository.

The workflow file can be found in the following path within the project:

```
.github/workflows/aws-cd.yml
```

Make sure the required AWS secrets are configured in the repository settings for proper deployment.

---

## Repository Contents

- **index.html**: The main HTML file.
- **/img**: Background image for the website.
- **/vendor**: Contains Bootstrap, Font Awesome, and jQuery files.
- **/css**: Custom CSS files for styling the website.
- **README.md**: Documentation for the project.
- **.github/workflows/aws-cd.yml**: GitHub Actions workflow file for automating deployment.

## Accessing the Website

Once deployed, the website can be accessed via the CloudFront domain name provided by AWS. If a custom domain is used, ensure that DNS records are correctly set up to point to the CloudFront distribution.

## Preview

<img width="1440" alt="Screenshot 2024-09-07 at 8 59 38 PM" src="https://github.com/user-attachments/assets/6c7afd44-b6c8-451f-bcde-a0d56fea5412">
<img width="1190" alt="Screenshot 2024-09-07 at 9 36 58 PM" src="https://github.com/user-attachments/assets/ce7f8536-266b-40b2-93c3-a4ec36fd9433">
<img width="1175" alt="Screenshot 2024-09-07 at 9 38 37 PM" src="https://github.com/user-attachments/assets/d9706933-cc07-49f4-8fec-277634821cba">


## Conclusion

This project demonstrates how to efficiently deploy and distribute a static website using AWS services. By leveraging S3 for storage, CloudFront for global content distribution, and IAM for secure access management, the website is both scalable and secure.
