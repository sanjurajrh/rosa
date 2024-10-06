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

===================================================================================================================== 2nd TERMINAL ===============================================================================
[student@workstation ~]$ oc whoami 
cluster-admin
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
[student@workstation ~]$ rosa describe cluster -c cs220lws | grep api 
API URL:                    https://api.cs220lws.nw83.p1.openshiftapps.com:6443
 - arn:aws:iam::210940124124:role/cs220lws-openshift-machine-api-aws-cloud-credentials
[student@workstation ~]$ 
[student@workstation ~]$ oc login -u cluster-admin -p Redhattraining123 https://api.cs220lws.nw83.p1.openshiftapps.com:6443 
Login successful.

You have access to 101 projects, the list has been suppressed. You can list all projects with 'oc projects'

Using project "pod-scheduling".
[student@workstation ~]$ rosa list machinepools -c cs220lws
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS             TAINTS                               AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
memory  No           2         r5a.xlarge     workload=memory    memory-optimized=32GiB:NoSchedule    ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
worker  No           2         m5.xlarge                                                              ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ oc project pod-scheduling 
Already on project "pod-scheduling" on server "https://api.cs220lws.nw83.p1.openshiftapps.com:6443".
[student@workstation ~]$ oc get pods,deployment 
NAME                             READY   STATUS    RESTARTS   AGE
pod/long-load-8647c68dcc-gwbs4   1/1     Running   0          19m
pod/long-load-8647c68dcc-h828n   1/1     Running   0          19m

NAME                        READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/long-load   2/2     2            2           19m
[student@workstation ~]$ oc scale deploy long-load --replicas 1
deployment.apps/long-load scaled
[student@workstation ~]$ oc get pods 
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-h828n   1/1     Running   0          21m
[student@workstation ~]$ wget https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/autoscale-pods/hpa.yaml
--2024-10-06 10:41:50--  https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/autoscale-pods/hpa.yaml
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.109.133, 185.199.110.133, 185.199.111.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 386 [text/plain]
Saving to: ‘hpa.yaml’

hpa.yaml                             100%[====================================================================>]     386  --.-KB/s    in 0s      

2024-10-06 10:41:51 (21.9 MB/s) - ‘hpa.yaml’ saved [386/386]

[student@workstation ~]$ cat hpa.yaml 
---
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  labels:
    app: long-load
  name: long-load
spec:
  minReplicas: 1
  maxReplicas: 4
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: long-load
  metrics:
    - type: Resource
      resource:
        name: memory
        target:
          type: Utilization
          averageUtilization: 2
[student@workstation ~]$ oc get podmetrics
error: the server doesn't have a resource type "podmetrics"
[student@workstation ~]$ oc get pods 
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-h828n   1/1     Running   0          26m
[student@workstation ~]$ oc adm top pod --sort-by=memory
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-h828n   0m           57Mi            
[student@workstation ~]$ oc adm top pod 
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-h828n   0m           57Mi            
[student@workstation ~]$ oc get deployment long-load -o json| jq '.items[].spec.template.spec.containers[0].resources'
jq: error (at <stdin>:144): Cannot iterate over null (null)
[student@workstation ~]$ oc get deployment long-load -o yaml | less 
[student@workstation ~]$ oc get deployment long-load -o yaml 
apiVersion: apps/v1
kind: Deployment
metadata:
  annotations:
    deployment.kubernetes.io/revision: "1"
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"apps/v1","kind":"Deployment","metadata":{"annotations":{},"labels":{"app":"long-load"},"name":"long-load","namespace":"pod-scheduling"},"spec":{"replicas":2,"selector":{"matchLabels":{"app":"long-load"}},"template":{"metadata":{"labels":{"app":"long-load"}},"spec":{"containers":[{"image":"quay.io/redhattraining/long-load:v1","livenessProbe":{"httpGet":{"path":"/health","port":3000},"initialDelaySeconds":30},"name":"long-load","ports":[{"containerPort":3000}],"readinessProbe":{"httpGet":{"path":"/health","port":3000},"initialDelaySeconds":10},"resources":{"requests":{"memory":"20Gi"}},"securityContext":{"allowPrivilegeEscalation":false,"capabilities":{"drop":["ALL"]}}}],"nodeSelector":{"workload":"memory"},"securityContext":{"runAsNonRoot":true,"seccompProfile":{"type":"RuntimeDefault"}},"tolerations":[{"effect":"NoSchedule","key":"memory-optimized","operator":"Equal","value":"32GiB"}]}}}}
  creationTimestamp: "2024-10-06T14:18:34Z"
  generation: 2
  labels:
    app: long-load
  name: long-load
  namespace: pod-scheduling
  resourceVersion: "835728"
  uid: 83776f84-f894-4cfd-b3e9-7cca75f9df4a
