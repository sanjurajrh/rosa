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


=============================================================================================== 2nd TERMINAL =====================================================================================================
[student@workstation ~]$ oc login -u cluster-admin -p Redhatatraining123 https://api.cs220lws.nw83.p1.openshiftapps.com:6443 
Login failed (401 Unauthorized)
Verify you have provided the correct credentials.
[student@workstation ~]$ 
[student@workstation ~]$ oc login -u cluster-admin -p Redhattraining123 https://api.cs220lws.nw83.p1.openshiftapps.com:6443 
Login successful.

You have access to 100 projects, the list has been suppressed. You can list all projects with 'oc projects'

Using project "default".
[student@workstation ~]$ oc get nodes -o wide 
NAME                                            STATUS   ROLES                  AGE   VERSION            INTERNAL-IP   EXTERNAL-IP   OS-IMAGE                                                       KERNEL-VERSION                 CONTAINER-RUNTIME
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   18h   v1.28.13+2ca1a23   10.1.0.121    <none>        Red Hat Enterprise Linux CoreOS 415.92.202409101905-0 (Plow)   5.14.0-284.84.1.el9_2.x86_64   cri-o://1.28.10-3.rhaos4.15.git368cd23.el9
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           17h   v1.28.13+2ca1a23   10.1.0.19     <none>        Red Hat Enterprise Linux CoreOS 415.92.202409101905-0 (Plow)   5.14.0-284.84.1.el9_2.x86_64   cri-o://1.28.10-3.rhaos4.15.git368cd23.el9
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   18h   v1.28.13+2ca1a23   10.1.0.223    <none>        Red Hat Enterprise Linux CoreOS 415.92.202409101905-0 (Plow)   5.14.0-284.84.1.el9_2.x86_64   cri-o://1.28.10-3.rhaos4.15.git368cd23.el9
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   18h   v1.28.13+2ca1a23   10.1.0.242    <none>        Red Hat Enterprise Linux CoreOS 415.92.202409101905-0 (Plow)   5.14.0-284.84.1.el9_2.x86_64   cri-o://1.28.10-3.rhaos4.15.git368cd23.el9
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 18h   v1.28.13+2ca1a23   10.1.0.247    <none>        Red Hat Enterprise Linux CoreOS 415.92.202409101905-0 (Plow)   5.14.0-284.84.1.el9_2.x86_64   cri-o://1.28.10-3.rhaos4.15.git368cd23.el9
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           17h   v1.28.13+2ca1a23   10.1.0.252    <none>        Red Hat Enterprise Linux CoreOS 415.92.202409101905-0 (Plow)   5.14.0-284.84.1.el9_2.x86_64   cri-o://1.28.10-3.rhaos4.15.git368cd23.el9
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 18h   v1.28.13+2ca1a23   10.1.0.62     <none>        Red Hat Enterprise Linux CoreOS 415.92.202409101905-0 (Plow)   5.14.0-284.84.1.el9_2.x86_64   cri-o://1.28.10-3.rhaos4.15.git368cd23.el9
[student@workstation ~]$ oc get machines -A 
NAMESPACE               NAME                                          PHASE     TYPE         REGION           ZONE              AGE
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a-ft65n    Running   r5.xlarge    ap-southeast-2   ap-southeast-2a   17h
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a-xvg4m    Running   r5.xlarge    ap-southeast-2   ap-southeast-2a   17h
openshift-machine-api   cs220lws-cxw8p-master-0                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   18h
openshift-machine-api   cs220lws-cxw8p-master-1                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   18h
openshift-machine-api   cs220lws-cxw8p-master-2                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   18h
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a-c7v9r   Running   m5.xlarge    ap-southeast-2   ap-southeast-2a   18h
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a-snvrx   Running   m5.xlarge    ap-southeast-2   ap-southeast-2a   18h
[student@workstation ~]$ oc describe machine cs220lws-cxw8p-master-0 -n openshift-machine-api 
Name:         cs220lws-cxw8p-master-0
Namespace:    openshift-machine-api
Labels:       machine.openshift.io/cluster-api-cluster=cs220lws-cxw8p
              machine.openshift.io/cluster-api-machine-role=master
              machine.openshift.io/cluster-api-machine-type=master
              machine.openshift.io/instance-type=m5.2xlarge
              machine.openshift.io/region=ap-southeast-2
              machine.openshift.io/zone=ap-southeast-2a
Annotations:  machine.openshift.io/instance-state: running
API Version:  machine.openshift.io/v1beta1
Kind:         Machine
Metadata:
  Creation Timestamp:  2024-10-05T16:31:50Z
  Finalizers:
    machine.machine.openshift.io
  Generation:  3
  Managed Fields:
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:labels:
          .:
          f:machine.openshift.io/cluster-api-cluster:
          f:machine.openshift.io/cluster-api-machine-role:
          f:machine.openshift.io/cluster-api-machine-type:
      f:spec:
        .:
        f:lifecycleHooks:
        f:metadata:
        f:providerSpec:
          .:
          f:value:
            .:
            f:ami:
              .:
              f:id:
            f:apiVersion:
            f:blockDevices:
            f:credentialsSecret:
              .:
              f:name:
            f:deviceIndex:
            f:iamInstanceProfile:
              .:
              f:id:
            f:instanceType:
            f:kind:
            f:loadBalancers:
            f:metadata:
              .:
              f:creationTimestamp:
            f:metadataServiceOptions:
            f:placement:
              .:
              f:availabilityZone:
              f:region:
            f:securityGroups:
            f:subnet:
              .:
              f:id:
            f:tags:
            f:userDataSecret:
              .:
              f:name:
    Manager:      cluster-bootstrap
    Operation:    Update
    Time:         2024-10-05T16:31:50Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:status:
    Manager:      cluster-bootstrap
    Operation:    Update
    Subresource:  status
    Time:         2024-10-05T16:31:50Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:annotations:
          .:
          f:machine.openshift.io/instance-state:
        f:finalizers:
          .:
          v:"machine.machine.openshift.io":
        f:labels:
          f:machine.openshift.io/instance-type:
          f:machine.openshift.io/region:
          f:machine.openshift.io/zone:
      f:spec:
        f:providerID:
    Manager:      machine-controller-manager
    Operation:    Update
    Time:         2024-10-05T16:38:35Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:spec:
        f:lifecycleHooks:
          f:preDrain:
            .:
            k:{"name":"EtcdQuorumOperator"}:
              .:
              f:name:
              f:owner:
    Manager:      cluster-etcd-operator
    Operation:    Update
    Time:         2024-10-05T16:38:37Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:ownerReferences:
          .:
          k:{"uid":"64093dbc-5d5b-49a5-8478-3fcfb715b264"}:
    Manager:      manager
    Operation:    Update
    Time:         2024-10-05T16:38:37Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:status:
        f:addresses:
        f:conditions:
        f:phase:
        f:providerStatus:
          .:
          f:conditions:
          f:instanceId:
          f:instanceState:
    Manager:      machine-controller-manager
    Operation:    Update
    Subresource:  status
    Time:         2024-10-05T16:38:42Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:status:
        f:lastUpdated:
        f:nodeRef:
    Manager:      nodelink-controller
    Operation:    Update
    Subresource:  status
    Time:         2024-10-05T17:13:10Z
  Owner References:
    API Version:           machine.openshift.io/v1
    Block Owner Deletion:  true
    Controller:            true
    Kind:                  ControlPlaneMachineSet
    Name:                  cluster
    UID:                   64093dbc-5d5b-49a5-8478-3fcfb715b264
  Resource Version:        70392
  UID:                     647b76f3-cffe-4bcf-9db1-6a40adc92995
