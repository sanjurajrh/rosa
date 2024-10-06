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

============================================================================================================ 2nd TERMINAL =========================================================================================
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

[student@workstation ~]$ oc whoami  
cluster-admin
[student@workstation ~]$ rosa list machinepools -c cs220lws
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS             TAINTS                               AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
memory  No           2         r5a.xlarge     workload=memory    memory-optimized=32GiB:NoSchedule    ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
worker  No           2         m5.xlarge                                                              ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ oc project deployment,pods
error: A project named "deployment,pods" does not exist on "https://api.cs220lws.nw83.p1.openshiftapps.com:6443".
Your projects are:
* dedicated-admin
* default
* kube-node-lease
* kube-public
* kube-system
* openshift
* openshift-addon-operator
* openshift-apiserver
* openshift-apiserver-operator
* openshift-aqua
* openshift-authentication
* openshift-authentication-operator
* openshift-backplane
* openshift-backplane-cee
* openshift-backplane-csa
* openshift-backplane-cse
* openshift-backplane-csm
* openshift-backplane-managed-scripts
* openshift-backplane-mobb
* openshift-backplane-srep
* openshift-backplane-tam
* openshift-cloud-controller-manager
* openshift-cloud-controller-manager-operator
* openshift-cloud-credential-operator
* openshift-cloud-network-config-controller
* openshift-cloud-platform-infra
* openshift-cluster-csi-drivers
* openshift-cluster-machine-approver
* openshift-cluster-node-tuning-operator
* openshift-cluster-samples-operator
* openshift-cluster-storage-operator
* openshift-cluster-version
* openshift-codeready-workspaces
* openshift-config
* openshift-config-managed
* openshift-config-operator
* openshift-console
* openshift-console-operator
* openshift-console-user-settings
* openshift-controller-manager
* openshift-controller-manager-operator
* openshift-custom-domains-operator
* openshift-customer-monitoring
* openshift-deployment-validation-operator
* openshift-dns
* openshift-dns-operator
* openshift-etcd
* openshift-etcd-operator
* openshift-host-network
* openshift-image-registry
* openshift-infra
* openshift-ingress
* openshift-ingress-canary
* openshift-ingress-operator
* openshift-insights
* openshift-kni-infra
* openshift-kube-apiserver
* openshift-kube-apiserver-operator
* openshift-kube-controller-manager
* openshift-kube-controller-manager-operator
* openshift-kube-scheduler
* openshift-kube-scheduler-operator
* openshift-kube-storage-version-migrator
* openshift-kube-storage-version-migrator-operator
* openshift-logging
* openshift-machine-api
* openshift-machine-config-operator
* openshift-managed-node-metadata-operator
* openshift-managed-upgrade-operator
* openshift-marketplace
* openshift-monitoring
* openshift-multus
* openshift-must-gather-operator
* openshift-network-diagnostics
* openshift-network-node-identity
* openshift-network-operator
* openshift-node
* openshift-nutanix-infra
* openshift-oauth-apiserver
* openshift-observability-operator
* openshift-ocm-agent-operator
* openshift-openstack-infra
* openshift-operator-lifecycle-manager
* openshift-operators
* openshift-operators-redhat
* openshift-osd-metrics
* openshift-ovirt-infra
* openshift-ovn-kubernetes
* openshift-package-operator
* openshift-rbac-permissions
* openshift-route-controller-manager
* openshift-route-monitor-operator
* openshift-security
* openshift-service-ca
* openshift-service-ca-operator
* openshift-splunk-forwarder-operator
* openshift-sre-pruning
* openshift-user-workload-monitoring
* openshift-validation-webhook
* openshift-vsphere-infra
* pod-scheduling
[student@workstation ~]$ 
[student@workstation ~]$ oc project pod-scheduling 
oAlready on project "pod-scheduling" on server "https://api.cs220lws.nw83.p1.openshiftapps.com:6443".
[student@workstation ~]$ oc get deployment,pods
NAME                        READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/long-load   1/1     1            1           130m

