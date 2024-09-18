# hello-world-k8s

This is a simple Hello World application deployed to Kubernetes on AWS (EKS)

The App is accessible on https://k8s.daniel-test.com/

CI/CD pipeline is set up so that any PR that is merged to main gets deployed immediately.

How it works (on a PR merge):
* Builds docker image with latest code and pushes it to dockerhub
* It applies the k8s resources (pod/svc)
* Pod pulls latest image and starts runnning

To improve:
* Right now all k8s resources are a pod and a service load balancer. Ideally, for a scalable system we'd want a deployment and a replicaset.
* All AWS infra was created via console, to scale we'd want IAC (terraform, pulumi, etc)
* Many permissions could be more restrictive (AWS resources, PR merges, etc)