spec:
  progressDeadlineSeconds: 600
  replicas: 1
  revisionHistoryLimit: 10
  selector:
    matchLabels:
      app: long-load
  strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: long-load
    spec:
      containers:
      - image: quay.io/redhattraining/long-load:v1
        imagePullPolicy: IfNotPresent
        livenessProbe:
          failureThreshold: 3
          httpGet:
            path: /health
            port: 3000
            scheme: HTTP
          initialDelaySeconds: 30
          periodSeconds: 10
          successThreshold: 1
          timeoutSeconds: 1
        name: long-load
        ports:
        - containerPort: 3000
          protocol: TCP
        readinessProbe:
          failureThreshold: 3
          httpGet:
            path: /health
            port: 3000
            scheme: HTTP
          initialDelaySeconds: 10
          periodSeconds: 10
          successThreshold: 1
          timeoutSeconds: 1
        resources:
          requests:
            memory: 20Gi
        securityContext:
          allowPrivilegeEscalation: false
          capabilities:
            drop:
            - ALL
        terminationMessagePath: /dev/termination-log
        terminationMessagePolicy: File
      dnsPolicy: ClusterFirst
      nodeSelector:
        workload: memory
      restartPolicy: Always
      schedulerName: default-scheduler
      securityContext:
        runAsNonRoot: true
        seccompProfile:
          type: RuntimeDefault
      terminationGracePeriodSeconds: 30
      tolerations:
      - effect: NoSchedule
        key: memory-optimized
        operator: Equal
        value: 32GiB
status:
  availableReplicas: 1
  conditions:
  - lastTransitionTime: "2024-10-06T14:19:05Z"
    lastUpdateTime: "2024-10-06T14:19:05Z"
    message: Deployment has minimum availability.
    reason: MinimumReplicasAvailable
    status: "True"
    type: Available
  - lastTransitionTime: "2024-10-06T14:18:34Z"
    lastUpdateTime: "2024-10-06T14:19:05Z"
    message: ReplicaSet "long-load-8647c68dcc" has successfully progressed.
    reason: NewReplicaSetAvailable
    status: "True"
    type: Progressing
  observedGeneration: 2
  readyReplicas: 1
  replicas: 1
  updatedReplicas: 1