Spec:
  Lifecycle Hooks:
    Pre Drain:
      Name:   EtcdQuorumOperator
      Owner:  clusteroperator/etcd
  Metadata:
  Provider ID:  aws:///ap-southeast-2a/i-0eccb75468dbfcef2
  Provider Spec:
    Value:
      Ami:
        Id:         ami-0f45350e59d5513cb
      API Version:  machine.openshift.io/v1beta1
      Block Devices:
        Ebs:
          Encrypted:  true
          Iops:       0
          Kms Key:
            Arn:        
          Volume Size:  350
          Volume Type:  gp3
      Credentials Secret:
        Name:        aws-cloud-credentials
      Device Index:  0
      Iam Instance Profile:
        Id:           cs220lws-cxw8p-master-profile
      Instance Type:  m5.2xlarge
      Kind:           AWSMachineProviderConfig
      Load Balancers:
        Name:  cs220lws-cxw8p-int
        Type:  network
      Metadata:
        Creation Timestamp:  <nil>
      Metadata Service Options:
      Placement:
        Availability Zone:  ap-southeast-2a
        Region:             ap-southeast-2
      Security Groups:
        Filters:
          Name:  tag:Name
          Values:
            cs220lws-cxw8p-master-sg
      Subnet:
        Id:  subnet-0e9ab412dc0120842
      Tags:
        Name:   kubernetes.io/cluster/cs220lws-cxw8p
        Value:  owned
        Name:   red-hat-clustertype
        Value:  rosa
        Name:   red-hat-managed
        Value:  true
        Name:   redhattraining:course-sku
        Value:  CS220
        Name:   redhattraining:rosa-cluster-id
        Value:  cs220lws
      User Data Secret:
        Name:  master-user-data
Status:
  Addresses:
    Address:  10.1.0.121
    Type:     InternalIP
    Address:  ip-10-1-0-121.ap-southeast-2.compute.internal
    Type:     InternalDNS
    Address:  ip-10-1-0-121.ap-southeast-2.compute.internal
    Type:     Hostname
  Conditions:
    Last Transition Time:  2024-10-05T16:38:42Z
    Message:               Drain operation currently blocked by: [{Name:EtcdQuorumOperator Owner:clusteroperator/etcd}]
    Reason:                HookPresent
    Severity:              Warning
    Status:                False
    Type:                  Drainable
    Last Transition Time:  2024-10-05T16:38:35Z
    Status:                True
    Type:                  InstanceExists
    Last Transition Time:  2024-10-05T16:38:35Z
    Status:                True
    Type:                  Terminable
  Last Updated:            2024-10-05T17:13:10Z
  Node Ref:
    Kind:  Node
    Name:  ip-10-1-0-121.ap-southeast-2.compute.internal
    UID:   36ee37bd-8591-4243-99ac-4ab3d332899f
  Phase:   Running
  Provider Status:
    Conditions:
      Last Transition Time:  2024-10-05T16:38:35Z
      Message:               Machine successfully created
      Reason:                MachineCreationSucceeded
      Status:                True
      Type:                  MachineCreation
    Instance Id:             i-0eccb75468dbfcef2
    Instance State:          running
Events:                      <none>
[student@workstation ~]$ oc get machinesets -A
NAMESPACE               NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           18h
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           18h
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

[student@workstation ~]$ rosa list machinepools -c cs220lws
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS    TAINTS    AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
worker  No           2         m5.xlarge                          ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ aws ec2 describe-instances --output text --filters "Name=tag:redhattraining:rosa-cluster-id.Values=cs220lws" --query "Reservations[].Instances[].InstanceId"
[student@workstation ~]$ 
[student@workstation ~]$ aws ec2 describe-instances --output text --filters "Name=tag:redhattraining:rosa-cluster-id,Values=cs220lws" --query "Reservations[].Instances[].InstanceId"
i-005d00ae43dc717fb     i-056e20a47d81acbf6     i-0eccb75468dbfcef2     i-082c3da6aad966702     i-075f26be7d580d944     i-0a2240058618393f2     i-0e83a8a319ed709a4
[student@workstation ~]$ 
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
[student@workstation ~]$ oc whoami 
cluster-admin
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
[student@workstation ~]$ rosa list machinepools --cluster cs220lws
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS    TAINTS    AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
worker  No           2         m5.xlarge                          ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ oc get machinesets -A
NAMESPACE               NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           18h
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           19h
[student@workstation ~]$ oc describe machineset cs220lws-cxw8p-worker-ap-southeast-2a -n openshift-machine-api 
Name:         cs220lws-cxw8p-worker-ap-southeast-2a
Namespace:    openshift-machine-api
Labels:       hive.openshift.io/machine-pool=worker
              hive.openshift.io/managed=true
              machine.openshift.io/cluster-api-cluster=cs220lws-cxw8p
Annotations:  capacity.cluster-autoscaler.kubernetes.io/labels: kubernetes.io/arch=amd64
              machine.openshift.io/GPU: 0
              machine.openshift.io/memoryMb: 16384
              machine.openshift.io/vCPU: 4
