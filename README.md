# lab3-cloud-service-availability
In this Lab, we will deploy a complete set of monitoring and alert services, and use a series of methods to improve the availability of services

## Introduction

> What is availability?

> How to Measure Availability?

> What are the common factors that affect the availability of services, and how to solve these problems

> What are the differences in ensuring service availability between cloud and non-cloud.

## Learning Objectives

- Learn the definition and measurement of availability
- Learn how to think about service availability
- Learn some best practices about high availability

## Pre-requisites
Lab3 has the same prerequisites as lab1. it will speed up the progress of lab3 if you have completed lab1.

- An AWS account
- [`kubectl`](https://kubernetes.io/docs/tasks/tools/install-kubectl/): the standard Kubernetes command line interface
- Node.js 16. Use nvm to [install Node.js 16](https://github.com/nvm-sh/nvm#installing-and-updating):

  ```bash
  $ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
  $ nvm install 16
  ```

- Basic knowledge of AWS, Kubernetes, RDBMS
- VPN for connecting to AWS API and GitHub

## Syllabus

1. Create a new GitHub repository base on [this template](https://github.com/vldbss-2023/lab3-cloud-service-availability)
   1. Clone the newly created repository
   2. In the root directory of the repository, run `make install` to install the dependencies
2. (20 min) Create an EKS cluster [`1-create-an-eks-cluster`](./1-create-an-eks-cluster/README.md)
3. (30 min) Deploy observability service
   Operator [`2-deploy-observability-service`](./2-deploy-observability-service/README.md)
4. (20 min) Find out issues about availability[`3-find-out-issues-aboud-availability`](./3-find-out-issues-aboud-availability/README.md)
5. (50 min) Optimize observability service
   Operator [`4-optimize-observability-service`](./4-optimize-observability-service/README.md)
6. Bonus: Think about the possibility that all PODs and Disks of vmcluster will be damaged, how should we protect our services in advance?

---

## AWS billing price

This lab will incur charges under the aws account, described in detail at: 

- New EKS cluster control plane, **_1_** cluster x **_0.10_** USD per hour
- Two EKS worker EC2 `t2.medium` instances, **_2_** instances * **_0.0464_** USD per hour
- 4 EBS of size 1 GiB, with negligible cost

Total **_0.1928_** USD per hour.
