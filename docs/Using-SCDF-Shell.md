# Using the Spring Cloud Data Flow shell

Note that deployment can take several minutes.  Once the application is up
and running, you can connect to the SCDF command line interface (CLI) via 
the Java `.jar` file

Once the server is running, run the following command to download the
`.jar` file:
```
wget https://repo.spring.io/release/org/springframework/cloud/spring-cloud-dataflow-shell/2.7.2/spring-cloud-dataflow-shell-2.7.2.jar
```
Next, connect to the SCDF CLI using the URL provided by minikube:
```
java -jar spring-cloud-dataflow-shell-2.7.2.jar --dataflow.uri=$(minikube service --url scdf-server)
```

Some basic operations are documented in [docs/Operating-SCDF.md](./Operating-SCDF.md)
