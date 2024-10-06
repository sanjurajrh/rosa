[student@workstation ~]$ sudo openvpn --config vpn-configuration.ovpn 
Sun Oct  6 06:53:42 2024 OpenVPN 2.4.12 x86_64-redhat-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Nov 10 2023
Sun Oct  6 06:53:42 2024 library versions: OpenSSL 1.1.1k  FIPS 25 Mar 2021, LZO 2.08
Sun Oct  6 06:53:48 2024 TCP/UDP: Preserving recently used remote address: [AF_INET]3.104.174.93:443
Sun Oct  6 06:53:48 2024 Socket Buffers: R=[212992->212992] S=[212992->212992]
Sun Oct  6 06:53:48 2024 UDP link local: (not bound)
Sun Oct  6 06:53:48 2024 UDP link remote: [AF_INET]3.104.174.93:443
Sun Oct  6 06:53:48 2024 TLS: Initial packet from [AF_INET]3.104.174.93:443, sid=78b5de69 4614ebdb
Sun Oct  6 06:53:48 2024 VERIFY OK: depth=1, CN=Red Hat Training
Sun Oct  6 06:53:48 2024 VERIFY KU OK
Sun Oct  6 06:53:48 2024 Validating certificate extended key usage
Sun Oct  6 06:53:48 2024 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Sun Oct  6 06:53:48 2024 VERIFY EKU OK
Sun Oct  6 06:53:48 2024 VERIFY X509NAME OK: CN=server
Sun Oct  6 06:53:48 2024 VERIFY OK: depth=0, CN=server
Sun Oct  6 06:53:48 2024 Control Channel: TLSv1.2, cipher TLSv1.2 ECDHE-RSA-AES256-GCM-SHA384, 2048 bit RSA
Sun Oct  6 06:53:48 2024 [server] Peer Connection Initiated with [AF_INET]3.104.174.93:443
Sun Oct  6 06:53:49 2024 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Sun Oct  6 06:53:50 2024 PUSH: Received control message: 'PUSH_REPLY,dhcp-option DNS 10.2.0.2,route 10.2.0.0 255.255.0.0,route 10.1.0.0 255.255.0.0,route-gateway 172.16.0.129,topology subnet,ping 1,ping-restart 20,echo,echo,echo,ifconfig 172.16.0.130 255.255.255.224,peer-id 0,cipher AES-256-GCM'
Sun Oct  6 06:53:50 2024 OPTIONS IMPORT: timers and/or timeouts modified
Sun Oct  6 06:53:50 2024 OPTIONS IMPORT: --ifconfig/up options modified
Sun Oct  6 06:53:50 2024 OPTIONS IMPORT: route options modified
Sun Oct  6 06:53:50 2024 OPTIONS IMPORT: route-related options modified
Sun Oct  6 06:53:50 2024 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Sun Oct  6 06:53:50 2024 OPTIONS IMPORT: peer-id set
Sun Oct  6 06:53:50 2024 OPTIONS IMPORT: adjusting link_mtu to 1624
Sun Oct  6 06:53:50 2024 OPTIONS IMPORT: data channel crypto options modified
Sun Oct  6 06:53:50 2024 Outgoing Data Channel: Cipher 'AES-256-GCM' initialized with 256 bit key
Sun Oct  6 06:53:50 2024 Incoming Data Channel: Cipher 'AES-256-GCM' initialized with 256 bit key
Sun Oct  6 06:53:50 2024 ROUTE_GATEWAY 172.25.250.254/255.255.255.0 IFACE=eth0 HWADDR=52:54:00:00:fa:09
Sun Oct  6 06:53:50 2024 TUN/TAP device tun0 opened
Sun Oct  6 06:53:50 2024 TUN/TAP TX queue length set to 100
Sun Oct  6 06:53:50 2024 /sbin/ip link set dev tun0 up mtu 1500
Sun Oct  6 06:53:50 2024 /sbin/ip addr add dev tun0 172.16.0.130/27 broadcast 172.16.0.159
Sun Oct  6 06:53:50 2024 /sbin/ip route add 10.2.0.0/16 via 172.16.0.129
Sun Oct  6 06:53:50 2024 /sbin/ip route add 10.1.0.0/16 via 172.16.0.129
Sun Oct  6 06:53:50 2024 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Sun Oct  6 06:53:50 2024 Initialization Sequence Completed

