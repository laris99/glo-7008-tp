$ kind create cluster --config cluster.yaml

$ docker build -t logicapi ./logic-api/
$ docker build -t feedbackapi ./feedback-api/

$ docker login

$ docker tag logicapi labdev11/logicapi:v1
$ docker tag feedbackapi labdev11/feedbackapi:v1

$ docker push labdev11/logicapi:v1
$ docker push labdev11/feedbackapi:v1

$ kubectl create deployment logicapi-dp --image=labdev11/logicapi:v1 --replicas=2
$ kubectl create deployment feedbackapi-dp --image=labdev11/feedbackapi:v1 --replicas=2

$ kubectl scale deployment logicapi-dp --replicas=2
$ kubectl scale deployment feedbackapi-dp --replicas=2

$ kubectl get deployment logicapi-dp
$ kubectl get deployment feedbackapi-dp
$ kubectl get pods

$ kubectl get deployment logicapi-dp -o yaml > ./submission/logicapi-dp.yaml
$ kubectl get deployment feedbackapi-dp -o yaml > ./submission/feedbackapi-dp.yaml

$ kubectl delete deployment logicapi-dp