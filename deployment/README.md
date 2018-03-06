Deployment Guides
======

Guides for making things run smoothly.

## Preface

There are three deployment environments for the backend, DEV/DEMO, QA, and PROD. Their URIs are:

- DEV/DEMO: https://demo-api.mintservices.com
- QA: http://internal-lb-hfa-us-e-1-t-int-vpc-hub-api-2080413110.us-east-1.elb.amazonaws.com
- PROD: https://api.sesac.com

The service registry (where the list of available backend applications is kept) for each environment is at:

- DEV/PROD: http://10.44.7.164:8082/registry
- QA: http://10.24.51.50:8082/registry
- PROD: http://10.40.1.225:8082/registry

Applications will be registered with a title like: `go.micro.srv.statements`. The application's name is the part without
`go.micro.srv`, e.g. `statements`. If an application presents a REST interface, using this name, it will be available at
`http://<environment hostname>/<application name>/v1`. Note that not all applications present a REST interface.

### Docs

An application's docs (if it presents a REST interface) will be located at `http://<hostname>/<appname>/<version>/docs`,
e.g. `http://internal-LB-HFA-US-E-1-T-INT-VPC-HUB-API-2080413110.us-east-1.elb.amazonaws.com/statements/v1/docs`. This
url can be put into the "Explore" bar on this site: http://petstore.swagger.io/, which will provide a nicer UI to
explore and application's HTTP capabilities.

### Logs

In production, the logs for the `sesac-api` application are sent to an ElasticSearch, Logstash, Kibana (ELK) instance at
http://10.40.3.181:5601/app/kibana#/discover?_g=(). In all other environments they are sent to stdout on the server. To
find the IP address of an application server, go to the EC2 interface on the AWS console, and search for the
application's name. The instance name will be something like `EC2-HFA-US_E_1-D-L-APP-STATEMENTS
(EC2-HFA-US_E_1-<environment>-L-APP-<application_name>).

## Guides

* [Debugging](/deployment/debugging.md)
