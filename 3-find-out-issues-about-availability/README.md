So far, we have built a set of monitoring and alert services
There is no actual operation in this step, please think about the following questions:

1. What if the resource of EC2 are insufficient to meet the needs of all services?

2. What happens if a vmstorage pod crashes? What happens if an EC2 crashes?

3. If the vmcluster service crashes for 5 minutes, do we have to lose data during that time?

4. If a customer's alert rule will cause the service to crash, will the alert function of all customers be unavailable?
