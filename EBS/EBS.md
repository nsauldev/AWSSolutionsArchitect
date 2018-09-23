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

### **EBS**
* SSD
* Magnetic 