SECRET_NAME=$(echo $DOMAIN | sed 's/\./-/g')-tls; echo $SECRET_NAME

kubectl create secret tls $SECRET_NAME --cert=tls_self.crt --key=tls_self.key
