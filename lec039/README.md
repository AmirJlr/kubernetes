# Deployment Instructions

openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout tls.key \
  -out tls.crt \
  -subj "/CN=random.app.local" \
  -addext "subjectAltName = DNS:random.app.local,DNS:spacex.app.local"

kubectl create secret tls tls-secret --key=tls.key --cert=tls.crt

kubectl get secret

  tls:
  - hosts:
    - random.app.local
    - spacex.app.local
    secretName: tls-secret