API Version:  machine.openshift.io/v1beta1
Kind:         MachineSet
Metadata:
  Creation Timestamp:  2024-10-05T16:31:50Z
  Generation:          1
  Managed Fields:
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:labels:
          .:
          f:hive.openshift.io/machine-pool:
          f:hive.openshift.io/managed:
          f:machine.openshift.io/cluster-api-cluster:
      f:spec:
        .:
        f:replicas:
        f:selector:
        f:template:
          .:
          f:metadata:
            .:
            f:labels:
              .:
              f:machine.openshift.io/cluster-api-cluster:
              f:machine.openshift.io/cluster-api-machine-role:
              f:machine.openshift.io/cluster-api-machine-type:
              f:machine.openshift.io/cluster-api-machineset:
          f:spec:
            .:
            f:lifecycleHooks:
            f:metadata:
            f:providerSpec:
              .:
              f:value:
                .:
                f:ami:
                  .:
                  f:id:
                f:apiVersion:
                f:blockDevices:
                f:credentialsSecret:
                  .:
                  f:name:
                f:deviceIndex:
                f:iamInstanceProfile:
                  .:
                  f:id:
                f:instanceType:
                f:kind:
                f:metadata:
                  .:
                  f:creationTimestamp:
                f:metadataServiceOptions:
                f:placement:
                  .:
                  f:availabilityZone:
                  f:region:
                f:securityGroups:
                f:subnet:
                  .:
                  f:id:
                f:tags:
                f:userDataSecret:
                  .:
                  f:name:
    Manager:      cluster-bootstrap
    Operation:    Update
    Time:         2024-10-05T16:31:50Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:status:
    Manager:      cluster-bootstrap
    Operation:    Update
    Subresource:  status
    Time:         2024-10-05T16:31:50Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:annotations:
          .:
          f:capacity.cluster-autoscaler.kubernetes.io/labels:
          f:machine.openshift.io/GPU:
          f:machine.openshift.io/memoryMb:
          f:machine.openshift.io/vCPU:
    Manager:      machine-controller-manager
    Operation:    Update
    Time:         2024-10-05T16:38:35Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:status:
        f:availableReplicas:
        f:fullyLabeledReplicas:
        f:observedGeneration:
        f:readyReplicas:
        f:replicas:
    Manager:         machineset-controller
    Operation:       Update
    Subresource:     status
    Time:            2024-10-05T17:00:30Z
  Resource Version:  40633
  UID:               db5c86d7-2b49-4417-bd09-b9ad3ee6e8fb
Spec:
  Replicas:  2
  Selector:
    Match Labels:
      machine.openshift.io/cluster-api-cluster:     cs220lws-cxw8p
      machine.openshift.io/cluster-api-machineset:  cs220lws-cxw8p-worker-ap-southeast-2a
  Template:
    Metadata:
      Labels:
        machine.openshift.io/cluster-api-cluster:       cs220lws-cxw8p
        machine.openshift.io/cluster-api-machine-role:  worker
        machine.openshift.io/cluster-api-machine-type:  worker
        machine.openshift.io/cluster-api-machineset:    cs220lws-cxw8p-worker-ap-southeast-2a
    Spec:
      Lifecycle Hooks:
      Metadata:
      Provider Spec:
        Value:
          Ami:
            Id:         ami-0c9a7d075dac15517
          API Version:  machine.openshift.io/v1beta1
          Block Devices:
            Ebs:
              Encrypted:  true
              Iops:       0
              Kms Key:
                Arn:        
              Volume Size:  300
              Volume Type:  gp3
          Credentials Secret:
            Name:        aws-cloud-credentials
          Device Index:  0
          Iam Instance Profile:
            Id:           cs220lws-cxw8p-worker-profile
          Instance Type:  m5.xlarge
          Kind:           AWSMachineProviderConfig
          Metadata:
            Creation Timestamp:  <nil>
          Metadata Service Options:
          Placement:
            Availability Zone:  ap-southeast-2a
            Region:             ap-southeast-2
          Security Groups:
            Filters:
              Name:  tag:Name
              Values:
                cs220lws-cxw8p-worker-sg
          Subnet:
            Id:  subnet-0e9ab412dc0120842
          Tags:
            Name:   kubernetes.io/cluster/cs220lws-cxw8p
            Value:  owned
            Name:   red-hat-clustertype
            Value:  rosa
            Name:   red-hat-managed
            Value:  true
            Name:   redhattraining:course-sku
            Value:  CS220
            Name:   redhattraining:rosa-cluster-id
            Value:  cs220lws
          User Data Secret:
            Name:  worker-user-data
Status:
  Available Replicas:      2
  Fully Labeled Replicas:  2
  Observed Generation:     1
  Ready Replicas:          2
  Replicas:                2
Events:                    <none>
[student@workstation ~]$ oc get machines -A -L machine.openshift.io/cluster-api-machineset
NAMESPACE               NAME                                          PHASE     TYPE         REGION           ZONE              AGE   CLUSTER-API-MACHINESET
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a-ft65n    Running   r5.xlarge    ap-southeast-2   ap-southeast-2a   18h   cs220lws-cxw8p-infra-ap-southeast-2a
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a-xvg4m    Running   r5.xlarge    ap-southeast-2   ap-southeast-2a   18h   cs220lws-cxw8p-infra-ap-southeast-2a
openshift-machine-api   cs220lws-cxw8p-master-0                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   19h   
openshift-machine-api   cs220lws-cxw8p-master-1                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   19h   
openshift-machine-api   cs220lws-cxw8p-master-2                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   19h   
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a-c7v9r   Running   m5.xlarge    ap-southeast-2   ap-southeast-2a   19h   cs220lws-cxw8p-worker-ap-southeast-2a
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a-snvrx   Running   m5.xlarge    ap-southeast-2   ap-southeast-2a   19h   cs220lws-cxw8p-worker-ap-southeast-2a
[student@workstation ~]$ 
[student@workstation ~]$ oc get nodes 
NAME                                            STATUS   ROLES                  AGE   VERSION
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   19h   v1.28.13+2ca1a23
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           18h   v1.28.13+2ca1a23
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   19h   v1.28.13+2ca1a23
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   19h   v1.28.13+2ca1a23
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 19h   v1.28.13+2ca1a23
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           18h   v1.28.13+2ca1a23
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 19h   v1.28.13+2ca1a23
[student@workstation ~]$ oc get nodes -o json | jq '.items[].metadata | .name,.annotations."machine.openshift.io/machine"'
"ip-10-1-0-121.ap-southeast-2.compute.internal"
"openshift-machine-api/cs220lws-cxw8p-master-0"
"ip-10-1-0-19.ap-southeast-2.compute.internal"
"openshift-machine-api/cs220lws-cxw8p-infra-ap-southeast-2a-ft65n"
"ip-10-1-0-223.ap-southeast-2.compute.internal"
"openshift-machine-api/cs220lws-cxw8p-master-1"
"ip-10-1-0-242.ap-southeast-2.compute.internal"
"openshift-machine-api/cs220lws-cxw8p-master-2"
"ip-10-1-0-247.ap-southeast-2.compute.internal"
"openshift-machine-api/cs220lws-cxw8p-worker-ap-southeast-2a-snvrx"
"ip-10-1-0-252.ap-southeast-2.compute.internal"
"openshift-machine-api/cs220lws-cxw8p-infra-ap-southeast-2a-xvg4m"
"ip-10-1-0-62.ap-southeast-2.compute.internal"
"openshift-machine-api/cs220lws-cxw8p-worker-ap-southeast-2a-c7v9r"
[student@workstation ~]$ oc get nods -o custom-columns='NAME:.metadata.name,MACHINE:.metadata.annotations.machine\.openshift\.io/machine'
error: the server doesn't have a resource type "nods"
[student@workstation ~]$ oc get nodes -o custom-columns='NAME:.metadata.name,MACHINE:.metadata.annotations.machine\.openshift\.io/machine'
NAME                                            MACHINE
ip-10-1-0-121.ap-southeast-2.compute.internal   openshift-machine-api/cs220lws-cxw8p-master-0
ip-10-1-0-19.ap-southeast-2.compute.internal    openshift-machine-api/cs220lws-cxw8p-infra-ap-southeast-2a-ft65n
ip-10-1-0-223.ap-southeast-2.compute.internal   openshift-machine-api/cs220lws-cxw8p-master-1
ip-10-1-0-242.ap-southeast-2.compute.internal   openshift-machine-api/cs220lws-cxw8p-master-2
ip-10-1-0-247.ap-southeast-2.compute.internal   openshift-machine-api/cs220lws-cxw8p-worker-ap-southeast-2a-snvrx
ip-10-1-0-252.ap-southeast-2.compute.internal   openshift-machine-api/cs220lws-cxw8p-infra-ap-southeast-2a-xvg4m
ip-10-1-0-62.ap-southeast-2.compute.internal    openshift-machine-api/cs220lws-cxw8p-worker-ap-southeast-2a-c7v9r
[student@workstation ~]$ 
[student@workstation ~]$ 
[student@workstation ~]$ aws ec2 describe-instances --output table --filters "Name=tag:redhattraining:rosa-cluster-id,Values=cs220lws" "Name=instance-state-name,Values=running" --query "Reservations[].Instances[].InstanceType,Tags[?Key=='Name']|[0].Value]"

