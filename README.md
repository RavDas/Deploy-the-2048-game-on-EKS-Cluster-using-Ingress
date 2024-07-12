# Deploy-the-2048-game-on-EKS

## Why we use EKS over Kubeadm and Kops 

### Kubeadm

Kubeadm is a toolkit for bootstrapping a minimum viable Kubernetes cluster that conforms to best practices. It is designed to be a simple, fast way to get up and running with Kubernetes.

#### Key Features
- **Ease of Use:** Kubeadm simplifies the process of setting up a Kubernetes cluster by handling the complex parts of the installation and configuration.
- **Control Plane Setup:** It sets up the essential components of the control plane, such as the API server, scheduler, and controller manager.
- **Node Joining:** Provides straightforward commands for adding new nodes to the cluster.
- **Configuration:** Users have the flexibility to configure networking, storage, and other cluster aspects manually, providing full control over the setup.

#### Pros and Cons
- **Pros:** High flexibility, full control over the cluster, ideal for custom setups.
- **Cons:** Requires manual setup and maintenance, more suited for users with Kubernetes expertise.

### Kops

Kops (Kubernetes Operations) is an open-source project that helps you create, upgrade, and maintain production-grade, highly available Kubernetes clusters from the command line.

#### Key Features
- **Automation:** Automates many tasks involved in cluster management, including installation, scaling, and upgrades.
- **AWS Integration:** Optimized for AWS but also supports GCE and other cloud providers to some extent.
- **Cluster Management:** Provides features for managing state, rolling updates, and managing the lifecycle of clusters.
- **Configuration:** Allows for a high degree of customization through configuration files.

#### Pros and Cons
- **Pros:** Good balance of automation and customization, production-ready, easier upgrades and management.
- **Cons:** Somewhat more complex than fully managed services like EKS, primarily designed for AWS.

### EKS (Elastic Kubernetes Service)

EKS is a managed Kubernetes service provided by AWS. It takes care of the heavy lifting involved in running Kubernetes clusters, such as infrastructure management, upgrades, and scaling.

#### Key Features
- **Managed Service:** AWS handles the availability and scalability of the Kubernetes control plane.
- **Integration with AWS Services:** Seamlessly integrates with other AWS services like IAM, VPC, CloudWatch, and more.
- **Security:** Provides built-in security features such as IAM roles for service accounts and fine-grained access control.
- **Maintenance:** AWS takes care of patching, updating, and managing the control plane components.

#### Pros and Cons
- **Pros:** Reduced operational overhead, high availability and scalability, deep integration with AWS services.
- **Cons:** Less control over the underlying infrastructure, potentially higher cost, dependent on AWS ecosystem.

### Detailed Comparison

| Feature                     | Kubeadm                                | Kops                                    | EKS                                      |
|-----------------------------|----------------------------------------|-----------------------------------------|------------------------------------------|
| **Control**                 | Full control over all components       | High control with some automation       | Limited control, AWS manages control plane |
| **Ease of Use**             | Requires Kubernetes expertise          | Easier than Kubeadm, but still technical| Easiest, managed by AWS                  |
| **Automation**              | Minimal automation                     | High level of automation                | Fully automated by AWS                   |
| **Maintenance**             | Manual updates and patches             | Automated but requires some intervention| Fully managed by AWS                     |
| **Cost**                    | Lower cost, only infrastructure        | Medium cost, depends on usage           | Higher cost, managed service premium     |
| **Flexibility**             | High flexibility for custom setups     | Flexible with customizable configurations| Less flexibility, follows AWS best practices |
| **Use Case**                | Custom infrastructure setups, learning | Production-grade clusters on AWS        | Easy, reliable clusters on AWS           |

### Choosing the Right Tool

- **Kubeadm** is best if you want to learn Kubernetes deeply, need a custom setup, or are running on on-premises infrastructure.
- **Kops** is a great choice for AWS users who need a production-ready solution with some level of control and automation.
- **EKS** is ideal if you prefer a managed service, want to reduce operational complexity, and are already invested in the AWS ecosystem.


![image](https://github.com/user-attachments/assets/0f2978dd-f2e8-46b8-93f1-d79036357d29)


EKS is a highly managed controlled plane but it is not managed data plane. It will give a higly available Kubernetes cluster with regard to the control plane.

To attach worker nodes we can create EC2 instances (we have to take care of high availablitiy of instances) or can use Fargate (AWS Serverless Compute that allows to run containers)

The prerequisites for this setup include:

1. kubectl: A command-line tool for managing Kubernetes clusters. To install or update kubectl, refer to the official documentation.

2. eksctl: A command-line tool designed for working with EKS clusters, streamlining various tasks. For installation or updates, consult the provided documentation.
3. 
4. AWS CLI: A command-line interface for interacting with AWS services, including Amazon EKS. To install, update, and uninstall AWS CLI, follow the instructions in the AWS Command Line Interface User Guide. After installation, it is advisable to configure the AWS CLI using the guidelines outlined in the AWS Command Line Interface User Guide under “Quick configuration with aws configure.”