===================================================================================================== 2nd TERMINAL ===============================================================================================
[student@workstation ~]$ oc whoami 
cluster-admin
[student@workstation ~]$ 
[student@workstation ~]$ rosa whoami 
AWS ARN:                      arn:aws:iam::210940124124:user/open-environment-hnvcc-admin
AWS Account ID:               210940124124
AWS Default Region:           ap-southeast-2
OCM API:                      https://api.openshift.com
OCM Account Email:            saraj@redhat.com
OCM Account ID:               1smk11d25cYrVNyZcUkDjkQjEhf
OCM Account Name:             SANJU RAJ
OCM Account Username:         lws_sanjuraj
OCM Organization External ID: 14540894
OCM Organization ID:          1smk13BQJPldrljrpNVqM3JvqRp
OCM Organization Name:        SANJU RAJ

[student@workstation ~]$ rosa list clusters
ID                                NAME      STATE  TOPOLOGY
2e7hgds6t2ps7st0llufqfipkkhbuv0f  cs220lws  ready  Classic (STS)
[student@workstation ~]$ rosa list machinepools -c cs220lws
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS             TAINTS                               AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
memory  No           2         r5a.xlarge     workload=memory    memory-optimized=32GiB:NoSchedule    ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
worker  No           2         m5.xlarge                                                              ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ oc get nodes -L workload 
NAME                                            STATUS   ROLES                  AGE   VERSION            WORKLOAD
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   21h   v1.28.13+2ca1a23   
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           21h   v1.28.13+2ca1a23   
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   21h   v1.28.13+2ca1a23   
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   21h   v1.28.13+2ca1a23   
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 21h   v1.28.13+2ca1a23   
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           21h   v1.28.13+2ca1a23   
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 21h   v1.28.13+2ca1a23   
ip-10-1-0-63.ap-southeast-2.compute.internal    Ready    worker                 58m   v1.28.13+2ca1a23   memory
ip-10-1-0-93.ap-southeast-2.compute.internal    Ready    worker                 58m   v1.28.13+2ca1a23   memory
[student@workstation ~]$ oc new-project pod-scheduling
Now using project "pod-scheduling" on server "https://api.cs220lws.nw83.p1.openshiftapps.com:6443".

You can add applications to this project with the 'new-app' command. For example, try:

    oc new-app rails-postgresql-example

to build a new example application in Ruby. Or use kubectl to deploy a simple Kubernetes application:

    kubectl create deployment hello-node --image=k8s.gcr.io/e2e-test-images/agnhost:2.33 -- /agnhost serve-hostname

[student@workstation ~]$ wget https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/pod-scheduling/long-load.yaml
--2024-10-06 10:16:42--  https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/pod-scheduling/long-load.yaml
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.109.133, 185.199.110.133, 185.199.111.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1913 (1.9K) [text/plain]
Saving to: ‘long-load.yaml’

long-load.yaml                                       100%[=====================================================================================================================>]   1.87K  --.-KB/s    in 0s      

2024-10-06 10:16:43 (17.2 MB/s) - ‘long-load.yaml’ saved [1913/1913]