Bad value for --query Reservations[].Instances[].InstanceType,Tags[?Key=='Name']|[0].Value]: Unexpected token: ,: Parse error at column 39, token "," (COMMA), for expression:
"Reservations[].Instances[].InstanceType,Tags[?Key=='Name']|[0].Value]"
                                        ^
[student@workstation ~]$ aws ec2 describe-instances --output table --filters "Name=tag:redhattraining:rosa-cluster-id,Values=cs220lws" "Name=instance-state-name,Values=running" --query "Reservations[].Instances[].[InstanceType,Tags[?Key=='Name']|[0].Value]"
---------------------------------------------------------------
|                      DescribeInstances                      |
+------------+------------------------------------------------+
|  m5.xlarge |  cs220lws-cxw8p-worker-ap-southeast-2a-snvrx   |
|  m5.2xlarge|  cs220lws-cxw8p-master-1                       |
|  m5.2xlarge|  cs220lws-cxw8p-master-0                       |
|  r5.xlarge |  cs220lws-cxw8p-infra-ap-southeast-2a-ft65n    |
|  m5.2xlarge|  cs220lws-cxw8p-master-2                       |
|  m5.xlarge |  cs220lws-cxw8p-worker-ap-southeast-2a-c7v9r   |
|  r5.xlarge |  cs220lws-cxw8p-infra-ap-southeast-2a-xvg4m    |
+------------+------------------------------------------------+
[student@workstation ~]$ oc get machines -A 
NAMESPACE               NAME                                          PHASE     TYPE         REGION           ZONE              AGE
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a-ft65n    Running   r5.xlarge    ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a-xvg4m    Running   r5.xlarge    ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-master-0                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-master-1                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-master-2                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a-c7v9r   Running   m5.xlarge    ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a-snvrx   Running   m5.xlarge    ap-southeast-2   ap-southeast-2a   20h
[student@workstation ~]$ 
[student@workstation ~]$ 
[student@workstation ~]$ complete -C '/usr/local/bin/aws_completer' aws
[student@workstation ~]$ aws ec2 describe-instance-types --instance-types m5.xlarge --query "InstanceTypes[].MemoryInfo"
[
    {
        "SizeInMiB": 16384
    }
]
[student@workstation ~]$ rosa list instance-types | grep m5.xlarge
m5.xlarge          general_purpose        4          16.0 GiB
[student@workstation ~]$ rosa list instance-types | head 
ID                 CATEGORY               CPU_CORES  MEMORY
dl1.24xlarge       accelerated_computing  96         768.0 GiB
g4ad.16xlarge      accelerated_computing  64         256.0 GiB
g4ad.2xlarge       accelerated_computing  8          32.0 GiB
g4ad.4xlarge       accelerated_computing  16         64.0 GiB
g4ad.8xlarge       accelerated_computing  32         128.0 GiB
g4ad.xlarge        accelerated_computing  4          16.0 GiB
g4dn.12xlarge      accelerated_computing  48         192.0 GiB
g4dn.16xlarge      accelerated_computing  64         256.0 GiB
g4dn.2xlarge       accelerated_computing  8          32.0 GiB
[student@workstation ~]$ rosa list instance-types | grep r5a.xlarge
r5a.xlarge         memory_optimized       4          32.0 GiB
[student@workstation ~]$ rosa list machinepools -c cs220lws
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS    TAINTS    AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
worker  No           2         m5.xlarge                          ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ rosa create machinepool --help 
Add a machine pool to the cluster.

Usage:
  rosa create machinepool [flags]

Aliases:
  machinepool, machinepools, machine-pool, machine-pools

Examples:
  # Interactively add a machine pool to a cluster named "mycluster"
  rosa create machinepool --cluster=mycluster --interactive
  # Add a machine pool mp-1 with 3 replicas of m5.xlarge to a cluster
  rosa create machinepool --cluster=mycluster --name=mp-1 --replicas=3 --instance-type=m5.xlarge
  # Add a machine pool mp-1 with autoscaling enabled and 3 to 6 replicas of m5.xlarge to a cluster
  rosa create machinepool --cluster=mycluster --name=mp-1 --enable-autoscaling \
	--min-replicas=3 --max-replicas=6 --instance-type=m5.xlarge
  # Add a machine pool with labels to a cluster
  rosa create machinepool -c mycluster --name=mp-1 --replicas=2 --instance-type=r5.2xlarge --labels=foo=bar,bar=baz,
  # Add a machine pool with spot instances to a cluster
  rosa create machinepool -c mycluster --name=mp-1 --replicas=2 --instance-type=r5.2xlarge --use-spot-instances \
    --spot-max-price=0.5
  # Add a machine pool to a cluster and set the node drain grace period
  rosa create machinepool -c mycluster --name=mp-1 --node-drain-grace-period="90 minutes"

