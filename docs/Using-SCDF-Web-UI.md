# Using the Spring Cloud Data Flow Web UI

Note that deployment can take several minutes.  Once the application is up
and running, you can access the SCDF web UI via the `/dashboard` route.

The URL can be obtained by the Minikube CLI.  Once the server is running,
run the following command to print the URL:
```
curl -s $(minikube service --url scdf-server) | jq '._links.dashboard'
```
For example, the output may be:
```
{
  "href": "http://192.168.99.120:31198/dashboard"
}
```
Navigate to http://192.168.99.120:31198/dashboard to continue.

Some basic operations are documented in [docs/Operating-SCDF.md](./Operating-SCDF.md)