[student@workstation ~]$ cat long-load.yaml 
---
apiVersion: v1
kind: List
metadata: {}
items:
  - apiVersion: apps/v1
    kind: Deployment
    metadata:
      labels:
        app: long-load
      name: long-load
    spec:
      replicas: 2
      selector:
        matchLabels:
          app: long-load
      template:
        metadata:
          labels:
            app: long-load
        spec:
          nodeSelector:
            workload: memory
          tolerations:
            - key: "memory-optimized"
              operator: "Equal"
              value: "32GiB"
              effect: "NoSchedule"
          containers:
            - name: long-load
              image: quay.io/redhattraining/long-load:v1
              resources:
                requests:
                  memory: 20Gi
              ports:
                - containerPort: 3000
              readinessProbe:
                initialDelaySeconds: 10
                httpGet:
                  path: /health
                  port: 3000
              livenessProbe:
                initialDelaySeconds: 30
                httpGet:
                  path: /health
                  port: 3000
              securityContext:
                capabilities:
                  drop:
                    - ALL
                allowPrivilegeEscalation: false
          securityContext:
            runAsNonRoot: true
            seccompProfile:
              type: RuntimeDefault
  - apiVersion: v1
    kind: Service
    metadata:
      labels:
        app: long-load
      name: long-load
    spec:
      ports:
        - protocol: TCP
          port: 3000
          targetPort: 3000
      selector:
        app: long-load
  - apiVersion: route.openshift.io/v1
    kind: Route
    metadata:
      labels:
        app: long-load
      name: long-load
    spec:
      port:
        targetPort: 3000
      to:
        kind: Service
        name: long-load
      tls:
        termination: edge
[student@workstation ~]$ oc apply -f long-load.yaml 
deployment.apps/long-load created
service/long-load created
route.route.openshift.io/long-load created
[student@workstation ~]$ oc get pods -o wide 
NAME                         READY   STATUS              RESTARTS   AGE   IP       NODE                                           NOMINATED NODE   READINESS GATES
long-load-8647c68dcc-gwbs4   0/1     ContainerCreating   0          9s    <none>   ip-10-1-0-93.ap-southeast-2.compute.internal   <none>           <none>
long-load-8647c68dcc-h828n   0/1     ContainerCreating   0          9s    <none>   ip-10-1-0-63.ap-southeast-2.compute.internal   <none>           <none>
[student@workstation ~]$ oc get pods -o wide 
NAME                         READY   STATUS    RESTARTS   AGE   IP           NODE                                           NOMINATED NODE   READINESS GATES
long-load-8647c68dcc-gwbs4   0/1     Running   0          21s   10.131.2.6   ip-10-1-0-93.ap-southeast-2.compute.internal   <none>           <none>
long-load-8647c68dcc-h828n   0/1     Running   0          21s   10.128.4.6   ip-10-1-0-63.ap-southeast-2.compute.internal   <none>           <none>
[student@workstation ~]$ oc get pods -o wide 
NAME                         READY   STATUS    RESTARTS   AGE   IP           NODE                                           NOMINATED NODE   READINESS GATES
long-load-8647c68dcc-gwbs4   1/1     Running   0          34s   10.131.2.6   ip-10-1-0-93.ap-southeast-2.compute.internal   <none>           <none>
long-load-8647c68dcc-h828n   1/1     Running   0          34s   10.128.4.6   ip-10-1-0-63.ap-southeast-2.compute.internal   <none>           <none>
[student@workstation ~]$ oc get nodes -l workload=memory
NAME                                           STATUS   ROLES    AGE   VERSION
ip-10-1-0-63.ap-southeast-2.compute.internal   Ready    worker   64m   v1.28.13+2ca1a23
ip-10-1-0-93.ap-southeast-2.compute.internal   Ready    worker   64m   v1.28.13+2ca1a23
[student@workstation ~]$ wget https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/pod-scheduling/no-tolerations.yaml
--2024-10-06 10:24:21--  https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/pod-scheduling/no-tolerations.yaml
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.110.133, 185.199.111.133, 185.199.108.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.110.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1592 (1.6K) [text/plain]
Saving to: ‘no-tolerations.yaml’

no-tolerations.yaml                                  100%[=====================================================================================================================>]   1.55K  --.-KB/s    in 0s      

2024-10-06 10:24:22 (13.0 MB/s) - ‘no-tolerations.yaml’ saved [1592/1592]

[student@workstation ~]$ cat no-tolerations.yaml 
---
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: no-tolerations
  name: no-tolerations
