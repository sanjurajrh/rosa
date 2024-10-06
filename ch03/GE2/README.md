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

============================================================================= 2nd TERMINAL ========================================================================================================================
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

[student@workstation ~]$ oc whoami -c 
openshift-logging/api-cs220lws-nw83-p1-openshiftapps-com:6443/cluster-admin
[student@workstation ~]$ 
[student@workstation ~]$ oc get pods -n openshift-logging 
NAME                                        READY   STATUS    RESTARTS   AGE
cluster-logging-operator-774844f649-d5l65   1/1     Running   0          18m
collector-8pb4b                             1/1     Running   0          7m57s
collector-cdl8w                             1/1     Running   0          7m56s
collector-gsnkh                             1/1     Running   0          7m57s
collector-sjcgl                             1/1     Running   0          7m57s
collector-sl8pt                             1/1     Running   0          7m56s
[student@workstation ~]$ oc project 
Using project "openshift-logging" on server "https://api.cs220lws.nw83.p1.openshiftapps.com:6443".
[student@workstation ~]$ aws logs describe-log-groups --log-group-name-prefix cs220lws
{
    "logGroups": [
        {
            "logGroupName": "cs220lws-cxw8p.audit",
            "creationTime": 1728238319062,
            "metricFilterCount": 0,
            "arn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.audit:*",
            "storedBytes": 0,
            "logGroupClass": "STANDARD",
            "logGroupArn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.audit"
        },
        {
            "logGroupName": "cs220lws-cxw8p.infrastructure",
            "creationTime": 1728238319441,
            "metricFilterCount": 0,
            "arn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.infrastructure:*",
            "storedBytes": 0,
            "logGroupClass": "STANDARD",
            "logGroupArn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.infrastructure"
        }
    ]
}
[student@workstation ~]$ complete -C '/usr/local/bin/aws_completer' aws 
[student@workstation ~]$ aws logs describe-log-groups --log-group-name-prefix cs220lws 
{
    "logGroups": [
        {
            "logGroupName": "cs220lws-cxw8p.audit",
            "creationTime": 1728238319062,
            "metricFilterCount": 0,
            "arn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.audit:*",
            "storedBytes": 0,
            "logGroupClass": "STANDARD",
            "logGroupArn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.audit"
        },
        {
            "logGroupName": "cs220lws-cxw8p.infrastructure",
            "creationTime": 1728238319441,
            "metricFilterCount": 0,
            "arn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.infrastructure:*",
            "storedBytes": 0,
            "logGroupClass": "STANDARD",
            "logGroupArn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.infrastructure"
        }
    ]
}
[student@workstation ~]$ wget https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/query-logs/resources.yaml
--2024-10-06 14:22:23--  https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/query-logs/resources.yaml
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.108.133, 185.199.110.133, 185.199.109.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.108.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6843 (6.7K) [text/plain]
Saving to: ‘resources.yaml’

resources.yaml                                       100%[=====================================================================================================================>]   6.68K  --.-KB/s    in 0s      

2024-10-06 14:22:24 (94.9 MB/s) - ‘resources.yaml’ saved [6843/6843]

[student@workstation ~]$ grep Kind resources.yaml 
[student@workstation ~]$ grep kind resources.yaml 
kind: List
    kind: Project
    kind: PersistentVolumeClaim
    kind: Secret
    kind: Deployment
    kind: Service
    kind: Deployment
    kind: Service
    kind: Route
        kind: Service
    kind: Deployment
[student@workstation ~]$ oc apply -f resources.yaml 
project.project.openshift.io/query-logs created
persistentvolumeclaim/mariadb created
secret/mariadb created
deployment.apps/mariadb created
service/mariadb created
deployment.apps/famous-quotes created
service/famous-quotes created
route.route.openshift.io/famous-quotes created
deployment.apps/need-20gib created
[student@workstation ~]$ oc project query-logs
Now using project "query-logs" on server "https://api.cs220lws.nw83.p1.openshiftapps.com:6443".
[student@workstation ~]$ oc get pods 
NAME                             READY   STATUS             RESTARTS   AGE
famous-quotes-7c6f59b79d-kfgnx   0/1     ImagePullBackOff   0          26s
mariadb-9796877df-zgcdx          0/1     Running            0          27s
need-20gib-58775b7dbf-qtd5p      0/1     Pending            0          25s
[student@workstation ~]$ oc get pods 
NAME                             READY   STATUS         RESTARTS   AGE
famous-quotes-7c6f59b79d-kfgnx   0/1     ErrImagePull   0          35s
mariadb-9796877df-zgcdx          0/1     Running        0          36s
need-20gib-58775b7dbf-qtd5p      0/1     Pending        0          34s
[student@workstation ~]$ 
[student@workstation ~]$ oc get pods 
NAME                             READY   STATUS             RESTARTS   AGE
famous-quotes-7c6f59b79d-kfgnx   0/1     ImagePullBackOff   0          42s
mariadb-9796877df-zgcdx          1/1     Running            0          43s
need-20gib-58775b7dbf-qtd5p      0/1     Pending            0          41s
[student@workstation ~]$ 
[student@workstation ~]$ oc project query-logs
Already on project "query-logs" on server "https://api.cs220lws.nw83.p1.openshiftapps.com:6443".
[student@workstation ~]$ oc get pods 
NAME                             READY   STATUS             RESTARTS   AGE
famous-quotes-7c6f59b79d-kfgnx   0/1     ImagePullBackOff   0          51s
mariadb-9796877df-zgcdx          1/1     Running            0          52s
need-20gib-58775b7dbf-qtd5p      0/1     Pending            0          50s
[student@workstation ~]$ oc get all
Warning: apps.openshift.io/v1 DeploymentConfig is deprecated in v4.14+, unavailable in v4.10000+
NAME                                 READY   STATUS         RESTARTS   AGE
pod/famous-quotes-7c6f59b79d-kfgnx   0/1     ErrImagePull   0          61s
pod/mariadb-9796877df-zgcdx          1/1     Running        0          62s
pod/need-20gib-58775b7dbf-qtd5p      0/1     Pending        0          60s