Flags:
      --additional-security-group-ids strings   The additional Security Group IDs to be added to the machine pool. Format should be a comma-separated list.
      --autorepair                              Select auto-repair behaviour for a machinepool in a hosted cluster. (default true)
      --availability-zone string                Select availability zone to create a single AZ machine pool for a multi-AZ cluster
  -c, --cluster string                          Name or ID of the cluster.
      --disk-size string                        Root disk size with a suffix like GiB or TiB
      --ec2-metadata-http-tokens string         Should cluster nodes use both v1 and v2 endpoints or just v2 endpoint of EC2 Instance Metadata Service (IMDS)This flag is only supported for Hosted Control Planes.
      --enable-autoscaling                      Enable autoscaling for the machine pool.
  -h, --help                                    help for machinepool
      --instance-type string                    Instance type that should be used. (default "m5.xlarge")
  -i, --interactive                             Enable interactive mode.
      --kubelet-configs string                  Name of the kubelet config to be applied to the machine pool. A single kubelet config is allowed. Kubelet config must already exist. This will overwrite any modifications made to node kubelet configs on an ongoing basis.
      --labels string                           Labels for machine pool. Format should be a comma-separated list of 'key=value'. This list will overwrite any modifications made to Node labels on an ongoing basis.
      --max-replicas int                        Maximum number of machines for the machine pool.
      --max-surge string                        The maximum number of nodes that can be provisioned above the desired number of nodes in the machinepool during the upgrade. It can be an absolute number i.e. 1, or a percentage i.e. '20%'. (default "1")
      --max-unavailable string                  The maximum number of nodes in the machinepool that can be unavailable during the upgrade. It can be an absolute number i.e. 1, or a percentage i.e. '20%'. (default "0")
      --min-replicas int                        Minimum number of machines for the machine pool.
      --multi-availability-zone                 Create a multi-AZ machine pool for a multi-AZ cluster (default true)
      --name string                             Name for the machine pool (required).
      --node-drain-grace-period string          You may set a grace period for how long Pod Disruption Budget-protected workloads will be respected when the NodePool is being replaced or upgraded.
                                                After this grace period, all remaining workloads will be forcibly evicted.
                                                Valid value is from 0 to 1 week (10080 minutes), and the supported units are 'minute|minutes' or 'hour|hours'. 0 or empty value means that the NodePool can be drained without any time limitations.
                                                This flag is only supported for Hosted Control Planes.
  -o, --output string                           Output format. Allowed formats are [json yaml]
      --replicas int                            Count of machines for the machine pool (required when autoscaling is disabled).
      --spot-max-price string                   Max price for spot instance. If empty use the on-demand price. (default "on-demand")
      --subnet string                           Select subnet to create a single AZ machine pool for BYOVPC cluster
      --tags strings                            Apply user defined tags to all resources created by ROSA in AWS. Tags are comma separated, for example: 'key value, foo bar'
      --taints string                           Taints for machine pool. Format should be a comma-separated list of 'key=value:ScheduleType'. This list will overwrite any modifications made to Node taints on an ongoing basis.
      --tuning-configs string                   Name of the tuning configs to be applied to the machine pool. Format should be a comma-separated list. Tuning config must already exist. This list will overwrite any modifications made to node tuning configs on an ongoing basis.
      --use-spot-instances                      Use spot instances for the machine pool.
      --version string                          Version of OpenShift that will be used to install a machine pool for a hosted cluster, for example "4.12.4"

Global Flags:
      --color string     Surround certain characters with escape sequences to display them in color on the terminal. Allowed options are [auto never always] (default "auto")
      --debug            Enable debug mode.
      --profile string   Use a specific AWS profile from your credential file.
      --region string    Use a specific AWS region, overriding the AWS_REGION environment variable.
  -y, --yes              Automatically answer yes to confirm operation.
[student@workstation ~]$ rosa create machinepool --cluster cs220lws --name memory --replicas 2 --instance-type r5a.xlarge --labels workload=memory --taints memory-optimized=32GiB:NoSchedule 
I: Checking available instance types for machine pool 'memory'
I: Machine pool 'memory' created successfully on cluster 'cs220lws'
I: To view the machine pool details, run 'rosa describe machinepool --cluster cs220lws --machinepool memory'
I: To view all machine pools, run 'rosa list machinepools --cluster cs220lws'
[student@workstation ~]$ rosa list machinepools --cluster cs220lws
ID      AUTOSCALING  REPLICAS  INSTANCE TYPE  LABELS             TAINTS                               AVAILABILITY ZONES    SUBNETS                     SPOT INSTANCES  DISK SIZE  SG IDs
memory  No           2         r5a.xlarge     workload=memory    memory-optimized=32GiB:NoSchedule    ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
worker  No           2         m5.xlarge                                                              ap-southeast-2a       subnet-0e9ab412dc0120842    No              300 GiB    
[student@workstation ~]$ oc get machinesets -A 
NAMESPACE               NAME                                    DESIRED   CURRENT   READY   AVAILABLE   AGE
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a    2         2         2       2           20h
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a   2         2                             66s
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a   2         2         2       2           20h
[student@workstation ~]$ oc describe machinesets cs220lws-cxw8p-memory-ap-southeast-2a -n openshift-machine-api
Name:         cs220lws-cxw8p-memory-ap-southeast-2a
Namespace:    openshift-machine-api
Labels:       hive.openshift.io/machine-pool=memory
              hive.openshift.io/managed=true
              machine.openshift.io/cluster-api-cluster=cs220lws-cxw8p
Annotations:  capacity.cluster-autoscaler.kubernetes.io/labels: kubernetes.io/arch=amd64
              machine.openshift.io/GPU: 0
              machine.openshift.io/memoryMb: 32768
              machine.openshift.io/vCPU: 4
API Version:  machine.openshift.io/v1beta1
Kind:         MachineSet
Metadata:
  Creation Timestamp:  2024-10-06T13:10:33Z
  Generation:          1
  Managed Fields:
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:labels:
          .:
          f:hive.openshift.io/machine-pool:
          f:hive.openshift.io/managed:
          f:machine.openshift.io/cluster-api-cluster:
      f:spec:
        .:
        f:replicas:
        f:selector:
        f:template:
          .:
          f:metadata:
            .:
            f:labels:
              .:
              f:machine.openshift.io/cluster-api-cluster:
              f:machine.openshift.io/cluster-api-machine-role:
              f:machine.openshift.io/cluster-api-machine-type:
              f:machine.openshift.io/cluster-api-machineset:
          f:spec:
            .:
            f:lifecycleHooks:
            f:metadata:
              .:
              f:labels:
                .:
                f:workload:
            f:providerSpec:
              .:
              f:value:
                .:
                f:ami:
                  .:
                  f:id:
                f:apiVersion:
                f:blockDevices:
                f:credentialsSecret:
                  .:
                  f:name:
                f:deviceIndex:
                f:iamInstanceProfile:
                  .:
                  f:id:
                f:instanceType:
                f:kind:
                f:metadata:
                  .:
                  f:creationTimestamp:
                f:metadataServiceOptions:
                f:placement:
                  .:
                  f:availabilityZone:
                  f:region:
                f:securityGroups:
                f:subnet:
                  .:
                  f:id:
                f:tags:
                f:userDataSecret:
                  .:
                  f:name:
            f:taints:
    Manager:      hive2-machinepool
    Operation:    Update
    Time:         2024-10-06T13:10:33Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:annotations:
          .:
          f:capacity.cluster-autoscaler.kubernetes.io/labels:
          f:machine.openshift.io/GPU:
          f:machine.openshift.io/memoryMb:
          f:machine.openshift.io/vCPU:
    Manager:      machine-controller-manager
    Operation:    Update
    Time:         2024-10-06T13:10:33Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:status:
        .:
        f:fullyLabeledReplicas:
        f:observedGeneration:
        f:replicas:
    Manager:         machineset-controller
    Operation:       Update
    Subresource:     status
    Time:            2024-10-06T13:10:33Z
  Resource Version:  779625
  UID:               1ee9537e-aedf-478a-a157-d64e1a02fdc3
