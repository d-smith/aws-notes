## Fun with failover

1. Use the vpc notebook to instantiate two vpcs (in different regions) and private instances fronted
by load balancers. 
2. Create domain name health checks for the two load balancers using the
DNS names for the load balancers on their index.html page.
3. In a hosted zone, create aliases for the two load balancers. The aliases
are needed because when we create a failover policy the health check
targets need to  be different than the alias targets assocaited with the 
primary and secondary endpoints in the failover policy.
4. Create two failover records sets, one primary, one secondary. Use the 
alias names as the targets, and reference the assocaited health checks.

When set up, you can nslookup the alias assocaited with the failover policy,
which will match the alias associated with load balancer. Then, go to the 
primary region and terminate the instance. The health check will go 
unhealthy after the threshold is exceeded, and the nslookup with then
reflect the secondary region/alias.

Go back to the work book, launch a new instance in the primary region, and 
associated with the target group. The unhealthy health check will become
heathly again after a couple minutes, and the nslookup will then return the 
original values.
