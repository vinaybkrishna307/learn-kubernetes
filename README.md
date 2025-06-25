#apiVersion: apps/v1
#kind: Deployment
#metadata:
#  name: nginx-deployment
#  labels:
#    app: nginx
#spec:
#  replicas: 3
#  selector:
#    matchLabels:
#      app: nginx
#  template:
#    metadata:
#      labels:
#        app: nginx
#    spec:
#      containers:
#        - name: nginx
#          image: nginx:1.14.2
#          ports:
#            - containerPort: 80
#envFrom:
#  - configMapRef:
#      name: myconfigmap
#
#-----------------------------------------------------------------------------------------------------------
#
#apiVersion: v1
#kind: Service
#metadata:
#  name: my-service
#spec:
#  selector:
#    app.kubernetes.io/name: MyApp
#  ports:
#    - protocol: TCP
#      port: 80
#      targetPort: 9376
#  clusterIP: 10.0.171.239
#  type: LoadBalancer
#status:
#  loadBalancer:
#    ingress:
#      - ip: 192.0.2.127
#
#-----------------------------------------------------------------------------------------------------
#
#apiVersion: v1
#kind: ConfigMap
#metadata:
#  name: myconfigmap
#data:
#  username: k8s-admin
#  access_level: "1"
#  
#-----------------------------------------------------------------------------------------------------
#  
#apiVersion: batch/v1
#kind: Job
#metadata:
#  name: pi
#spec:
#  template:
#    spec:
#      containers:
#        - name: pi
#          image: perl:5.34.0
#          command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
#      restartPolicy: Never
#  backoffLimit: 4
#
#
##-----------------------------------------------------------------------------------------------------

# learn-kubernetes