spec:
  replicas: 1
  selector:
    matchLabels:
      app: no-tolerations
  template:
    metadata:
      labels:
        app: no-tolerations
    spec:
      nodeSelector:
        workload: memory
      containers:
        - name: mariadb
          image: registry.redhat.io/rhel9/mariadb-105
          ports:
            - containerPort: 3306
          env:
            - name: MYSQL_USER
              value: operator1
            - name: MYSQL_PASSWORD
              value: redhat
            - name: MYSQL_ROOT_PASSWORD
              value: redhat
            - name: MYSQL_DATABASE
              value: do120db
          livenessProbe:
            exec:
              command:
                - /bin/sh
                - -i
                - -c
                - MYSQL_PWD="$MYSQL_PASSWORD" mysqladmin -u $MYSQL_USER ping
            initialDelaySeconds: 30
            timeoutSeconds: 1
          readinessProbe:
            exec:
              command:
                - /bin/sh
                - -i
                - -c
                - MYSQL_PWD="$MYSQL_PASSWORD" mysqladmin -u $MYSQL_USER ping
            initialDelaySeconds: 5
            timeoutSeconds: 1
          resources:
            limits:
              memory: 512Mi
          securityContext:
            capabilities:
              drop:
                - ALL
            allowPrivilegeEscalation: false
      securityContext:
        runAsNonRoot: true
        seccompProfile:
          type: RuntimeDefault
[student@workstation ~]$ oc apply -f no-tolerations.yaml 
deployment.apps/no-tolerations created
[student@workstation ~]$ oc get pods 
NAME                              READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-gwbs4        1/1     Running   0          6m51s
long-load-8647c68dcc-h828n        1/1     Running   0          6m51s
no-tolerations-7bf44c8d54-cfdw7   0/1     Pending   0          25s
[student@workstation ~]$ oc describe pod no-tolerations-7bf44c8d54-cfdw7
Name:             no-tolerations-7bf44c8d54-cfdw7
Namespace:        pod-scheduling
Priority:         0
Service Account:  default
Node:             <none>
Labels:           app=no-tolerations
                  pod-template-hash=7bf44c8d54
Annotations:      openshift.io/scc: restricted-v2
                  seccomp.security.alpha.kubernetes.io/pod: runtime/default
Status:           Pending
IP:               
IPs:              <none>
Controlled By:    ReplicaSet/no-tolerations-7bf44c8d54
Containers:
  mariadb:
    Image:      registry.redhat.io/rhel9/mariadb-105
    Port:       3306/TCP
    Host Port:  0/TCP
    Limits:
      memory:  512Mi
    Requests:
      memory:   512Mi
    Liveness:   exec [/bin/sh -i -c MYSQL_PWD="$MYSQL_PASSWORD" mysqladmin -u $MYSQL_USER ping] delay=30s timeout=1s period=10s #success=1 #failure=3
    Readiness:  exec [/bin/sh -i -c MYSQL_PWD="$MYSQL_PASSWORD" mysqladmin -u $MYSQL_USER ping] delay=5s timeout=1s period=10s #success=1 #failure=3
    Environment:
      MYSQL_USER:           operator1
      MYSQL_PASSWORD:       redhat
      MYSQL_ROOT_PASSWORD:  redhat
      MYSQL_DATABASE:       do120db
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-nx5zg (ro)
Conditions:
  Type           Status
  PodScheduled   False 
Volumes:
  kube-api-access-nx5zg:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
    ConfigMapName:           openshift-service-ca.crt
    ConfigMapOptional:       <nil>
QoS Class:                   Burstable
Node-Selectors:              workload=memory
Tolerations:                 node.kubernetes.io/memory-pressure:NoSchedule op=Exists
                             node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason            Age   From               Message
  ----     ------            ----  ----               -------
  Warning  FailedScheduling  107s  default-scheduler  0/9 nodes are available: 2 node(s) didn't match Pod's node affinity/selector, 2 node(s) had untolerated taint {memory-optimized: 32GiB}, 2 node(s) had untolerated taint {node-role.kubernetes.io/infra: }, 3 node(s) had untolerated taint {node-role.kubernetes.io/master: }. preemption: 0/9 nodes are available: 9 Preemption is not helpful for scheduling..
[student@workstation ~]$ oc delete deployment no-tolerations 
deployment.apps "no-tolerations" deleted
[student@workstation ~]$ 


