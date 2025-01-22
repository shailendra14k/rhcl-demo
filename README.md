# Deployment files for the RHCL demo 
Blog:- 

#backend-api app
Its a simple camel route, Backed app send the message with cluster name and pod details.


Backend Route:- image quay.io/shailendra14k/backend:6.1

```
  <route id="api2">
     <from id="api2" uri="undertow:http://0.0.0.0:8180/backend"/>
     <setBody id="_setBody2">
        <constant>"Backend called from Cluster:- {{env:ClusterName}} and POD hostName {{env:HOSTNAME}}"</constant>
     </setBody>
     <log id="log2" message=">>> hello backend"/>
  </route>
```

Sample Logs message received while calling the backend-api
~~~
-> curl https://api.rhcl.shailendra14k.in/backend
"Backend called from Cluster:- ARO-Azure-CentralIndia and POD hostName backend-api-56b9687bd4-8qb5j"
~~~
