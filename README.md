# ELK
kubectl exec -it $(kubectl get pods -n es | grep elasticsearch-client | sed -n 1p | awk '{print $1}') -n es -- bin/elasticsearch-setup-passwords auto -b


kubectl create secret generic elasticsearch-pw-elastic -n kibana --from-literal password=<elasticsearch Password>


NameSpaces:

1. Create Namespace.

elastic search:

1. master elastic config, service and deployment.
2. data elastic config, service and deployment.
3. client elastic config, service and deployment.

Outside access ingress deployment.

Kibana:

1. kibana config, service and deployment.

Outside access ingress deployment.



Create a public Kubernetes HTTPS Application:

1. export DOMAIN=$(minikube ip).nip.io
2. openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout tls_self.key -out tls_self.crt -subj "/CN=*.${DOMAIN}" -days 365

Create Kubernetes Secret

1. SECRET_NAME=$(echo $DOMAIN | sed 's/\./-/g')-tls; echo $SECRET_NAME
2. kubectl create secret tls $SECRET_NAME --cert=tls_self.crt --key=tls_self.key