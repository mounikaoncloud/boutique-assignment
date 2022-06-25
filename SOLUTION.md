1) I have deployed all pods in my cluster , and i found adservice pod is crashing due to unable to pull the specified image in yaml file "gcr.io/google-samples/microservices-demo/adservice:v0.3.1
 ==> So i have followed the below steps
	--> edited the ad-service yaml file and changed image version to adservice:v0.3.4 and did a rollout restart deployment .
	--> now pod is running state 

2) using kubectl port-forward connected to the frontend service and i found i'm able to open the UI but not able to order.
	==> few pods are not running due to readiness  probe and liveness probe issues.
	==> i resolved the rediness and liveness probe issues changing initialdelayseconds,timeout seconds and etc (reffered few documents) and resolved those issues.
	==> now all pods are running 1/1 state

3) Pod redis-cart also failing due to nodeSelector issue
	==> i have changed kubernetes.io/hostname: **test-worker-2** to kubernetes.io/hostname=**qa-cluster-worker**
	==> and did a rollout restart , and pod got started running 1/1

4) uploaded loadgenerator-output.txt in test folder