Spec:
  Replicas:  2
  Selector:
    Match Labels:
      machine.openshift.io/cluster-api-cluster:     cs220lws-cxw8p
      machine.openshift.io/cluster-api-machineset:  cs220lws-cxw8p-memory-ap-southeast-2a
  Template:
    Metadata:
      Labels:
        machine.openshift.io/cluster-api-cluster:       cs220lws-cxw8p
        machine.openshift.io/cluster-api-machine-role:  memory
        machine.openshift.io/cluster-api-machine-type:  memory
        machine.openshift.io/cluster-api-machineset:    cs220lws-cxw8p-memory-ap-southeast-2a
    Spec:
      Lifecycle Hooks:
      Metadata:
        Labels:
          Workload:  memory
      Provider Spec:
        Value:
          Ami:
            Id:         ami-0f45350e59d5513cb
          API Version:  machine.openshift.io/v1beta1
          Block Devices:
            Ebs:
              Encrypted:  true
              Iops:       0
              Kms Key:
                Arn:        
              Volume Size:  300
              Volume Type:  gp3
          Credentials Secret:
            Name:        aws-cloud-credentials
          Device Index:  0
          Iam Instance Profile:
            Id:           cs220lws-cxw8p-worker-profile
          Instance Type:  r5a.xlarge
          Kind:           AWSMachineProviderConfig
          Metadata:
            Creation Timestamp:  <nil>
          Metadata Service Options:
          Placement:
            Availability Zone:  ap-southeast-2a
            Region:             ap-southeast-2
          Security Groups:
            Filters:
              Name:  tag:Name
              Values:
                cs220lws-cxw8p-node
            Filters:
              Name:  tag:Name
              Values:
                cs220lws-cxw8p-lb
            Filters:
              Name:  tag:Name
              Values:
                cs220lws-cxw8p-worker-sg
          Subnet:
            Id:  subnet-0e9ab412dc0120842
          Tags:
            Name:   kubernetes.io/cluster/cs220lws-cxw8p
            Value:  owned
            Name:   red-hat-clustertype
            Value:  rosa
            Name:   red-hat-managed
            Value:  true
            Name:   redhattraining:course-sku
            Value:  CS220
            Name:   redhattraining:rosa-cluster-id
            Value:  cs220lws
          User Data Secret:
            Name:  worker-user-data
      Taints:
        Effect:  NoSchedule
        Key:     memory-optimized
        Value:   32GiB
Status:
  Fully Labeled Replicas:  2
  Observed Generation:     1
  Replicas:                2
Events:                    <none>
[student@workstation ~]$ oc get machines -A 
NAMESPACE               NAME                                          PHASE     TYPE         REGION           ZONE              AGE
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a-ft65n    Running   r5.xlarge    ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-infra-ap-southeast-2a-xvg4m    Running   r5.xlarge    ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-master-0                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-master-1                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-master-2                       Running   m5.2xlarge   ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a-6fv44   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   4m52s
openshift-machine-api   cs220lws-cxw8p-memory-ap-southeast-2a-np7l9   Running   r5a.xlarge   ap-southeast-2   ap-southeast-2a   4m52s
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a-c7v9r   Running   m5.xlarge    ap-southeast-2   ap-southeast-2a   20h
openshift-machine-api   cs220lws-cxw8p-worker-ap-southeast-2a-snvrx   Running   m5.xlarge    ap-southeast-2   ap-southeast-2a   20h
[student@workstation ~]$ oc describe machine cs220lws-cxw8p-memory-ap-southeast-2a-6fv44 -n openshift-machine-api
Name:         cs220lws-cxw8p-memory-ap-southeast-2a-6fv44
Namespace:    openshift-machine-api
Labels:       machine.openshift.io/cluster-api-cluster=cs220lws-cxw8p
              machine.openshift.io/cluster-api-machine-role=memory
              machine.openshift.io/cluster-api-machine-type=memory
              machine.openshift.io/cluster-api-machineset=cs220lws-cxw8p-memory-ap-southeast-2a
              machine.openshift.io/instance-type=r5a.xlarge
              machine.openshift.io/region=ap-southeast-2
              machine.openshift.io/zone=ap-southeast-2a
Annotations:  machine.openshift.io/instance-state: running
API Version:  machine.openshift.io/v1beta1
Kind:         Machine
Metadata:
  Creation Timestamp:  2024-10-06T13:10:33Z
  Finalizers:
    machine.machine.openshift.io
  Generate Name:  cs220lws-cxw8p-memory-ap-southeast-2a-
  Generation:     2
  Managed Fields:
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:generateName:
        f:labels:
          .:
          f:machine.openshift.io/cluster-api-cluster:
          f:machine.openshift.io/cluster-api-machine-role:
          f:machine.openshift.io/cluster-api-machine-type:
          f:machine.openshift.io/cluster-api-machineset:
        f:ownerReferences:
          .:
          k:{"uid":"1ee9537e-aedf-478a-a157-d64e1a02fdc3"}:
      f:spec:
        .:
        f:lifecycleHooks:
        f:metadata:
          .:
          f:labels:
            .:
            f:workload:
        f:providerSpec:
          .:
          f:value:
            .:
            f:ami:
              .:
              f:id:
            f:apiVersion:
            f:blockDevices:
            f:credentialsSecret:
              .:
              f:name:
            f:deviceIndex:
            f:iamInstanceProfile:
              .:
              f:id:
            f:instanceType:
            f:kind:
            f:metadata:
              .:
              f:creationTimestamp:
            f:metadataServiceOptions:
            f:placement:
              .:
              f:availabilityZone:
              f:region:
            f:securityGroups:
            f:subnet:
              .:
              f:id:
            f:tags:
            f:userDataSecret:
              .:
              f:name:
        f:taints:
    Manager:      machineset-controller
    Operation:    Update
    Time:         2024-10-06T13:10:33Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:annotations:
          .:
          f:machine.openshift.io/instance-state:
        f:finalizers:
          .:
          v:"machine.machine.openshift.io":
        f:labels:
          f:machine.openshift.io/instance-type:
          f:machine.openshift.io/region:
          f:machine.openshift.io/zone:
      f:spec:
        f:providerID:
    Manager:      machine-controller-manager
    Operation:    Update
    Time:         2024-10-06T13:11:07Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:status:
        .:
        f:addresses:
        f:conditions:
        f:phase:
        f:providerStatus:
          .:
          f:conditions:
          f:instanceId:
          f:instanceState:
    Manager:      machine-controller-manager
    Operation:    Update
    Subresource:  status
    Time:         2024-10-06T13:14:52Z
    API Version:  machine.openshift.io/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:status:
        f:lastUpdated:
        f:nodeRef:
    Manager:      nodelink-controller
    Operation:    Update
    Subresource:  status
    Time:         2024-10-06T13:16:19Z
  Owner References:
    API Version:           machine.openshift.io/v1beta1
    Block Owner Deletion:  true
    Controller:            true
    Kind:                  MachineSet
    Name:                  cs220lws-cxw8p-memory-ap-southeast-2a
    UID:                   1ee9537e-aedf-478a-a157-d64e1a02fdc3
  Resource Version:        783869
  UID:                     fd04984d-f93a-4197-8148-0fbcade1aa17
