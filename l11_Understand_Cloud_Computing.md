# Understand Cloud Computing

## What is cloud computing?
Definition
- Cloud Computing is the delivery of technology services. Including compute, storage, databases, networking, software, and many more. Over the internet as pay-as-you-go pricing.

Cloud Service Provider
- Amazon AWS
- Microsoft Azure
- Google Cloud Platform

### Hosting a website using a on premise server
- Server
  - Powerful computer
  - you can connect to remotely
- Located on the premises
- To handle the traffic without slowing down website
  - Buy/Rent new servers
    - Take time to set up
    - Cost a lot of money

### Hosting a website using a on cloud server
- Cloud server
- Access to computing power instantly when you need it
- To scale up can access more computing power in the cloud as you need
- Easily release redundant cloud servers
- Pay-as-you-go billing

## The power of the cloud
### 3 Main services on cloud
  1. Compute: provide the brains to process your workload.
  2. Storage: save and store data.
  3. Databases: store more structured sets of data.

### Cloud computing characteristics
- Virtualization: Fundamental technology that powers cloud computing.
  - Physical servers -> Multiple virtual servers.
  - Maximizes the output of individual servers.
  - Economies of scale.
- Scalability: Easily add or remove resources as you need them.
  - Example: e-commerce site.
  - Needs more resources during peak time.
  - Scale resource as necessary.
  - There are 2 type of scale 
    1. Vertical scaling: Increase the power of the instance.
    2. Horizontal scaling: Add more instances.
- Cost: Pay-as-you-go / Only pay for resources when you are using them.
- Speed: Immediately access to ready-to-go cloud resources.
  - On-demand resourcing.
  - Fast set-up.
  - Deploy services in a matter of minutes.
- Performance: Access to fast and efficient computing recources.
  - Data center: houses an orginization's IT operations and equipment.
  - World wide network of data center.
- Growth: Grow using a wide range of resources and services.
- Reliability: Guarantee durability and availability of data and services.
- Security: Sucure storage and management of your data.

### Cloud service models
If cloud service is car service
![Image](https://drive.google.com/uc?id=1_p2qnq_DHX4ONLO8vNbK16XQQGQkkN86)

![Image](https://drive.google.com/uc?id=1CZCyiGyJO2q-H7cFGoR84fTvefSQCscc)

![Image](https://drive.google.com/uc?id=16ZudUzdlgAVFwndS9kQxO9-SXts3Wi5i)

*Other service models*
- FaaS (Function as a Service)
  - Variation on SaaS.
  - Focuses on a function (part of the software).
  - e.g., identity authentication, payment transactions.
  - Uses a "serverless" billing model.

- Hardware as a Service (HaaS)
- Storage as a Service (SaaS)
- Database as a Service (DBaaS)
- Disaster Recovery as a Service (DRaaS)
- Network as a Service (NaaS)

## Cloud deployment models
- Important decision in cloud adoption.
- How much control do you need over your cloud development?
- 3 main types: private, public, and hybrid.

### Private cloud
Cloud infrastructure is designed for exclusive use by its tenants.

Private cloud are accessed by a network link (set up by IT)

Pros: Direct control of resources and data.
Cons: More upfron investment.

Unlike on-premise, private cloud uses virtualization for on-demand compute resources and can be off-premises.

### Public cloud
Cloud infrastructure is shared and open for use by the general public. it's owned and managed by a cloud service provider. Public clouds are internet access.

Pros: Get started quickly with minimal investment and Easier to scale.
Cons: No access to data center and hardware.

### Hybrid cloud
Combination of two or more distinct models.

Use cases: 
  - Store sensitive data on the private cloud and use application on public cloud for analytics.
  - Cloud bursting:: when private cloud hits capacity, temporarily move overflow to the public clod to avoid disruption of service.

### Other deployment models.
- Multi cloud
  - Combination of different cloud provider services. 
  - Flexibility on pricing plans and service offering. 
  - No reliance on one vender.
- Community model
  - Infrastructure shared by a specific cumminity for exclusive use. 
  - Common interest or concern, e.g., security, jurisdiction, mission. 
  - Can be managed and hosted internally or externally.

## Regulations on the cloud
### Genral Data Protection Regulation (GDPR)
- Regulates how personal data is collected, processed, and stored from users in the EU.
- Examples:
  - Users must explicitly consent to data collection. 
  - Notify users of any data breaches. 
  - Personal data information must be encrypted, anonymized, and/or pseudonymized.
  - Personal data can't leave EU borders, unless you can guarantee the same level of protection.

### Personal Data
Any information that relates to an identified or identifiable living individual.
  - home address 
  - first name 
  - last name 
  - email 
  - location data 
  - IP address 
  - racial or ethnic origin 
  - Political opinions 
  - Sexual orientation 
  - Health related data
- Personally Identifiable Information (PII)

## Cloud Providers and Case studies
## Amazon Web Services (AWS)
### Personal cloud
- Amazon drive
- Amazon photos

### Professional cloud
- File storage: AWS S3
- Computation: AWS EC2
- Databases: AWS RDS

### Amazon data services
- Redshift (analytics - data warehousing)
- Kinesis (real time data movement and analytics)
- SageMaker (predictive analytics and machine learning)

### AWS case study
Company: NerdWallet
Problem: Takes too long to deploy machine learning models.
Solution: Amazon SageMaker (cloud machine learning platform gathering machine learning processes.)
Improvement: 
  - Reduce training times to days. 
  - Reduce training costs by 75%.
  - Modenized data science engineering practices.

## Microsoft Azure
### Personal cloud
- OneDrive

### Professional cloud
- File storage: Azure Blob Storage
- Computation: Azure Virtual Machine
- Databases: Azure SQL Database

### Azure's data services
- Data Lake Storage (store data before cleaning) 
- Stream Analytics (real-time analytics) 
- Machine Learning (train and deploy machine learning models)

### Azure case study
Organization: Ottawa Hospital
Needs: Cost effective and secure disaster recovery solution (continue vital operations after a disater)
Solution: 
  - Microsoft IaaS (secure, scalable environment) 
  - Azure Storage (medical imaging data) 
  - Azure Site Recovery (automatically deploy recovery processes)
Improvement:
  - New secure, up-to-date, policy compliant disaster recovery site in under 3 months. 
  - Compliant with data privacy regulations. 
  - Saved ~50% on disaster recovery costs.