NAME                    TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
service/famous-quotes   ClusterIP   172.30.132.100   <none>        8000/TCP   61s
service/mariadb         ClusterIP   172.30.144.58    <none>        3306/TCP   62s

NAME                            READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/famous-quotes   0/1     1            0           61s
deployment.apps/mariadb         1/1     1            1           62s
deployment.apps/need-20gib      0/1     1            0           60s

NAME                                       DESIRED   CURRENT   READY   AGE
replicaset.apps/famous-quotes-7c6f59b79d   1         1         0       61s
replicaset.apps/mariadb-9796877df          1         1         1       62s
replicaset.apps/need-20gib-58775b7dbf      1         1         0       60s

NAME                                     HOST/PORT                                                          PATH   SERVICES        PORT   TERMINATION   WILDCARD
route.route.openshift.io/famous-quotes   famous-quotes-query-logs.apps.cs220lws.nw83.p1.openshiftapps.com          famous-quotes   8000   edge          None
[student@workstation ~]$ oc set image deployment/famous-quotes famous-quotes=quay.io/redhattraining/famous-quotes:2.1
deployment.apps/famous-quotes image updated
[student@workstation ~]$ oc get pods 
NAME                             READY   STATUS    RESTARTS   AGE
famous-quotes-5b76495774-frrl8   1/1     Running   0          3s
mariadb-9796877df-zgcdx          1/1     Running   0          22m
need-20gib-58775b7dbf-qtd5p      0/1     Pending   0          22m
[student@workstation ~]$ oc scale deployment famous-quotes --replicas 6
deployment.apps/famous-quotes scaled
[student@workstation ~]$ oc get pods 
NAME                             READY   STATUS              RESTARTS   AGE
famous-quotes-5b76495774-5np4h   0/1     ContainerCreating   0          2s
famous-quotes-5b76495774-c9j67   1/1     Running             0          2s
famous-quotes-5b76495774-ckzqf   0/1     ContainerCreating   0          2s
famous-quotes-5b76495774-frrl8   1/1     Running             0          29s
famous-quotes-5b76495774-h6mqh   1/1     Running             0          2s
famous-quotes-5b76495774-hjrdx   0/1     ContainerCreating   0          2s
mariadb-9796877df-zgcdx          1/1     Running             0          22m
need-20gib-58775b7dbf-qtd5p      0/1     Pending             0          22m
[student@workstation ~]$ oc get pods 
NAME                             READY   STATUS              RESTARTS   AGE
famous-quotes-5b76495774-5np4h   0/1     ContainerCreating   0          18s
famous-quotes-5b76495774-c9j67   1/1     Running             0          18s
famous-quotes-5b76495774-ckzqf   0/1     ContainerCreating   0          18s
famous-quotes-5b76495774-frrl8   1/1     Running             0          45s
famous-quotes-5b76495774-h6mqh   1/1     Running             0          18s
famous-quotes-5b76495774-hjrdx   0/1     ContainerCreating   0          18s
mariadb-9796877df-zgcdx          1/1     Running             0          22m
need-20gib-58775b7dbf-qtd5p      0/1     Pending             0          22m
[student@workstation ~]$ oc get pods 
NAME                             READY   STATUS    RESTARTS   AGE
famous-quotes-5b76495774-5np4h   1/1     Running   0          31s
famous-quotes-5b76495774-c9j67   1/1     Running   0          31s
famous-quotes-5b76495774-ckzqf   1/1     Running   0          31s
famous-quotes-5b76495774-frrl8   1/1     Running   0          58s
famous-quotes-5b76495774-h6mqh   1/1     Running   0          31s
famous-quotes-5b76495774-hjrdx   1/1     Running   0          31s
mariadb-9796877df-zgcdx          1/1     Running   0          23m
need-20gib-58775b7dbf-qtd5p      0/1     Pending   0          23m
[student@workstation ~]$ oc get nodes 
NAME                                            STATUS   ROLES                  AGE   VERSION
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   26h   v1.28.13+2ca1a23
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           25h   v1.28.13+2ca1a23
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   26h   v1.28.13+2ca1a23
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   26h   v1.28.13+2ca1a23
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 26h   v1.28.13+2ca1a23
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           25h   v1.28.13+2ca1a23
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 26h   v1.28.13+2ca1a23
[student@workstation ~]$ oc delete deployment famous-quotes 
deployment.apps "famous-quotes" deleted
[student@workstation ~]$ oc delete project query-logs 
project.project.openshift.io "query-logs" deleted
[student@workstation ~]$ oc delete clusterlogging instance -n openshift-logging
clusterlogging.logging.openshift.io "instance" deleted
[student@workstation ~]$ oc delete clusterlogforwarder instance -n openshift-logging
clusterlogforwarder.logging.openshift.io "instance" deleted
[student@workstation ~]$ oc delete secret cloudwatch-credentials -n openshift-logging
secret "cloudwatch-credentials" deleted
[student@workstation ~]$ oc delete subscription cluster-logging -n openshift-logging
subscription.operators.coreos.com "cluster-logging" deleted
[student@workstation ~]$ oc get csv -n openshift-logging
NAME                                       DISPLAY                     VERSION            REPLACES                                   PHASE
cluster-logging.v5.9.7                     Red Hat OpenShift Logging   5.9.7              cluster-logging.v5.9.6                     Succeeded
observability-operator.v0.4.0              Observability Operator      0.4.0              observability-operator.v0.3.5              Succeeded
route-monitor-operator.v0.1.679-g9a607b8   Route Monitor Operator      0.1.679-g9a607b8   route-monitor-operator.v0.1.677-gbf6ebed   Succeeded
[student@workstation ~]$ 
[student@workstation ~]$ oc delete csv cluster-logging.v5.9.7 -n openshift-logging
clusterserviceversion.operators.coreos.com "cluster-logging.v5.9.7" deleted
[student@workstation ~]$ aws logs describe-log-groups --log-group-name-prefix cs220lws 
{
    "logGroups": [
        {
            "logGroupName": "cs220lws-cxw8p.application",
            "creationTime": 1728239025242,
            "metricFilterCount": 0,
            "arn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.application:*",
            "storedBytes": 0,
            "logGroupClass": "STANDARD",
            "logGroupArn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.application"
        },
        {
            "logGroupName": "cs220lws-cxw8p.audit",
            "creationTime": 1728238319062,
            "metricFilterCount": 0,
            "arn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.audit:*",
            "storedBytes": 0,
            "logGroupClass": "STANDARD",
            "logGroupArn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.audit"
        },
        {
            "logGroupName": "cs220lws-cxw8p.infrastructure",
            "creationTime": 1728238319441,
            "metricFilterCount": 0,
            "arn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.infrastructure:*",
            "storedBytes": 0,
            "logGroupClass": "STANDARD",
            "logGroupArn": "arn:aws:logs:ap-southeast-2:210940124124:log-group:cs220lws-cxw8p.infrastructure"
        }
    ]
}
[student@workstation ~]$ aws logs describe-log-groups --log-group-name-prefix cs220lws --query "logGroups[].logGroupName"
[
    "cs220lws-cxw8p.application",
    "cs220lws-cxw8p.audit",
    "cs220lws-cxw8p.infrastructure"
]
[student@workstation ~]$ aws logs delete-log-group --log-group-name cs220lws-cxw8p.application
[student@workstation ~]$ aws logs delete-log-group --log-group-name cs220lws-cxw8p.audit
[student@workstation ~]$ aws logs delete-log-group --log-group-name cs220lws-cxw8p.infrastructure
[student@workstation ~]$ echo $POL_ARN

[student@workstation ~]$ aws iam list-policies --output text --query "Policies[?PolicyName=='cs220lws-RosaCloudWatch'].Arn"
arn:aws:iam::210940124124:policy/cs220lws-RosaCloudWatch
[student@workstation ~]$ POL_ARN="arn:aws:iam::210940124124:policy/cs220lws-RosaCloudWatch"
[student@workstation ~]$ echo $POL_ARN
arn:aws:iam::210940124124:policy/cs220lws-RosaCloudWatch
[student@workstation ~]$ aws iam detach-role-policy --role-name cs220lws-RosaCloudWatch --policy-arn $POL_ARN
[student@workstation ~]$ aws iam delete-role --role-name cs220lws-RosaCloudWatch
[student@workstation ~]$ aws iam delete-policy --policy-arn $POL_ARN
[student@workstation ~]$ 