Spec:
  Lifecycle Hooks:
  Metadata:
    Labels:
      Workload:  memory
  Provider ID:   aws:///ap-southeast-2a/i-0e5445a95b9ebcada
  Provider Spec:
    Value:
      Ami:
        Id:         ami-0f45350e59d5513cb
      API Version:  machine.openshift.io/v1beta1
      Block Devices:
        Ebs:
          Encrypted:  true
          Iops:       0
          Kms Key:
            Arn:        
          Volume Size:  300
          Volume Type:  gp3
      Credentials Secret:
        Name:        aws-cloud-credentials
      Device Index:  0
      Iam Instance Profile:
        Id:           cs220lws-cxw8p-worker-profile
      Instance Type:  r5a.xlarge
      Kind:           AWSMachineProviderConfig
      Metadata:
        Creation Timestamp:  <nil>
      Metadata Service Options:
      Placement:
        Availability Zone:  ap-southeast-2a
        Region:             ap-southeast-2
      Security Groups:
        Filters:
          Name:  tag:Name
          Values:
            cs220lws-cxw8p-node
        Filters:
          Name:  tag:Name
          Values:
            cs220lws-cxw8p-lb
        Filters:
          Name:  tag:Name
          Values:
            cs220lws-cxw8p-worker-sg
      Subnet:
        Id:  subnet-0e9ab412dc0120842
      Tags:
        Name:   kubernetes.io/cluster/cs220lws-cxw8p
        Value:  owned
        Name:   red-hat-clustertype
        Value:  rosa
        Name:   red-hat-managed
        Value:  true
        Name:   redhattraining:course-sku
        Value:  CS220
        Name:   redhattraining:rosa-cluster-id
        Value:  cs220lws
      User Data Secret:
        Name:  worker-user-data
  Taints:
    Effect:  NoSchedule
    Key:     memory-optimized
    Value:   32GiB
Status:
  Addresses:
    Address:  10.1.0.93
    Type:     InternalIP
    Address:  ip-10-1-0-93.ap-southeast-2.compute.internal
    Type:     InternalDNS
    Address:  ip-10-1-0-93.ap-southeast-2.compute.internal
    Type:     Hostname
  Conditions:
    Last Transition Time:  2024-10-06T13:10:33Z
    Status:                True
    Type:                  Drainable
    Last Transition Time:  2024-10-06T13:11:07Z
    Status:                True
    Type:                  InstanceExists
    Last Transition Time:  2024-10-06T13:10:33Z
    Status:                True
    Type:                  Terminable
  Last Updated:            2024-10-06T13:16:19Z
  Node Ref:
    Kind:  Node
    Name:  ip-10-1-0-93.ap-southeast-2.compute.internal
    UID:   b22569a6-4af9-4546-a980-bb1105c63f4c
  Phase:   Running
  Provider Status:
    Conditions:
      Last Transition Time:  2024-10-06T13:10:37Z
      Message:               Machine successfully created
      Reason:                MachineCreationSucceeded
      Status:                True
      Type:                  MachineCreation
    Instance Id:             i-0e5445a95b9ebcada
    Instance State:          running
Events:
  Type     Reason             Age                     From                           Message
  ----     ------             ----                    ----                           -------
  Normal   Create             7m20s                   awscontroller                  Created Machine cs220lws-cxw8p-memory-ap-southeast-2a-6fv44
  Warning  FailedUpdate       7m19s (x2 over 7m20s)   awscontroller                  cs220lws-cxw8p-memory-ap-southeast-2a-6fv44: reconciler failed to Update machine: requeue in: 20s
  Normal   DetectedUnhealthy  6m50s (x16 over 7m24s)  machinehealthcheck-controller  Machine openshift-machine-api/srep-worker-healthcheck/cs220lws-cxw8p-memory-ap-southeast-2a-6fv44/ has unhealthy node
  Normal   Update             6m50s                   awscontroller                  Updated Machine cs220lws-cxw8p-memory-ap-southeast-2a-6fv44
  Normal   DetectedUnhealthy  2m20s (x26 over 3m5s)   machinehealthcheck-controller  Machine openshift-machine-api/srep-worker-healthcheck/cs220lws-cxw8p-memory-ap-southeast-2a-6fv44/ip-10-1-0-93.ap-southeast-2.compute.internal has unhealthy node ip-10-1-0-93.ap-southeast-2.compute.internal