[student@workstation ~]$ oc apply -f hpa.yaml 
horizontalpodautoscaler.autoscaling/long-load created
[student@workstation ~]$ oc get hpa long-load -w 
NAME        REFERENCE              TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
long-load   Deployment/long-load   0%/2%     1         4         1          23s
long-load   Deployment/long-load   0%/2%     1         4         1          32s
long-load   Deployment/long-load   0%/2%     1         4         1          62s
long-load   Deployment/long-load   0%/2%     1         4         1          92s
long-load   Deployment/long-load   0%/2%     1         4         1          2m2s
long-load   Deployment/long-load   0%/2%     1         4         1          2m17s
long-load   Deployment/long-load   0%/2%     1         4         1          2m32s
long-load   Deployment/long-load   0%/2%     1         4         1          3m2s
long-load   Deployment/long-load   0%/2%     1         4         1          3m32s
long-load   Deployment/long-load   0%/2%     1         4         1          4m2s
long-load   Deployment/long-load   0%/2%     1         4         1          4m32s
long-load   Deployment/long-load   3%/2%     1         4         1          4m47s
long-load   Deployment/long-load   3%/2%     1         4         2          5m2s
long-load   Deployment/long-load   3%/2%     1         4         2          5m17s
long-load   Deployment/long-load   1%/2%     1         4         2          5m47s
long-load   Deployment/long-load   1%/2%     1         4         2          6m17s
long-load   Deployment/long-load   1%/2%     1         4         2          6m32s
long-load   Deployment/long-load   1%/2%     1         4         2          6m47s
long-load   Deployment/long-load   1%/2%     1         4         2          7m17s
long-load   Deployment/long-load   1%/2%     1         4         2          7m47s
long-load   Deployment/long-load   1%/2%     1         4         2          8m17s
long-load   Deployment/long-load   1%/2%     1         4         2          8m32s
long-load   Deployment/long-load   1%/2%     1         4         2          8m47s
long-load   Deployment/long-load   1%/2%     1         4         2          9m18s
long-load   Deployment/long-load   3%/2%     1         4         2          9m48s
long-load   Deployment/long-load   3%/2%     1         4         3          10m
long-load   Deployment/long-load   3%/2%     1         4         3          10m
long-load   Deployment/long-load   3%/2%     1         4         3          10m
long-load   Deployment/long-load   11%/2%    1         4         3          11m
long-load   Deployment/long-load   9%/2%     1         4         4          11m
long-load   Deployment/long-load   11%/2%    1         4         4          11m
long-load   Deployment/long-load   11%/2%    1         4         4          12m
long-load   Deployment/long-load   11%/2%    1         4         4          12m
long-load   Deployment/long-load   11%/2%    1         4         4          12m
long-load   Deployment/long-load   11%/2%    1         4         4          13m
long-load   Deployment/long-load   11%/2%    1         4         4          13m
long-load   Deployment/long-load   11%/2%    1         4         4          13m
long-load   Deployment/long-load   11%/2%    1         4         4          14m
long-load   Deployment/long-load   11%/2%    1         4         4          14m
long-load   Deployment/long-load   11%/2%    1         4         4          14m
long-load   Deployment/long-load   11%/2%    1         4         4          15m
long-load   Deployment/long-load   11%/2%    1         4         4          15m
[student@workstation ~]$ oc get hpa long-load -w 
NAME        REFERENCE              TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
long-load   Deployment/long-load   4%/2%     1         4         4          34m
^C[student@workstation ~]$ oc get hpa long-load -w
NAME        REFERENCE              TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
long-load   Deployment/long-load   4%/2%     1         4         4          34m
long-load   Deployment/long-load   4%/2%     1         4         4          34m
long-load   Deployment/long-load   4%/2%     1         4         4          34m
long-load   Deployment/long-load   4%/2%     1         4         4          35m
long-load   Deployment/long-load   0%/2%     1         4         4          35m
long-load   Deployment/long-load   0%/2%     1         4         4          35m
long-load   Deployment/long-load   0%/2%     1         4         4          35m
long-load   Deployment/long-load   0%/2%     1         4         4          36m
long-load   Deployment/long-load   0%/2%     1         4         4          36m
long-load   Deployment/long-load   0%/2%     1         4         4          36m
long-load   Deployment/long-load   0%/2%     1         4         4          36m
long-load   Deployment/long-load   0%/2%     1         4         4          37m
long-load   Deployment/long-load   0%/2%     1         4         4          37m
long-load   Deployment/long-load   0%/2%     1         4         4          37m
long-load   Deployment/long-load   0%/2%     1         4         4          37m
long-load   Deployment/long-load   0%/2%     1         4         4          38m
long-load   Deployment/long-load   0%/2%     1         4         4          38m
long-load   Deployment/long-load   0%/2%     1         4         4          38m
long-load   Deployment/long-load   0%/2%     1         4         4          38m
long-load   Deployment/long-load   0%/2%     1         4         4          39m
long-load   Deployment/long-load   0%/2%     1         4         4          39m
long-load   Deployment/long-load   0%/2%     1         4         4          39m
long-load   Deployment/long-load   0%/2%     1         4         4          39m
long-load   Deployment/long-load   0%/2%     1         4         4          40m
long-load   Deployment/long-load   0%/2%     1         4         1          40m
long-load   Deployment/long-load   0%/2%     1         4         1          40m
long-load   Deployment/long-load   0%/2%     1         4         1          41m
long-load   Deployment/long-load   0%/2%     1         4         1          41m
long-load   Deployment/long-load   0%/2%     1         4         1          42m
long-load   Deployment/long-load   0%/2%     1         4         1          42m
long-load   Deployment/long-load   0%/2%     1         4         1          43m
long-load   Deployment/long-load   0%/2%     1         4         1          43m
long-load   Deployment/long-load   0%/2%     1         4         1          44m
long-load   Deployment/long-load   0%/2%     1         4         1          44m
long-load   Deployment/long-load   0%/2%     1         4         1          44m
^C[student@workstation ~]$ 
=========================================================================================================== 3rd TERMINAL ==========================================================================================================



[student@workstation ~]$ oc get route 

NAME        HOST/PORT                                                          PATH   SERVICES    PORT   TERMINATION   WILDCARD
long-load   long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com          long-load   3000   edge          None
[student@workstation ~]$ 
[student@workstation ~]$ oc adm top pod 
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-97bvf   0m           54Mi            
long-load-8647c68dcc-h828n   0m           732Mi           
[student@workstation ~]$ oc adm top pod 
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-97bvf   0m           54Mi            
long-load-8647c68dcc-h828n   56m          702Mi           
[student@workstation ~]$ oc get pods,deploymnet 
error: the server doesn't have a resource type "deploymnet"
[student@workstation ~]$ oc get pods,deployment

NAME                             READY   STATUS    RESTARTS   AGE
pod/long-load-8647c68dcc-97bvf   1/1     Running   0          4m13s
pod/long-load-8647c68dcc-h828n   1/1     Running   0          41m

