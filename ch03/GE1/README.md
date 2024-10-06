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

========================================================================================= 2nd TERMINAL ============================================================================================================
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
[student@workstation ~]$ rosa describe cluster -c cs220lws | grep API 
API URL:                    https://api.cs220lws.nw83.p1.openshiftapps.com:6443
[student@workstation ~]$ oc login -u cluster-admin -p Redhattraining123 https://api.cs220lws.nw83.p1.openshiftapps.com:6443 
Login successful.

You have access to 100 projects, the list has been suppressed. You can list all projects with 'oc projects'

Using project "default".
[student@workstation ~]$ oc whoami -c 
default/api-cs220lws-nw83-p1-openshiftapps-com:6443/cluster-admin
[student@workstation ~]$ 
[student@workstation ~]$ oc get csv -n openshift-logging 
NAME                                       DISPLAY                  VERSION            REPLACES                                   PHASE
observability-operator.v0.4.0              Observability Operator   0.4.0              observability-operator.v0.3.5              Succeeded
route-monitor-operator.v0.1.679-g9a607b8   Route Monitor Operator   0.1.679-g9a607b8   route-monitor-operator.v0.1.677-gbf6ebed   Succeeded
[student@workstation ~]$ wget https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/configure-logs/policy.json
--2024-10-06 13:44:48--  https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/configure-logs/policy.json
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.108.133, 185.199.109.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 436 [text/plain]
Saving to: ‘policy.json’

policy.json                                 100%[========================================================================================>]     436  --.-KB/s    in 0s      

2024-10-06 13:44:49 (22.8 MB/s) - ‘policy.json’ saved [436/436]

[student@workstation ~]$ cat polic
cat: polic: No such file or directory
[student@workstation ~]$ cat policy.json 
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:DescribeLogGroups",
                "logs:DescribeLogStreams",
                "logs:PutLogEvents",
                "logs:PutRetentionPolicy"
            ],
            "Resource": "arn:aws:logs:*:*:*"
        }
    ]
}
[student@workstation ~]$ complete -C '/usr/local/sbin/aws_completer' aws 
[student@workstation ~]$ aws iabash: /usr/local/sbin/aws_completer: No such file or directory
^C
[student@workstation ~]$ complete -C '/usr/local/bin/aws_completer' aws 
[student@workstation ~]$ aws iam create-policy --policy-name cs220lws-RosaCloudWatch --policy-document file://policy.json --query Policy.Arn --output text 
arn:aws:iam::210940124124:policy/cs220lws-RosaCloudWatch
[student@workstation ~]$ POL_ARN="arn:aws:iam::210940124124:policy/cs220lws-RosaCloudWatch"
[student@workstation ~]$ echo $POL_ARN
arn:aws:iam::210940124124:policy/cs220lws-RosaCloudWatch
[student@workstation ~]$ aws iam list-open-id-connect-providers 
{
    "OpenIDConnectProviderList": [
        {
            "Arn": "arn:aws:iam::210940124124:oidc-provider/cs220lws-oidc-i8e4.s3.ap-southeast-2.amazonaws.com"
        }
    ]
}
[student@workstation ~]$ rosa describe cluster -c cs220lws | grep OIDC
OIDC Endpoint URL:          https://cs220lws-oidc-i8e4.s3.ap-southeast-2.amazonaws.com (Unmanaged)
[student@workstation ~]$ wget https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/configure-logs/trust-policy.json
--2024-10-06 13:51:57--  https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/configure-logs/trust-policy.json
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.109.133, 185.199.110.133, 185.199.111.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 436 [text/plain]
Saving to: ‘trust-policy.json’

trust-policy.json                           100%[========================================================================================>]     436  --.-KB/s    in 0s      

2024-10-06 13:51:58 (28.4 MB/s) - ‘trust-policy.json’ saved [436/436]

[student@workstation ~]$ cat trust-policy.json 
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Federated": "<CHANGE_ME>"
            },
            "Action": "sts:AssumeRoleWithWebIdentity",
            "Condition": {
                "StringEquals": {
                    "<CHANGE_ME>:sub": "system:serviceaccount:openshift-logging:logcollector"
                }
            }
        }
    ]
}
[student@workstation ~]$ vim trust-policy.json 
[student@workstation ~]$ vim trust-policy.json 
[student@workstation ~]$ cat trust-policy.json 
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Federated": "arn:aws:iam::210940124124:oidc-provider/cs220lws-oidc-i8e4.s3.ap-southeast-2.amazonaws.com"
            },
            "Action": "sts:AssumeRoleWithWebIdentity",
            "Condition": {
                "StringEquals": {
                    "cs220lws-oidc-i8e4.s3.ap-southeast-2.amazonaws.com:sub": "system:serviceaccount:openshift-logging:logcollector"
                }
            }
        }
    ]
}
[student@workstation ~]$ aws iam create-role --role-name c220lws-RosaCloudWatch --assume-role-policy-document file://trust-policy.json --query "Role.Arn" --output text 
arn:aws:iam::210940124124:role/c220lws-RosaCloudWatch
[student@workstation ~]$ ROLE_ARN="arn:aws:iam::210940124124:role/c220lws-RosaCloudWatch"
[student@workstation ~]$ echo $ROLE_ARN 
arn:aws:iam::210940124124:role/c220lws-RosaCloudWatch
[student@workstation ~]$ aws iam attach-role-policy --role-name cs220lws-RosaCloudWatch --policy-arn $POL_ARN