NAME                             READY   STATUS    RESTARTS   AGE
pod/long-load-8647c68dcc-h828n   1/1     Running   0          130m
[student@workstation ~]$ oc get hpa 
NAME        REFERENCE              TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
long-load   Deployment/long-load   0%/2%     1         4         1          98m
[student@workstation ~]$ rosa edit machinepool -c cs220lws --enable-autoscaling --min-replicas 2 --max-replicas 3 memory 
I: Updated machine pool 'memory' on cluster 'cs220lws'
[student@workstation ~]$ 
[student@workstation ~]$ rosa list machinepools -c cs220lws 
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS             TAINTS                               AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
memory  Yes          2-3       r5a.xlarge     workload=memory    memory-optimized=32GiB:NoSchedule    ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
worker  No           2         m5.xlarge                                                              ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ oc get machineautoscalers.autoscaling.openshift.io -A 
NAMESPACE               NAME                                    REF KIND     REF NAME                                MIN   MAX   AGE
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a   MachineSet   cs220lws-cxw8p-memory-ap-southeast-2a   2     3     4m12s
[student@workstation ~]$ oc get machineset -n openshift-machine-api 
NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           23h
cs220lws-cxw8p-memory-ap-southeast-2a   2         2         2       2           3h28m
cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           24h
[student@workstation ~]$ oc get route 
NAME        HOST/PORT                                                          PATH   SERVICES    PORT   TERMINATION   WILDCARD
long-load   long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com          long-load   3000   edge          None
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak 
consuming memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak 
consuming memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak 
consuming memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak 
consuming memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak 
consuming memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak 
consuming memory!
[student@workstation ~]$ oc adm top pod 
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-h828n   1058m        3914Mi          
[student@workstation ~]$ oc adm top pod 
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-h828n   1058m        3914Mi          
[student@workstation ~]$ oc adm top pod -w
error: unknown shorthand flag: 'w' in -w
See 'oc adm top pod --help' for usage.
[student@workstation ~]$ watch oc adm top pod 
[student@workstation ~]$ oc adm top pod 
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-h828n   1297m        3914Mi          
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak 
consuming memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak 
consuming memory!
[student@workstation ~]$ curl https://long-load-pod-scheduling.apps.cs220lws.nw83.p1.openshiftapps.com/leak 
consuming memory!
[student@workstation ~]$ oc adm top pod 
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-d4jhl   38m          52Mi            
long-load-8647c68dcc-h828n   524m         3939Mi          
[student@workstation ~]$ oc get hpa 
NAME        REFERENCE              TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
long-load   Deployment/long-load   9%/2%     1         4         4          113m
[student@workstation ~]$ oc get pod -o wide 
NAME                         READY   STATUS    RESTARTS   AGE    IP           NODE                                            NOMINATED NODE   READINESS GATES
long-load-8647c68dcc-d4jhl   1/1     Running   0          94s    10.129.4.7   ip-10-1-0-189.ap-southeast-2.compute.internal   <none>           <none>
long-load-8647c68dcc-d9sm8   0/1     Pending   0          94s    <none>       <none>                                          <none>           <none>
long-load-8647c68dcc-h828n   1/1     Running   0          145m   10.128.4.6   ip-10-1-0-63.ap-southeast-2.compute.internal    <none>           <none>
long-load-8647c68dcc-q9zwr   0/1     Pending   0          94s    <none>       <none>                                          <none>           <none>
[student@workstation ~]$ oc adm top pod 
NAME                         CPU(cores)   MEMORY(bytes)   
long-load-8647c68dcc-d4jhl   434m         1994Mi          
long-load-8647c68dcc-h828n   0m           3940Mi          
[student@workstation ~]$ oc get pod -o wide 
NAME                         READY   STATUS    RESTARTS   AGE    IP           NODE                                            NOMINATED NODE   READINESS GATES
long-load-8647c68dcc-d4jhl   1/1     Running   0          5m8s   10.129.4.7   ip-10-1-0-189.ap-southeast-2.compute.internal   <none>           <none>
long-load-8647c68dcc-d9sm8   0/1     Pending   0          5m8s   <none>       <none>                                          <none>           <none>
long-load-8647c68dcc-h828n   1/1     Running   0          149m   10.128.4.6   ip-10-1-0-63.ap-southeast-2.compute.internal    <none>           <none>
long-load-8647c68dcc-q9zwr   0/1     Pending   0          5m8s   <none>       <none>                                          <none>           <none>
[student@workstation ~]$ oc get nodes -L workload
NAME                                            STATUS     ROLES                  AGE     VERSION            WORKLOAD
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready      control-plane,master   24h     v1.28.13+2ca1a23   
ip-10-1-0-189.ap-southeast-2.compute.internal   Ready      worker                 89m     v1.28.13+2ca1a23   memory
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready      infra,worker           23h     v1.28.13+2ca1a23   
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready      control-plane,master   24h     v1.28.13+2ca1a23   
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready      control-plane,master   24h     v1.28.13+2ca1a23   
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready      worker                 24h     v1.28.13+2ca1a23   
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready      infra,worker           23h     v1.28.13+2ca1a23   
ip-10-1-0-35.ap-southeast-2.compute.internal    NotReady   worker                 56s     v1.28.13+2ca1a23   memory
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready      worker                 24h     v1.28.13+2ca1a23   
ip-10-1-0-63.ap-southeast-2.compute.internal    Ready      worker                 3h33m   v1.28.13+2ca1a23   memory
[student@workstation ~]$ oc get machineset -n openshift-machine-api
NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           23h
cs220lws-cxw8p-memory-ap-southeast-2a   3         3         2       2           3h37m
cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           24h
[student@workstation ~]$ oc get nodes -L workload
NAME                                            STATUS   ROLES                  AGE     VERSION            WORKLOAD
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   24h     v1.28.13+2ca1a23   
ip-10-1-0-189.ap-southeast-2.compute.internal   Ready    worker                 90m     v1.28.13+2ca1a23   memory
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           23h     v1.28.13+2ca1a23   
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   24h     v1.28.13+2ca1a23   
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   24h     v1.28.13+2ca1a23   
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 24h     v1.28.13+2ca1a23   
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           23h     v1.28.13+2ca1a23   
ip-10-1-0-35.ap-southeast-2.compute.internal    Ready    worker                 2m42s   v1.28.13+2ca1a23   memory
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 24h     v1.28.13+2ca1a23   
ip-10-1-0-63.ap-southeast-2.compute.internal    Ready    worker                 3h34m   v1.28.13+2ca1a23   memory
[student@workstation ~]$ oc get machineset -n openshift-machine-api
NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           23h
cs220lws-cxw8p-memory-ap-southeast-2a   3         3         3       3           3h40m
cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           24h
[student@workstation ~]$ oc get pods -o wide 
NAME                         READY   STATUS    RESTARTS   AGE     IP           NODE                                            NOMINATED NODE   READINESS GATES
long-load-8647c68dcc-d4jhl   1/1     Running   0          8m37s   10.129.4.7   ip-10-1-0-189.ap-southeast-2.compute.internal   <none>           <none>
long-load-8647c68dcc-d9sm8   1/1     Running   0          8m37s   10.130.4.6   ip-10-1-0-35.ap-southeast-2.compute.internal    <none>           <none>
long-load-8647c68dcc-h828n   1/1     Running   0          152m    10.128.4.6   ip-10-1-0-63.ap-southeast-2.compute.internal    <none>           <none>
long-load-8647c68dcc-q9zwr   0/1     Pending   0          8m37s   <none>       <none>                                          <none>           <none>
[student@workstation ~]$ oc get hpa
NAME        REFERENCE              TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
long-load   Deployment/long-load   9%/2%     1         4         4          123m
[student@workstation ~]$ oc get machineautoscalers -n openshift-machine-api 
NAME                                    REF KIND     REF NAME                                MIN   MAX   AGE
cs220lws-cxw8p-memory-ap-southeast-2a   MachineSet   cs220lws-cxw8p-memory-ap-southeast-2a   2     3     21m
[student@workstation ~]$ 
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
long-load-8647c68dcc-d4jhl   23m          68Mi            
long-load-8647c68dcc-d9sm8   1m           55Mi            
long-load-8647c68dcc-h828n   31m          93Mi            
[student@workstation ~]$ oc get pods -o wide 
NAME                         READY   STATUS    RESTARTS   AGE    IP           NODE                                            NOMINATED NODE   READINESS GATES
long-load-8647c68dcc-d4jhl   1/1     Running   0          14m    10.129.4.7   ip-10-1-0-189.ap-southeast-2.compute.internal   <none>           <none>
long-load-8647c68dcc-d9sm8   1/1     Running   0          14m    10.130.4.6   ip-10-1-0-35.ap-southeast-2.compute.internal    <none>           <none>
long-load-8647c68dcc-h828n   1/1     Running   0          158m   10.128.4.6   ip-10-1-0-63.ap-southeast-2.compute.internal    <none>           <none>
long-load-8647c68dcc-q9zwr   0/1     Pending   0          14m    <none>       <none>                                          <none>           <none>
[student@workstation ~]$ oc get machinesets -A 
NAMESPACE               NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           24h
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a   3         3         3       3           3h47m
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           24h
[student@workstation ~]$ oc get machines -A | grep memory 
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a-2pcw4   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   15m
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a-ltvjm   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   103m
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a-np7l9   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   3h47m
[student@workstation ~]$ 
[student@workstation ~]$ oc get machinesets -A 
NAMESPACE               NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           24h
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a   3         3         3       3           3h48m
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           24h
[student@workstation ~]$ oc get machines -A | grep memory 
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a-2pcw4   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   15m
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a-ltvjm   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   104m
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a-np7l9   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   3h48m
[student@workstation ~]$ oc get hpa
NAME        REFERENCE              TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
long-load   Deployment/long-load   0%/2%     1         4         4          128m
[student@workstation ~]$ watch -d oc get hpa
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
[student@workstation ~]$ oc get machines -A | grep memory 
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a-2pcw4   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   18m
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a-ltvjm   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   106m
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a-np7l9   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   3h50m
[student@workstation ~]$ watch -d oc get hpa
[student@workstation ~]$ oc get pods 
NAME                         READY   STATUS    RESTARTS   AGE
long-load-8647c68dcc-h828n   1/1     Running   0          163m
[student@workstation ~]$ oc get pods -o wide 
NAME                         READY   STATUS    RESTARTS   AGE    IP           NODE                                           NOMINATED NODE   READINESS GATES
long-load-8647c68dcc-h828n   1/1     Running   0          163m   10.128.4.6   ip-10-1-0-63.ap-southeast-2.compute.internal   <none>           <none>
[student@workstation ~]$ oc get machinesets -n openshift-machine-api 
NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           24h
cs220lws-cxw8p-memory-ap-southeast-2a   3         3         3       3           3h51m
cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           24h
[student@workstation ~]$ oc get machines -n openshift-machine-api  | grep memory 
cs220lws-cxw8p-memory-ap-southeast-2a-2pcw4   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   20m
cs220lws-cxw8p-memory-ap-southeast-2a-ltvjm   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   108m
cs220lws-cxw8p-memory-ap-southeast-2a-np7l9   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   3h52m
[student@workstation ~]$ watch -d oc get machinesets -n openshift-machine-api 
[student@workstation ~]$ oc get machines -n openshift-machine-api  | grep memory 
cs220lws-cxw8p-memory-ap-southeast-2a-2pcw4   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   20m
cs220lws-cxw8p-memory-ap-southeast-2a-ltvjm   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   109m
cs220lws-cxw8p-memory-ap-southeast-2a-np7l9   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   3h53m
[student@workstation ~]$ watch -d oc get machinesets -n openshift-machine-api 
[student@workstation ~]$ oc get machinesets -n openshift-machine-api 
NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           24h
cs220lws-cxw8p-memory-ap-southeast-2a   2         2         2       2           4h2m
cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           24h
[student@workstation ~]$ oc get machines -n openshift-machine-api  | grep memory 
cs220lws-cxw8p-memory-ap-southeast-2a-2pcw4   Deleting   r5a.xlarge   ap-southeast-2   ap-southeast-2a   30m
cs220lws-cxw8p-memory-ap-southeast-2a-ltvjm   Running    r5a.xlarge   ap-southeast-2   ap-southeast-2a   118m
cs220lws-cxw8p-memory-ap-southeast-2a-np7l9   Running    r5a.xlarge   ap-southeast-2   ap-southeast-2a   4h2m
[student@workstation ~]$ 
[student@workstation ~]$ watch -d oc get machines -n openshift-machine-api  | grep memory 

[student@workstation ~]$ watch -d 'oc get machines -n openshift-machine-api  | grep memory'
[student@workstation ~]$ oc get machines -n openshift-machine-api  | grep memory 
cs220lws-cxw8p-memory-ap-southeast-2a-ltvjm   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   119m
cs220lws-cxw8p-memory-ap-southeast-2a-np7l9   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   4h3m
[student@workstation ~]$ oc delete project pod-scheduling 
project.project.openshift.io "pod-scheduling" deleted
[student@workstation ~]$ rosa list machinepools -c cs220lws
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS             TAINTS                               AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
memory  Yes          2-3       r5a.xlarge     workload=memory    memory-optimized=32GiB:NoSchedule    ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
worker  No           2         m5.xlarge                                                              ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ rosa delete machinepool -c cs220lws memory
? Are you sure you want to delete machine pool 'memory' on cluster 'cs220lws'? Yes
I: Successfully deleted machine pool 'memory' from cluster 'cs220lws'
[student@workstation ~]$ 

