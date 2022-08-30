![image](https://user-images.githubusercontent.com/101533381/187448628-441cb804-1fc2-4536-9561-6baeccdedd00.png)

# Authentication on Google Cloud

## 13 core security controls:
https://www.bilibili.com/video/BV1og411A79Y?spm_id_from=333.337.search-card.all.click

### Note: 
The order of the list is important to ensure a good foundation before deploying the application. 
But we can use this list to design and build a GCP working environment. 
We can also use this list to evaluate and harden your current GCP environment.

### 1) Establish unified identity management with on-premises
### 2) Create a minimal role with IAM
### 3) Policy for establishing Orgainization (no external IP, domain restricted sharing, trusted images)
### 4) Use Shared VPC Project for network connectivity and isolation control.
### 5) Build high-availability and disaster-tolerant network topologies using multi-AZ/multi-region subnets
### 6) On-premises interconnect using VPN or InterConnect
### 7) Defend against DDos and external network attacks through Gloabal Load Balancer, Cloud Armor and VPC firewall
### 8) Collect logs centrally with Log Sink
### 9) Monitor your environment with Cloud Native tools,
### 10) Create a service project that hosts the workload
### 11) Establish Security Boundaries with VPC-Service Control
### 12) Secure access to GCP Service and Internet via private IP
### 13) Deploy secure built-in workloads that integrate key management and DLP, and leverage multi-region services for data storage.

![image](https://user-images.githubusercontent.com/101533381/187407676-09046b7d-367c-4ff9-9c3f-3603af4d6121.png)


## 1) Cloud Identity
Establish unified identity synchronization management on and off the cloud,
E.g. Active Directory is used under the cloud, and all identities are stored in Active Directory, and a series of workflows about identities are established in Active Directory, such as: new recruits, transfer workers and leavers. 
GCP can also have the same identity management workflow with on-cloud and off-cloud synchronization.

## 2) Cloud IAM
Create roles with least privileges.
Assign roles through Role based access control.
Instead of assigning directly to individuals, role assignments can be managed using IAM groups.
At the same time, it is necessary to design and deploy the resource organization structure on the GCP cloud, such as: how many folders are there, which folder represents what, and how many layers are there in the entire folder structure.

## 3) Organization Policies
On each node of the resource organization structure, such as: folders, projects, and even Organization Root. Common Organization Policies limit the external IP address of the GCE Virtual Machine and limit the sharing of different domain names. For example, the company currently uses stykka.com, which can restrict non-@stykka.com roles and cannot access certain resources. Implement to prevent data exposure.

## 4) Shared VPC Project
Through Shared VPC to achieve network connection and isolation control. Through the Shared VPC Project, manage all VPCs to achieve centralized management, isolation, and simplified network management.

## 5) HA/DR Network Design
Different regions and regions can be used to create a highly available and disaster recovery-ready network architecture on GCP. It is also possible to use a globalization feature that comes with VPC, unlike other public clouds, and does not require conversion between different regions.

## 6) Hybrid Connectivity
Customers who need hybrid links can create Cloud Interconnects, or use IPSec VPNs to create links on and off the cloud, or even link to other clouds.

## 7) Internet Facing App Defence
For some applications facing the external network, Gloabal Load Balancer, Cloud Armor and VPC firewall can be used to achieve DDos Attack defense. It is possible to further use Apigee and Recaptcha to implement authentication credentials, such protections from theft, and to protect APIs.

## 8) Centralized Logging
Collect all logs across the organization and consolidate them in one place. Also consider collecting VPC flow and firewall logs on some sensitive workloads and sensitive apps. Note: The traffic of these two logs will be very large, so be sure to enable log aggregation.

## 9) Cloud Native Monitoring
Process logs to gain insight. Take advantage of high-performance computing and low-cost storage on the cloud, and use some cloud-native tools such as: GCP Monitoring, Security Command Center, and BigQuery.

## 10) Workload Service Projects
With the network infrastructure in place, with the VPC, etc., you can start creating the Service Project and put the application in it. Note: Put the Service Project on the correct node, based on the GCP resource organization structure created in the second step. The Shared VPC Project created in the fourth step can also be used.

## 11) VPC Service Control (VPC SC)
This is a unique feature of GCP and can be thought of as an API-level firewall. You can draw a boundary, put Google Projects and the Services in Projects in this boundary, and then define what kind of traffic can come in, what kind of traffic can go out, and even define each API based on what context method.

## 12) Private Google Access
For resources placed in VPC, such as: GKE, GCE, etc., you can use Private Google Access, or Cloud NAT to help us access other Google resources or the internet. These routes can ensure that all our traffic is stored in Google's network backbone instead of using the public internet, which allows us to better use Google's high-performance network instead of the unreliable internet.

## 13) Deploy Secure Workload
Finally, cloud-native GCP security services such as Cloud DLP and Key Management Services can be used to protect applications on GCE or GKE, as well as data stored in BigQuery and Cloud Storage. In the process of data protection, it is necessary to use the form of multiple regions to ensure the high availability of data.