An error occurred (NoSuchEntity) when calling the AttachRolePolicy operation: The role with name cs220lws-RosaCloudWatch cannot be found.
[student@workstation ~]$ 
[student@workstation ~]$ aws iam list-role
list-role-policies  list-roles          list-role-tags      
[student@workstation ~]$ aws iam list-role
list-role-policies  list-roles          list-role-tags      
[student@workstation ~]$ aws iam list-roles | grep c220lws
            "RoleName": "c220lws-RosaCloudWatch",
            "Arn": "arn:aws:iam::210940124124:role/c220lws-RosaCloudWatch",
[student@workstation ~]$ aws iam delete-role
delete-role                       delete-role-permissions-boundary  delete-role-policy                
[student@workstation ~]$ aws iam delete-role --help 

usage: aws [options] <command> <subcommand> [<subcommand> ...] [parameters]
To see help text, you can run:

  aws help
  aws <command> help
  aws <command> <subcommand> help

aws: error: the following arguments are required: --role-name

[student@workstation ~]$ aws iam delete-role --role-name c220lws-RosaCloudWatch
[student@workstation ~]$ aws iam create-role --role-name cs220lws-RosaCloudWatch --assume-role-policy-document file://trust-policy.json --query "Role.Arn" --output text 
arn:aws:iam::210940124124:role/cs220lws-RosaCloudWatch
[student@workstation ~]$ unset $ROLE_ARN
bash: unset: `arn:aws:iam::210940124124:role/c220lws-RosaCloudWatch': not a valid identifier
[student@workstation ~]$ ROLE_ARN="arn:aws:iam::210940124124:role/cs220lws-RosaCloudWatch"
[student@workstation ~]$ aws iam attach-role-policy --role-name cs220lws-RosaCloudWatch --policy-arn $POL_ARN
[student@workstation ~]$ wget https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/configure-logs/subscription.yaml
--2024-10-06 14:00:02--  https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/configure-logs/subscription.yaml
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.108.133, 185.199.109.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 574 [text/plain]
Saving to: ‘subscription.yaml’

subscription.yaml                           100%[========================================================================================>]     574  --.-KB/s    in 0s      

2024-10-06 14:00:03 (37.6 MB/s) - ‘subscription.yaml’ saved [574/574]

[student@workstation ~]$ cat subscription.yaml 
---
apiVersion: v1
kind: List
metadata: {}
items:
  - apiVersion: operators.coreos.com/v1
    kind: OperatorGroup
    metadata:
      name: cluster-logging
      namespace: openshift-logging
    spec:
      targetNamespaces:
        - openshift-logging
  - apiVersion: operators.coreos.com/v1alpha1
    kind: Subscription
    metadata:
      name: cluster-logging
      namespace: openshift-logging
    spec:
      channel: "stable"
      installPlanApproval: Automatic
      name: cluster-logging
      source: redhat-operators
      sourceNamespace: openshift-marketplace
[student@workstation ~]$ oc apply -f subscription.yaml 
operatorgroup.operators.coreos.com/cluster-logging created
subscription.operators.coreos.com/cluster-logging created
[student@workstation ~]$ oc get csv -n openshift-logging 
NAME                                       DISPLAY                  VERSION            REPLACES                                   PHASE
observability-operator.v0.4.0              Observability Operator   0.4.0              observability-operator.v0.3.5              Succeeded
route-monitor-operator.v0.1.679-g9a607b8   Route Monitor Operator   0.1.679-g9a607b8   route-monitor-operator.v0.1.677-gbf6ebed   Succeeded
[student@workstation ~]$ watch -d oc get csv -n openshift-logging 
[student@workstation ~]$ oc project openshift-logging 
Now using project "openshift-logging" on server "https://api.cs220lws.nw83.p1.openshiftapps.com:6443".
[student@workstation ~]$ oc get all
Warning: apps.openshift.io/v1 DeploymentConfig is deprecated in v4.14+, unavailable in v4.10000+
NAME                                       TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
service/cluster-logging-operator-metrics   ClusterIP   172.30.129.243   <none>        8686/TCP   0s
[student@workstation ~]$ watch -d oc get csv -n openshift-logging 
[student@workstation ~]$ oc get csv -n openshift-logging 
NAME                                       DISPLAY                     VERSION            REPLACES                                   PHASE
cluster-logging.v5.9.7                     Red Hat OpenShift Logging   5.9.7              cluster-logging.v5.9.6                     Succeeded
observability-operator.v0.4.0              Observability Operator      0.4.0              observability-operator.v0.3.5              Succeeded
route-monitor-operator.v0.1.679-g9a607b8   Route Monitor Operator      0.1.679-g9a607b8   route-monitor-operator.v0.1.677-gbf6ebed   Succeeded
[student@workstation ~]$ oc get all
Warning: apps.openshift.io/v1 DeploymentConfig is deprecated in v4.14+, unavailable in v4.10000+
NAME                                            READY   STATUS    RESTARTS   AGE
pod/cluster-logging-operator-774844f649-d5l65   1/1     Running   0          34s

NAME                                       TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
service/cluster-logging-operator-metrics   ClusterIP   172.30.129.243   <none>        8686/TCP   38s

NAME                                       READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/cluster-logging-operator   1/1     1            1           35s

NAME                                                  DESIRED   CURRENT   READY   AGE
replicaset.apps/cluster-logging-operator-774844f649   1         1         1       35s
[student@workstation ~]$ 
[student@workstation ~]$ echo $ROLE_ARN
arn:aws:iam::210940124124:role/cs220lws-RosaCloudWatch
[student@workstation ~]$ 
[student@workstation ~]$ oc create secret generic cloud-watch-credentials -n openshift-logging --from-literal "role_arn=$ROLE_ARN"
secret/cloud-watch-credentials created
[student@workstation ~]$ oc delete secret/cloud-watch-credentials
secret "cloud-watch-credentials" deleted
[student@workstation ~]$ oc create secret generic cloudwatch-credentials -n openshift-logging --from-literal "role_arn=$ROLE_ARN"
secret/cloudwatch-credentials created
[student@workstation ~]$ 
[student@workstation ~]$ oc extract secret/cloudwatch-credentials --to -
# role_arn
arn:aws:iam::210940124124:role/cs220lws-RosaCloudWatch
[student@workstation ~]$ wget https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/configure-logs/vector-conf.yaml
--2024-10-06 14:06:18--  https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/configure-logs/vector-conf.yaml
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.110.133, 185.199.111.133, 185.199.108.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.110.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 428 [text/plain]
Saving to: ‘vector-conf.yaml’

vector-conf.yaml                            100%[========================================================================================>]     428  --.-KB/s    in 0s      

2024-10-06 14:06:19 (23.9 MB/s) - ‘vector-conf.yaml’ saved [428/428]

[student@workstation ~]$ cat vector-conf.yaml 
---
apiVersion: "logging.openshift.io/v1"
kind: ClusterLogForwarder
metadata:
  name: instance
  namespace: openshift-logging
spec:
  outputs:
    - name: cw
      type: cloudwatch
      cloudwatch:
        region: <CHANGE_ME>
      secret:
        name: cloudwatch-credentials
  pipelines:
    - name: to-cloudwatch
      inputRefs:
        - infrastructure
        - audit
        - application
      outputRefs:
        - cw
[student@workstation ~]$ vim vector-conf.yaml 
[student@workstation ~]$ cat vector-conf.yaml 
---
apiVersion: "logging.openshift.io/v1"
kind: ClusterLogForwarder
metadata:
  name: instance
  namespace: openshift-logging
spec:
  outputs:
    - name: cw
      type: cloudwatch
      cloudwatch:
        region: ap-southeast-2
      secret:
        name: cloudwatch-credentials
  pipelines:
    - name: to-cloudwatch
      inputRefs:
        - infrastructure
        - audit
        - application
      outputRefs:
        - cw
[student@workstation ~]$ oc apply -f vector-conf.yaml
clusterlogforwarder.logging.openshift.io/instance created
[student@workstation ~]$ oc api-resources | grep Forward
clusterlogforwarders                  clf                                                                                    logging.openshift.io/v1                         true         ClusterLogForwarder
splunkforwarders                                                                                                             splunkforwarder.managed.openshift.io/v1alpha1   true         SplunkForwarder
[student@workstation ~]$ wget https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/configure-logs/logging-conf.yaml
--2024-10-06 14:11:06--  https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/configure-logs/logging-conf.yaml
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.109.133, 185.199.108.133, 185.199.111.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 195 [text/plain]
Saving to: ‘logging-conf.yaml’

logging-conf.yaml                           100%[========================================================================================>]     195  --.-KB/s    in 0s      

2024-10-06 14:11:07 (4.14 MB/s) - ‘logging-conf.yaml’ saved [195/195]

[student@workstation ~]$ cat logging-conf.yaml 
---
apiVersion: logging.openshift.io/v1
kind: ClusterLogging
metadata:
  name: instance
  namespace: openshift-logging
spec:
  collection:
    logs:
      type: vector
  managementState: Managed
[student@workstation ~]$ 
[student@workstation ~]$ oc apply -f logging-conf.yaml 
clusterlogging.logging.openshift.io/instance created
[student@workstation ~]$ oc get all 
Warning: apps.openshift.io/v1 DeploymentConfig is deprecated in v4.14+, unavailable in v4.10000+
NAME                                            READY   STATUS    RESTARTS   AGE
pod/cluster-logging-operator-774844f649-d5l65   1/1     Running   0          10m
pod/collector-8pb4b                             1/1     Running   0          19s
pod/collector-cdl8w                             1/1     Running   0          18s
pod/collector-gsnkh                             1/1     Running   0          19s
pod/collector-sjcgl                             1/1     Running   0          19s
pod/collector-sl8pt                             1/1     Running   0          18s

NAME                                       TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)     AGE
service/cluster-logging-operator-metrics   ClusterIP   172.30.129.243   <none>        8686/TCP    10m
service/collector                          ClusterIP   172.30.211.245   <none>        24231/TCP   20s

NAME                       DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR            AGE
daemonset.apps/collector   5         5         5       5            5           kubernetes.io/os=linux   20s

NAME                                       READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/cluster-logging-operator   1/1     1            1           10m

NAME                                                  DESIRED   CURRENT   READY   AGE
replicaset.apps/cluster-logging-operator-774844f649   1         1         1       10m
[student@workstation ~]$ oc get pods -o wide 
NAME                                        READY   STATUS    RESTARTS   AGE   IP             NODE                                            NOMINATED NODE   READINESS GATES
cluster-logging-operator-774844f649-d5l65   1/1     Running   0          11m   10.131.0.151   ip-10-1-0-62.ap-southeast-2.compute.internal    <none>           <none>
collector-8pb4b                             1/1     Running   0          42s   10.130.0.141   ip-10-1-0-242.ap-southeast-2.compute.internal   <none>           <none>
collector-cdl8w                             1/1     Running   0          41s   10.129.0.79    ip-10-1-0-223.ap-southeast-2.compute.internal   <none>           <none>
collector-gsnkh                             1/1     Running   0          42s   10.128.0.38    ip-10-1-0-121.ap-southeast-2.compute.internal   <none>           <none>
collector-sjcgl                             1/1     Running   0          42s   10.128.2.19    ip-10-1-0-247.ap-southeast-2.compute.internal   <none>           <none>
collector-sl8pt                             1/1     Running   0          41s   10.131.0.153   ip-10-1-0-62.ap-southeast-2.compute.internal    <none>           <none>
[student@workstation ~]$ oc get nodes 
NAME                                            STATUS   ROLES                  AGE   VERSION
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   25h   v1.28.13+2ca1a23
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           25h   v1.28.13+2ca1a23
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   25h   v1.28.13+2ca1a23
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   25h   v1.28.13+2ca1a23
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 25h   v1.28.13+2ca1a23
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           25h   v1.28.13+2ca1a23
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 25h   v1.28.13+2ca1a23
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
[student@workstation ~]$ oc get pods 
NAME                                        READY   STATUS    RESTARTS   AGE
cluster-logging-operator-774844f649-d5l65   1/1     Running   0          14m
collector-8pb4b                             1/1     Running   0          3m46s
collector-cdl8w                             1/1     Running   0          3m45s
collector-gsnkh                             1/1     Running   0          3m46s
collector-sjcgl                             1/1     Running   0          3m46s
collector-sl8pt                             1/1     Running   0          3m45s
[student@workstation ~]$ oc adm top pods 
NAME                                        CPU(cores)   MEMORY(bytes)   
cluster-logging-operator-774844f649-d5l65   1m           34Mi            
collector-8pb4b                             19m          722Mi           
collector-cdl8w                             41m          642Mi           
collector-gsnkh                             29m          593Mi           
collector-sjcgl                             3m           325Mi           
collector-sl8pt                             5m           363Mi           
[student@workstation ~]$ oc adm top pods --sum 
NAME                                        CPU(cores)   MEMORY(bytes)   
cluster-logging-operator-774844f649-d5l65   1m           34Mi            
collector-8pb4b                             19m          718Mi           
collector-cdl8w                             29m          642Mi           
collector-gsnkh                             30m          591Mi           
collector-sjcgl                             3m           318Mi           
collector-sl8pt                             5m           351Mi           
                                            ________     ________        
                                            87m          2657Mi          
[student@workstation ~]$ 

