# Certified Solutions Architect Study Notes


## ![EC2](/images/EC2.png) EC2 - Elastic Compute Cloud

EC2 101

* Elastic Compute Cloud = EC2
* Provides resizable compute capacity
* Can scale up/down/out

EC2 has changed the economics of computing

* In the past we used ot buy a server and grow into it
* Now we can pay for the capacity we use

#### EC2 Instances & Pricing:

* **On-Demand Instance**

  * Fixed rate by hour with no commitment
  * Perfect for low-cost/flexibility
  * Short term or unpredicatable workloads
  * Good for apps being developed or tested for the first time

* **Reserved Instances**

  * 1-3 years in length
  * Offer significant discount
  * Apps should be steady or predictable
  * Users make up-front payments

    * Standard reserved instance 75% off On-Demand instance
    * Converitble 54% off On-Demand instance

      * Can change attributes of reserved instance if it creates reserved instances of equal or lesser value

  * Scheduled Reserve Rnstance
    * available in thetime you reserve
      * example = Your company has a routine sale at the end of the month

* **Spot Instances**

  * Bid whatever price you want
  * Like stock market
  * Flexible start & end times
  * Only feasible at low compute time
    * example = compute time at 4 a.m.

* **Dedicated Host**

  * Physical EC2 server dedicated for use
  * Useful for regulatory requirements if not allowing multi-tenancy
  * Can be purchased On-Demand (hourly)
  * Can be reserved 70% off On-Demand price

  #### Instance Types

  Family | Specialty | Use Case
  --- | --- | ---
  F1 | Field Programmable | Genome research, Financial Analysis, Big Data
  I3 | High Speed Storage | Data Warehousing
  G3 | Graphics Intesive | Video
  H1 | High Disk Throughput | Hadoop like installations
  T2 | Lowest Cost, General Purpose | Web servers/Small Databases
  D2 | Dense Storage | Fileservers, Data warehousing
  R4 | Memory Optimized | Memory Intensive Apps
  M5 | General Purpose | App Servers
  C5 | Compute Optimized | CPU Intensive Apps
  P3 | Graphics/General Purpose GPU | Machine Learning
  X1 | Memory Optimized | SAP Hana

  Instance type pnumonic = FIGHTDRMCPX = Fight Doctor McPix

  **F** - FPGA

  **I** - IOPS

  **G** - Graphics

  **H** - High Disk Throughput

  **T** - Cheap General Purpose

  **D** - Dense Storage

  **R** - RAM - Memory Optimized

  **M** - Main Choice General Purpose

  **C** - Compute

  **P** - Graphics

  **X** - Extreme Memory

#### Security Groups
* Virutal Firewall
* 1 instance can be a part of multiple security groups

#### AMI Types
* EBS or Instance Store
  * Select:
    * Region
    * OS
    * Architecture (32 bit or 64 bit)
    * Launch Permissions
    * Instance Store (Ephemeral Storage)
    * EBS Backed

* Instance Store
  * Cannot stop the instance
  * Root device defined by AMI
* EBS Volumes
  * Root device for instance is EBS

#### Elastic Load Balancers
* Virutal Appliance
  * Balance load of traffic

* **Types**
  * Application Load Balancer (ALB)
  * Network Load Balancer (NLB)
  * Classic Load Balancer (CLB)

* Application Load Balancer
  * Best suited for HTTP & HTTPS
  * OSI Layer 7 application-ware
  * Intelligent routing decisions

* Network Load Balancer
  * Best for TCP/Exterme Performance
  * Layer 4 connection
  * Can handle millions of requests per second

* Classic Load Balancer
  * Legacy Elastic Load Balancer
  * Layer 7 specific functions
    * X-Forward
    * Sticky Sessions
  * Layer 4 load balancer

If you get a 504 error:
  * Applicaiton is having issues
  * Web Server or Database are having issues
  * Determine where it is failing

X-Forward-For-Header
  * Take IP (Public IP) > Classic Load Balancer (Private IP) > EC2 (Public IP) {X-Forwarded-For-Header}



## **EBS - Elastic Block Storage**

* Create storage volumes
* Virtual Disks
* Create a file system on top
* Placed in specific availability zone

### Types

#### **SSD**

* General Purpose (GP2)
  * 3 IOPS per GB up to 10,000 IOPS

* Provisioned IOPS SSD (IO1)
  * I/O intensive (like big NoSQL database)
  * Can provision more than 20,000 IOPS

* Throughput Optimized HDD (STI)
  * Big data
  * Cannot be boot volume

* Cold HDD (SC1)
  * Lowest cost (like file server)
  * Not boot

* Magnetic
  * Lowest cost that can boot
  * access infrequently


## **Exam Tips**

### **EC2**
* Remember pricing models
* Spot instances
  * If terminated by Amazon, you will not be charged
  * If terminated by you, charged full hour
* Remember types of instances - FIGHTDRMCPX
* Instance store = Ephemeral storage
* Instance store volumes cannot be stopped. If host failes the data is lost.
* EBS volumes can be stopped
* Both can be rebooted with no data loss
* By default, root volume is deleted on instance termination
  * EBS volumes can be kept if needed

#### Elastic Load Balancer
* 3 types of LBs
* If you see Elastic Load Balancer = Classic Load Balancer
* 504 error means gateway timed out
* IPv4 end user, look for the X-Forwarded-For-Header

### **EBS**
* SSD
* Magnetic 