NAME                        READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/long-load   2/2     2            2           41m
[student@workstation ~]$ 
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak
consuming memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak
^[[Aconsuming memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak
consuming memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak
consuming memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak
consuming memory!
[student@workstation ~]$ oc adm top pod 
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-97bvf   369m         2023Mi          
long-load-8647c68dcc-h828n   0m           1350Mi          
[student@workstation ~]$ oc get pods 
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-2mxdq   0/1     Pending   0          4m49s
long-load-8647c68dcc-97bvf   1/1     Running   0          9m50s
long-load-8647c68dcc-h828n   1/1     Running   0          46m
long-load-8647c68dcc-kz5wx   0/1     Pending   0          3m19s
[student@workstation ~]$ oc describe pod long-load-8647c68dcc-2mxdq
Name:             long-load-8647c68dcc-2mxdq
Namespace:        pod-scheduling
Priority:         0
Service Account:  default
Node:             <none>
Labels:           app=long-load
                  pod-template-hash=8647c68dcc
Annotations:      openshift.io/scc: restricted-v2
                  seccomp.security.alpha.kubernetes.io/pod: runtime/default
Status:           Pending
IP:               
IPs:              <none>
Controlled By:    ReplicaSet/long-load-8647c68dcc
Containers:
  long-load:
    Image:      quay.io/redhattraining/long-load:v1
    Port:       3000/TCP
    Host Port:  0/TCP
    Requests:
      memory:     20Gi
    Liveness:     http-get http://:3000/health delay=30s timeout=1s period=10s #success=1 #failure=3
    Readiness:    http-get http://:3000/health delay=10s timeout=1s period=10s #success=1 #failure=3
    Environment:  <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-7nsk9 (ro)
Conditions:
  Type           Status
  PodScheduled   False 
Volumes:
  kube-api-access-7nsk9:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
    ConfigMapName:           openshift-service-ca.crt
    ConfigMapOptional:       <nil>
QoS Class:                   Burstable
Node-Selectors:              workload=memory
Tolerations:                 memory-optimized=32GiB:NoSchedule
                             node.kubernetes.io/memory-pressure:NoSchedule op=Exists
                             node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason            Age                    From               Message
  ----     ------            ----                   ----               -------
  Warning  FailedScheduling  6m46s                  default-scheduler  0/9 nodes are available: 2 Insufficient memory, 2 node(s) didn't match Pod's node affinity/selector, 2 node(s) had untolerated taint {node-role.kubernetes.io/infra: }, 3 node(s) had untolerated taint {node-role.kubernetes.io/master: }. preemption: 0/9 nodes are available: 2 No preemption victims found for incoming pod, 7 Preemption is not helpful for scheduling..
  Warning  FailedScheduling  6m38s (x2 over 6m40s)  default-scheduler  0/9 nodes are available: 2 Insufficient memory, 2 node(s) didn't match Pod's node affinity/selector, 2 node(s) had untolerated taint {node-role.kubernetes.io/infra: }, 3 node(s) had untolerated taint {node-role.kubernetes.io/master: }. preemption: 0/9 nodes are available: 2 No preemption victims found for incoming pod, 7 Preemption is not helpful for scheduling..
[student@workstation ~]$ oc get nodes -L workload 
NAME                                            STATUS   ROLES                  AGE    VERSION            WORKLOAD
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23   
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           22h    v1.28.13+2ca1a23   
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23   
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23   
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 22h    v1.28.13+2ca1a23   
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           22h    v1.28.13+2ca1a23   
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 22h    v1.28.13+2ca1a23   
ip-10-1-0-63.ap-southeast-2.compute.internal    Ready    worker                 115m   v1.28.13+2ca1a23   memory
ip-10-1-0-93.ap-southeast-2.compute.internal    Ready    worker                 115m   v1.28.13+2ca1a23   memory
[student@workstation ~]$ oc describe nodes ip-10-1-0-63.ap-southeast-2.compute.internal
Name:               ip-10-1-0-63.ap-southeast-2.compute.internal
Roles:              worker
Labels:             beta.kubernetes.io/arch=amd64
                    beta.kubernetes.io/instance-type=r5a.xlarge
                    beta.kubernetes.io/os=linux
                    failure-domain.beta.kubernetes.io/region=ap-southeast-2
                    failure-domain.beta.kubernetes.io/zone=ap-southeast-2a
                    kubernetes.io/arch=amd64
                    kubernetes.io/hostname=ip-10-1-0-63.ap-southeast-2.compute.internal
                    kubernetes.io/os=linux
                    node-role.kubernetes.io/worker=
                    node.kubernetes.io/instance-type=r5a.xlarge
                    node.openshift.io/os_id=rhcos
                    topology.ebs.csi.aws.com/zone=ap-southeast-2a
                    topology.kubernetes.io/region=ap-southeast-2
                    topology.kubernetes.io/zone=ap-southeast-2a
                    workload=memory
Annotations:        cloud.network.openshift.io/egress-ipconfig:
                      [{"interface":"eni-06c68eda510378afd","ifaddr":{"ipv4":"10.1.0.0/24"},"capacity":{"ipv4":14,"ipv6":15}}]
                    csi.volume.kubernetes.io/nodeid: {"ebs.csi.aws.com":"i-01cd1b2a093b4a3c6"}
                    k8s.ovn.org/host-cidrs: ["10.1.0.63/24"]
                    k8s.ovn.org/l3-gateway-config:
                      {"default":{"mode":"shared","interface-id":"br-ex_ip-10-1-0-63.ap-southeast-2.compute.internal","mac-address":"02:f5:5c:30:7b:01","ip-addr...
                    k8s.ovn.org/network-ids: {"default":"0"}
                    k8s.ovn.org/node-chassis-id: 8e4a9be2-7fcc-4041-ac0a-1ec7af23ab16
                    k8s.ovn.org/node-gateway-router-lrp-ifaddr: {"ipv4":"100.64.0.10/16"}
                    k8s.ovn.org/node-id: 10
                    k8s.ovn.org/node-mgmt-port-mac-address: 82:f9:f9:a3:e0:a3
                    k8s.ovn.org/node-primary-ifaddr: {"ipv4":"10.1.0.63/24"}
                    k8s.ovn.org/node-subnets: {"default":["10.128.4.0/23"]}
                    k8s.ovn.org/node-transit-switch-port-ifaddr: {"ipv4":"100.88.0.10/16"}
                    k8s.ovn.org/remote-zone-migrated: ip-10-1-0-63.ap-southeast-2.compute.internal
                    k8s.ovn.org/zone-name: ip-10-1-0-63.ap-southeast-2.compute.internal
                    machine.openshift.io/machine: openshift-machine-api/cs220lws-cxw8p-memory-ap-southeast-2a-np7l9
                    machineconfiguration.openshift.io/controlPlaneTopology: HighlyAvailable
                    machineconfiguration.openshift.io/currentConfig: rendered-worker-9cfee7ea754656efc3e9f57457f27b25
                    machineconfiguration.openshift.io/desiredConfig: rendered-worker-9cfee7ea754656efc3e9f57457f27b25
                    machineconfiguration.openshift.io/desiredDrain: uncordon-rendered-worker-9cfee7ea754656efc3e9f57457f27b25
                    machineconfiguration.openshift.io/lastAppliedDrain: uncordon-rendered-worker-9cfee7ea754656efc3e9f57457f27b25
                    machineconfiguration.openshift.io/lastSyncedControllerConfigResourceVersion: 722492
                    machineconfiguration.openshift.io/reason: 
                    machineconfiguration.openshift.io/state: Done
                    managed.openshift.com/customlabels: workload
                    volumes.kubernetes.io/controller-managed-attach-detach: true
CreationTimestamp:  Sun, 06 Oct 2024 09:14:52 -0400
Taints:             memory-optimized=32GiB:NoSchedule
Unschedulable:      false
Lease:
  HolderIdentity:  ip-10-1-0-63.ap-southeast-2.compute.internal
  AcquireTime:     <unset>
  RenewTime:       Sun, 06 Oct 2024 11:10:09 -0400
Conditions:
  Type             Status  LastHeartbeatTime                 LastTransitionTime                Reason                       Message
  ----             ------  -----------------                 ------------------                ------                       -------
  MemoryPressure   False   Sun, 06 Oct 2024 11:10:07 -0400   Sun, 06 Oct 2024 09:14:52 -0400   KubeletHasSufficientMemory   kubelet has sufficient memory available
  DiskPressure     False   Sun, 06 Oct 2024 11:10:07 -0400   Sun, 06 Oct 2024 09:14:52 -0400   KubeletHasNoDiskPressure     kubelet has no disk pressure
  PIDPressure      False   Sun, 06 Oct 2024 11:10:07 -0400   Sun, 06 Oct 2024 09:14:52 -0400   KubeletHasSufficientPID      kubelet has sufficient PID available
  Ready            True    Sun, 06 Oct 2024 11:10:07 -0400   Sun, 06 Oct 2024 09:16:19 -0400   KubeletReady                 kubelet is posting ready status
Addresses:
  InternalIP:   10.1.0.63
  InternalDNS:  ip-10-1-0-63.ap-southeast-2.compute.internal
  Hostname:     ip-10-1-0-63.ap-southeast-2.compute.internal
Capacity:
  cpu:                4
  ephemeral-storage:  313981932Ki
  hugepages-1Gi:      0
  hugepages-2Mi:      0
  memory:             32483080Ki
  pods:               250
Allocatable:
  cpu:                3920m
  ephemeral-storage:  288292006229
  hugepages-1Gi:      0
  hugepages-2Mi:      0
  memory:             29234952Ki
  pods:               250
System Info:
  Machine ID:                             ec214048e08ec7ea6a38807d287bbac9
  System UUID:                            ec214048-e08e-c7ea-6a38-807d287bbac9
  Boot ID:                                f4b05d0f-7859-4333-bdf2-b1bb43dc5bcd
  Kernel Version:                         5.14.0-284.84.1.el9_2.x86_64
  OS Image:                               Red Hat Enterprise Linux CoreOS 415.92.202409101905-0 (Plow)
  Operating System:                       linux
  Architecture:                           amd64
  Container Runtime Version:              cri-o://1.28.10-3.rhaos4.15.git368cd23.el9
  Kubelet Version:                        v1.28.13+2ca1a23
  Kube-Proxy Version:                     v1.28.13+2ca1a23
ProviderID:                               aws:///ap-southeast-2a/i-01cd1b2a093b4a3c6
Non-terminated Pods:                      (14 in total)
  Namespace                               Name                                                                 CPU Requests  CPU Limits  Memory Requests  Memory Limits  Age
  ---------                               ----                                                                 ------------  ----------  ---------------  -------------  ---
  openshift-cluster-csi-drivers           aws-ebs-csi-driver-node-hlt7c                                        30m (0%)      0 (0%)      150Mi (0%)       0 (0%)         115m
  openshift-cluster-node-tuning-operator  tuned-bm2rd                                                          10m (0%)      0 (0%)      50Mi (0%)        0 (0%)         115m
  openshift-dns                           node-resolver-kqd7z                                                  5m (0%)       0 (0%)      21Mi (0%)        0 (0%)         115m
  openshift-image-registry                node-ca-85lps                                                        10m (0%)      0 (0%)      10Mi (0%)        0 (0%)         115m
  openshift-machine-config-operator       kube-rbac-proxy-crio-ip-10-1-0-63.ap-southeast-2.compute.internal    20m (0%)      0 (0%)      50Mi (0%)        0 (0%)         115m
  openshift-machine-config-operator       machine-config-daemon-8btd9                                          40m (1%)      0 (0%)      100Mi (0%)       0 (0%)         115m
  openshift-monitoring                    node-exporter-9k6j9                                                  9m (0%)       0 (0%)      47Mi (0%)        0 (0%)         115m
  openshift-multus                        multus-additional-cni-plugins-2jl8v                                  10m (0%)      0 (0%)      10Mi (0%)        0 (0%)         115m
  openshift-multus                        multus-mr85m                                                         10m (0%)      0 (0%)      65Mi (0%)        0 (0%)         115m
  openshift-multus                        network-metrics-daemon-6b7wf                                         20m (0%)      0 (0%)      120Mi (0%)       0 (0%)         115m
  openshift-network-diagnostics           network-check-target-vj9jk                                           10m (0%)      0 (0%)      15Mi (0%)        0 (0%)         115m
  openshift-ovn-kubernetes                ovnkube-node-bzm6p                                                   80m (2%)      0 (0%)      1630Mi (5%)      0 (0%)         115m
  openshift-security                      splunkforwarder-ds-86hbg                                             0 (0%)        0 (0%)      0 (0%)           0 (0%)         115m
  pod-scheduling                          long-load-8647c68dcc-h828n                                           0 (0%)        0 (0%)      20Gi (71%)       0 (0%)         51m
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests       Limits
  --------           --------       ------
  cpu                254m (6%)      0 (0%)
  memory             22748Mi (79%)  0 (0%)
  ephemeral-storage  0 (0%)         0 (0%)
  hugepages-1Gi      0 (0%)         0 (0%)
  hugepages-2Mi      0 (0%)         0 (0%)
Events:
  Type    Reason                   Age                  From                   Message
  ----    ------                   ----                 ----                   -------
  Normal  Starting                 115m                 kubelet                Starting kubelet.
  Normal  NodeHasSufficientMemory  115m                 kubelet                Node ip-10-1-0-63.ap-southeast-2.compute.internal status is now: NodeHasSufficientMemory
  Normal  NodeHasNoDiskPressure    115m                 kubelet                Node ip-10-1-0-63.ap-southeast-2.compute.internal status is now: NodeHasNoDiskPressure
  Normal  NodeHasSufficientPID     115m                 kubelet                Node ip-10-1-0-63.ap-southeast-2.compute.internal status is now: NodeHasSufficientPID
  Normal  Synced                   115m                 cloud-node-controller  Node synced successfully
  Normal  Starting                 115m                 kubelet                Starting kubelet.
  Normal  NodeHasSufficientMemory  115m (x2 over 115m)  kubelet                Node ip-10-1-0-63.ap-southeast-2.compute.internal status is now: NodeHasSufficientMemory
  Normal  NodeHasNoDiskPressure    115m (x2 over 115m)  kubelet                Node ip-10-1-0-63.ap-southeast-2.compute.internal status is now: NodeHasNoDiskPressure
  Normal  NodeHasSufficientPID     115m (x2 over 115m)  kubelet                Node ip-10-1-0-63.ap-southeast-2.compute.internal status is now: NodeHasSufficientPID
  Normal  NodeAllocatableEnforced  115m                 kubelet                Updated Node Allocatable limit across pods
  Normal  RegisteredNode           115m                 node-controller        Node ip-10-1-0-63.ap-southeast-2.compute.internal event: Registered Node ip-10-1-0-63.ap-southeast-2.compute.internal in Controller
  Normal  NodeReady                113m                 kubelet                Node ip-10-1-0-63.ap-southeast-2.compute.internal status is now: NodeReady
[student@workstation ~]$ oc get machinesets -A 
NAMESPACE               NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           22h
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a   2         2         2       2           122m
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           22h
[student@workstation ~]$ rosa list machinepools -c cs220lws
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS             TAINTS                               AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
memory  No           2         r5a.xlarge     workload=memory    memory-optimized=32GiB:NoSchedule    ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
worker  No           2         m5.xlarge                                                              ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ 
[student@workstation ~]$ rosa edit machinepool --replicas 3 -c cs220lws memory 

I: Updated machine pool 'memory' on cluster 'cs220lws'
[student@workstation ~]$ 
[student@workstation ~]$ 
[student@workstation ~]$ rosa list machinepools -c cs220lws
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS             TAINTS                               AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
memory  No           3         r5a.xlarge     workload=memory    memory-optimized=32GiB:NoSchedule    ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
worker  No           2         m5.xlarge                                                              ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ 
[student@workstation ~]$ oc get machinesets -A 
NAMESPACE               NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           22h
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a   3         3         2       2           124m
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           22h
[student@workstation ~]$ 
[student@workstation ~]$ 
[student@workstation ~]$ oc get nodes 
NAME                                            STATUS   ROLES                  AGE    VERSION
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           22h    v1.28.13+2ca1a23
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 22h    v1.28.13+2ca1a23
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           22h    v1.28.13+2ca1a23
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 22h    v1.28.13+2ca1a23
ip-10-1-0-63.ap-southeast-2.compute.internal    Ready    worker                 120m   v1.28.13+2ca1a23
ip-10-1-0-93.ap-southeast-2.compute.internal    Ready    worker                 120m   v1.28.13+2ca1a23
[student@workstation ~]$ oc get nodes  -L workload 
NAME                                            STATUS   ROLES                  AGE    VERSION            WORKLOAD
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23   
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           22h    v1.28.13+2ca1a23   
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23   
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23   
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 22h    v1.28.13+2ca1a23   
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           22h    v1.28.13+2ca1a23   
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 22h    v1.28.13+2ca1a23   
ip-10-1-0-63.ap-southeast-2.compute.internal    Ready    worker                 120m   v1.28.13+2ca1a23   memory
ip-10-1-0-93.ap-southeast-2.compute.internal    Ready    worker                 120m   v1.28.13+2ca1a23   memory
[student@workstation ~]$ oc get pods 
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-2mxdq   0/1     Pending   0          15m
long-load-8647c68dcc-97bvf   1/1     Running   0          20m
long-load-8647c68dcc-h828n   1/1     Running   0          57m
long-load-8647c68dcc-kz5wx   0/1     Pending   0          14m
[student@workstation ~]$ oc get pods 
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-2mxdq   0/1     Pending   0          16m
long-load-8647c68dcc-97bvf   1/1     Running   0          21m
long-load-8647c68dcc-h828n   1/1     Running   0          57m
long-load-8647c68dcc-kz5wx   0/1     Pending   0          14m
[student@workstation ~]$ watch -d oc get nodes  -L workload 
[student@workstation ~]$ oc get pods 
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-2mxdq   0/1     Pending   0          20m
long-load-8647c68dcc-97bvf   1/1     Running   0          25m
long-load-8647c68dcc-h828n   1/1     Running   0          62m
long-load-8647c68dcc-kz5wx   0/1     Running   0          18m
[student@workstation ~]$ oc get nodes  -L workload 
NAME                                            STATUS   ROLES                  AGE    VERSION            WORKLOAD
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23   
ip-10-1-0-189.ap-southeast-2.compute.internal   Ready    worker                 106s   v1.28.13+2ca1a23   memory
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           22h    v1.28.13+2ca1a23   
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23   
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   22h    v1.28.13+2ca1a23   
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 22h    v1.28.13+2ca1a23   
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           22h    v1.28.13+2ca1a23   
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 22h    v1.28.13+2ca1a23   
ip-10-1-0-63.ap-southeast-2.compute.internal    Ready    worker                 125m   v1.28.13+2ca1a23   memory
ip-10-1-0-93.ap-southeast-2.compute.internal    Ready    worker                 125m   v1.28.13+2ca1a23   memory
[student@workstation ~]$ oc get pods 
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-2mxdq   0/1     Pending   0          20m
long-load-8647c68dcc-97bvf   1/1     Running   0          25m
long-load-8647c68dcc-h828n   1/1     Running   0          62m
long-load-8647c68dcc-kz5wx   0/1     Running   0          18m
[student@workstation ~]$ oc get pods 
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-2mxdq   0/1     Pending   0          20m
long-load-8647c68dcc-97bvf   1/1     Running   0          25m
long-load-8647c68dcc-h828n   1/1     Running   0          62m
long-load-8647c68dcc-kz5wx   0/1     Running   0          19m
[student@workstation ~]$ oc get pods -w
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-2mxdq   0/1     Pending   0          20m
long-load-8647c68dcc-97bvf   1/1     Running   0          25m
long-load-8647c68dcc-h828n   1/1     Running   0          62m
long-load-8647c68dcc-kz5wx   1/1     Running   0          19m
^C[student@workstation ~]$ oc get pods 
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-2mxdq   0/1     Pending   0          20m
long-load-8647c68dcc-97bvf   1/1     Running   0          25m
long-load-8647c68dcc-h828n   1/1     Running   0          62m
long-load-8647c68dcc-kz5wx   1/1     Running   0          19m
[student@workstation ~]$ oc get machinesets -A 
NAMESPACE               NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           22h
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a   3         3         3       3           132m
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           22h
[student@workstation ~]$ oc get route 
NAME        HOST/PORT                                                          PATH   SERVICES    PORT   TERMINATION   WILDCARD
long-load   long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com          long-load   3000   edge          None
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/unleak
releasing memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/unleak
releasing memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/unleak
releasing memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/unleak
releasing memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/unleak
releasing memory!
[student@workstation ~]$ oc adm top pod 
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-97bvf   0m           2642Mi          
long-load-8647c68dcc-h828n   0m           1999Mi          
long-load-8647c68dcc-kz5wx   0m           55Mi            
[student@workstation ~]$ watch -d oc adm top pod 
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/unleak
releasing memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/unleak
releasing memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/unleak
releasing memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/unleak
releasing memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/unleak
releasing memory!
[student@workstation ~]$ watch -d oc adm top pod 
[student@workstation ~]$ oc adm top pod 
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-h828n   0m           70Mi            
[student@workstation ~]$ oc get pods 
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-h828n   1/1     Running   0          73m
[student@workstation ~]$ rosa edit machinepool --replicas 2 -c cs220lws memory
I: Updated machine pool 'memory' on cluster 'cs220lws'
[student@workstation ~]$ rosa list machinepools 
Error: required flag(s) "cluster" not set
Usage:
  rosa list machinepools [flags]

Aliases:
  machinepools, machinepool, machine-pools, machine-pool

Examples:
  # List all machine pools on a cluster named "mycluster"
  rosa list machinepools --cluster=mycluster

Flags:
  -c, --cluster string   Name or ID of the cluster.
  -h, --help             help for machinepools
  -o, --output string    Output format. Allowed formats are [json yaml]

Global Flags:
      --color string     Surround certain characters with escape sequences to display them in color on the terminal. Allowed options are [auto never always] (default "auto")
      --debug            Enable debug mode.
      --profile string   Use a specific AWS profile from your credential file.
      --region string    Use a specific AWS region, overriding the AWS_REGION environment variable.

Failed to execute root command: required flag(s) "cluster" not set
[student@workstation ~]$ rosa list machinepools -c cs220lws
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS             TAINTS                               AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
memory  No           2         r5a.xlarge     workload=memory    memory-optimized=32GiB:NoSchedule    ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
worker  No           2         m5.xlarge                                                              ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ oc get machinesets -n openshift-machine-api
NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           22h
cs220lws-cxw8p-memory-ap-southeast-2a   2         2         2       2           144m
cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           23h
[student@workstation ~]$ 
[student@workstation ~]$ 