[student@workstation ~]$ oc get nodes 
NAME                                            STATUS   ROLES                  AGE     VERSION
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   20h     v1.28.13+2ca1a23
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           20h     v1.28.13+2ca1a23
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   20h     v1.28.13+2ca1a23
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   20h     v1.28.13+2ca1a23
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 20h     v1.28.13+2ca1a23
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           20h     v1.28.13+2ca1a23
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 20h     v1.28.13+2ca1a23
ip-10-1-0-63.ap-southeast-2.compute.internal    Ready    worker                 3m46s   v1.28.13+2ca1a23
ip-10-1-0-93.ap-southeast-2.compute.internal    Ready    worker                 3m46s   v1.28.13+2ca1a23
[student@workstation ~]$ oc get nodes  -L workload 
NAME                                            STATUS   ROLES                  AGE     VERSION            WORKLOAD
ip-10-1-0-121.ap-southeast-2.compute.internal   Ready    control-plane,master   20h     v1.28.13+2ca1a23   
ip-10-1-0-19.ap-southeast-2.compute.internal    Ready    infra,worker           20h     v1.28.13+2ca1a23   
ip-10-1-0-223.ap-southeast-2.compute.internal   Ready    control-plane,master   20h     v1.28.13+2ca1a23   
ip-10-1-0-242.ap-southeast-2.compute.internal   Ready    control-plane,master   20h     v1.28.13+2ca1a23   
ip-10-1-0-247.ap-southeast-2.compute.internal   Ready    worker                 20h     v1.28.13+2ca1a23   
ip-10-1-0-252.ap-southeast-2.compute.internal   Ready    infra,worker           20h     v1.28.13+2ca1a23   
ip-10-1-0-62.ap-southeast-2.compute.internal    Ready    worker                 20h     v1.28.13+2ca1a23   
ip-10-1-0-63.ap-southeast-2.compute.internal    Ready    worker                 4m27s   v1.28.13+2ca1a23   memory
ip-10-1-0-93.ap-southeast-2.compute.internal    Ready    worker                 4m27s   v1.28.13+2ca1a23   memory
[student@workstation ~]$ oc get nodes -o custom_columns=NAME:.metadata.name,TAINTS:.spec.taints[].key
error: unable to match a printer suitable for the output format "custom_columns=NAME:.metadata.name,TAINTS:.spec.taints[].key", allowed formats are: custom-columns,custom-columns-file,go-template,go-template-file,json,jsonpath,jsonpath-as-json,jsonpath-file,name,template,templatefile,wide,yaml
[student@workstation ~]$ 
[student@workstation ~]$ 
[student@workstation ~]$ oc get nodes -o custom-columns=NAME:.metadata.name,TAINTS:.spec.taints[].key
NAME                                            TAINTS
ip-10-1-0-121.ap-southeast-2.compute.internal   node-role.kubernetes.io/master
ip-10-1-0-19.ap-southeast-2.compute.internal    node-role.kubernetes.io/infra
ip-10-1-0-223.ap-southeast-2.compute.internal   node-role.kubernetes.io/master
ip-10-1-0-242.ap-southeast-2.compute.internal   node-role.kubernetes.io/master
ip-10-1-0-247.ap-southeast-2.compute.internal   <none>
ip-10-1-0-252.ap-southeast-2.compute.internal   node-role.kubernetes.io/infra
ip-10-1-0-62.ap-southeast-2.compute.internal    <none>
ip-10-1-0-63.ap-southeast-2.compute.internal    memory-optimized
ip-10-1-0-93.ap-southeast-2.compute.internal    memory-optimized
[student@workstation ~]$ oc new-project node-pools
Now using project "node-pools" on server "https://api.cs220lws.nw83.p1.openshiftapps.com:6443".

You can add applications to this project with the 'new-app' command. For example, try:

    oc new-app rails-postgresql-example

to build a new example application in Ruby. Or use kubectl to deploy a simple Kubernetes application:

    kubectl create deployment hello-node --image=k8s.gcr.io/e2e-test-images/agnhost:2.33 -- /agnhost serve-hostname

[student@workstation ~]$ wget https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/node-pools/need-20gib.yaml
--2024-10-06 09:58:20--  https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/resources/node-pools/need-20gib.yaml
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.108.133, 185.199.109.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1714 (1.7K) [text/plain]
Saving to: ‘need-20gib.yaml’

need-20gib.yaml                             100%[========================================================================================>]   1.67K  --.-KB/s    in 0s      

2024-10-06 09:58:21 (32.5 MB/s) - ‘need-20gib.yaml’ saved [1714/1714]

[student@workstation ~]$ cat need-20gib.yaml 
---
apiVersion: v1
kind: List
metadata: {}
items:
  - apiVersion: apps/v1
    kind: Deployment
    metadata:
      labels:
        app: need-20gib
      name: need-20gib
    spec:
      replicas: 2
      selector:
        matchLabels:
          app: need-20gib
      template:
        metadata:
          labels:
            app: need-20gib
        spec:
          containers:
            - name: need-20gib
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
        app: need-20gib
      name: need-20gib
    spec:
      ports:
        - protocol: TCP
          port: 3000
          targetPort: 3000
      selector:
        app: need-20gib
  - apiVersion: route.openshift.io/v1
    kind: Route
    metadata:
      labels:
        app: need-20gib
      name: need-20gib
    spec:
      port:
        targetPort: 3000
      to:
        kind: Service
        name: need-20gib
      tls:
        termination: edge
[student@workstation ~]$ oc apply -f need-20gib.yaml 
deployment.apps/need-20gib created
service/need-20gib created
route.route.openshift.io/need-20gib created
[student@workstation ~]$ oc get pods 
NAME                          READY   STATUS    RESTARTS   AGE
need-20gib-58775b7dbf-9vsl9   0/1     Pending   0          5s
need-20gib-58775b7dbf-hf46b   0/1     Pending   0          5s
[student@workstation ~]$ oc describe pod need-20gib-58775b7dbf-9vsl9
Name:             need-20gib-58775b7dbf-9vsl9
Namespace:        node-pools
Priority:         0
Service Account:  default
Node:             <none>
Labels:           app=need-20gib
                  pod-template-hash=58775b7dbf
Annotations:      openshift.io/scc: restricted-v2
                  seccomp.security.alpha.kubernetes.io/pod: runtime/default
Status:           Pending
IP:               
IPs:              <none>
Controlled By:    ReplicaSet/need-20gib-58775b7dbf
Containers:
  need-20gib:
    Image:      quay.io/redhattraining/long-load:v1
    Port:       3000/TCP
    Host Port:  0/TCP
    Requests:
      memory:     20Gi
    Liveness:     http-get http://:3000/health delay=30s timeout=1s period=10s #success=1 #failure=3
    Readiness:    http-get http://:3000/health delay=10s timeout=1s period=10s #success=1 #failure=3
    Environment:  <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-zq4hj (ro)
Conditions:
  Type           Status
  PodScheduled   False 
Volumes:
  kube-api-access-zq4hj:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
    ConfigMapName:           openshift-service-ca.crt
    ConfigMapOptional:       <nil>
QoS Class:                   Burstable
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/memory-pressure:NoSchedule op=Exists
                             node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason            Age   From               Message
  ----     ------            ----  ----               -------
  Warning  FailedScheduling  25s   default-scheduler  0/9 nodes are available: 2 Insufficient memory, 2 node(s) had untolerated taint {memory-optimized: 32GiB}, 2 node(s) had untolerated taint {node-role.kubernetes.io/infra: }, 3 node(s) had untolerated taint {node-role.kubernetes.io/master: }. preemption: 0/9 nodes are available: 2 No preemption victims found for incoming pod, 7 Preemption is not helpful for scheduling..
  Warning  FailedScheduling  2s    default-scheduler  0/9 nodes are available: 2 Insufficient memory, 2 node(s) had untolerated taint {memory-optimized: 32GiB}, 2 node(s) had untolerated taint {node-role.kubernetes.io/infra: }, 3 node(s) had untolerated taint {node-role.kubernetes.io/master: }. preemption: 0/9 nodes are available: 2 No preemption victims found for incoming pod, 7 Preemption is not helpful for scheduling..
[student@workstation ~]$ oc get pods 
NAME                          READY   STATUS    RESTARTS   AGE
need-20gib-58775b7dbf-9vsl9   0/1     Pending   0          58s
need-20gib-58775b7dbf-hf46b   0/1     Pending   0          58s
[student@workstation ~]$ oc delete project node-pools
project.project.openshift.io "node-pools" deleted
[student@workstation ~]$ 


