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

=========================================================================== 2nd TERMINAL ==========================================================================================================================
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
query-logs/api-cs220lws-nw83-p1-openshiftapps-com:6443/cluster-admin
[student@workstation ~]$ rosa list clusters 
roID                                NAME      STATE  TOPOLOGY
2e7hgds6t2ps7st0llufqfipkkhbuv0f  cs220lws  ready  Classic (STS)
[student@workstation ~]$ rosa describe cluster -c cs220lws | grep API 
API URL:                    https://api.cs220lws.nw83.p1.openshiftapps.com:6443
[student@workstation ~]$ oc login -u cluster-admin -p Redhattraining123 https://api.cs220lws.nw83.p1.openshiftapps.com:6443 
Login successful.

You have access to 100 projects, the list has been suppressed. You can list all projects with 'oc projects'

Using project "default".
[student@workstation ~]$ wget https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/aws/cloudformation/cognito-idp.yaml
--2024-10-06 15:09:27--  https://raw.githubusercontent.com/RedHatTraining/CS22X-apps/main/aws/cloudformation/cognito-idp.yaml
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.110.133, 185.199.111.133, 185.199.108.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.110.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5959 (5.8K) [text/plain]
Saving to: ‘cognito-idp.yaml’

cognito-idp.yaml                                     100%[=====================================================================================================================>]   5.82K  --.-KB/s    in 0s      

2024-10-06 15:09:28 (82.2 MB/s) - ‘cognito-idp.yaml’ saved [5959/5959]

[student@workstation ~]$ cat cognito-idp.yaml 
---
AWSTemplateFormatVersion: "2010-09-09"
Description: >
  This template creates Amazon Cognito resources for the guided exercise.

Parameters:
  RosaStackName:
    Description: >
      Name of the stack that deployed the AWS infrastructure
      for the ROSA cluster.
    Type: String
  ClusterDomain:
    Description: >
      DNS domain of the ROSA cluster. Run the
      "rosa describe cluster -c cs220yourname" command to retrieve that DNS
      domain. The domain is provided in the "DNS" attribute.
    Type: String

Resources:
  # Cognito user pool
  rCognitoUserPool:
    Type: AWS::Cognito::UserPool
    Properties:
      UserPoolName:
        Fn::Join:
          - ""
          - - Fn::ImportValue:
                !Join [":", [!Ref RosaStackName, RosaClusterName]]
            - "-user-pool"
      AutoVerifiedAttributes:
        - email
      AdminCreateUserConfig:
        AllowAdminCreateUserOnly: true
      Policies:
        PasswordPolicy:
          MinimumLength: 6
          TemporaryPasswordValidityDays: 365
      UserPoolTags:
        "redhattraining:course-sku": CS220-cognito
  # Create user pool Domain
  rCognitoUserPoolDomain:
    Type: AWS::Cognito::UserPoolDomain
    DependsOn: rCognitoUserPool
    Properties:
      Domain:
        Fn::ImportValue: !Join [":", [!Ref RosaStackName, RosaClusterName]]
      UserPoolId:
        Ref: rCognitoUserPool
  # Create users for Cognito
  rCognitoUserPoolUserAmelia:
    Type: AWS::Cognito::UserPoolUser
    DependsOn: rCognitoUserPool
    Properties:
      Username: amroy
      UserAttributes:
        - Name: preferred_username
          Value: amroy
        - Name: name
          Value: Amelia Roy
        - Name: email
          Value: amroy@cs220cluster
        - Name: email_verified
          Value: true
      UserPoolId:
        Ref: rCognitoUserPool
  rCognitoUserPoolUserSue:
    Type: AWS::Cognito::UserPoolUser
    DependsOn: rCognitoUserPool
    Properties:
      Username: smoody
      UserAttributes:
        - Name: preferred_username
          Value: smoody
        - Name: name
          Value: Sue Moody
        - Name: email
          Value: smoody@cs220cluster
        - Name: email_verified
          Value: true
      UserPoolId:
        Ref: rCognitoUserPool
  rCognitoUserPoolUserRoberto:
    Type: AWS::Cognito::UserPoolUser
    DependsOn: rCognitoUserPool
    Properties:
      Username: rruiz
      UserAttributes:
        - Name: preferred_username
          Value: rruiz
        - Name: name
          Value: Roberto Ruiz
        - Name: email
          Value: rruiz@cs220cluster
        - Name: email_verified
          Value: true
      UserPoolId:
        Ref: rCognitoUserPool
  # Create groups for Cognito
  rCongnitoUserPoolGroupManagers:
    Type: AWS::Cognito::UserPoolGroup
    DependsOn: rCognitoUserPool
    Properties:
      GroupName: managers
      Description: Group for Managers
      UserPoolId:
        Ref: rCognitoUserPool
  rCongnitoUserPoolGroupDevelopers:
    Type: AWS::Cognito::UserPoolGroup
    DependsOn: rCognitoUserPool
    Properties:
      GroupName: developers
      Description: Group for Developers
      UserPoolId:
        Ref: rCognitoUserPool
  rCongnitoUserPoolGroupOperations:
    Type: AWS::Cognito::UserPoolGroup
    DependsOn: rCognitoUserPool
    Properties:
      GroupName: operations
      Description: Group for Operations
      UserPoolId:
        Ref: rCognitoUserPool
  rCognitoUserToGroupManagers:
    Type: AWS::Cognito::UserPoolUserToGroupAttachment
    DependsOn:
      - rCognitoUserPool
      - rCongnitoUserPoolGroupManagers
    Properties:
      GroupName: managers
      Username: amroy
      UserPoolId:
        Ref: rCognitoUserPool
  rCognitoUserToGroupDevelopers:
    Type: AWS::Cognito::UserPoolUserToGroupAttachment
    DependsOn:
      - rCognitoUserPool
      - rCongnitoUserPoolGroupDevelopers
    Properties:
      GroupName: developers
      Username: smoody
      UserPoolId:
        Ref: rCognitoUserPool
  rCognitoUserToGroupOperations:
    Type: AWS::Cognito::UserPoolUserToGroupAttachment
    DependsOn:
      - rCognitoUserPool
      - rCongnitoUserPoolGroupOperations
    Properties:
      GroupName: operations
      Username: rruiz
      UserPoolId:
        Ref: rCognitoUserPool
  # Cognito user pool client
  rCognitoUserPoolClient:
    Type: AWS::Cognito::UserPoolClient
    DependsOn:
      - rCognitoUserPool
    Properties:
      UserPoolId:
        Ref: rCognitoUserPool
      ClientName:
        Fn::Join:
          - ""
          - - Fn::ImportValue:
                !Join [":", [!Ref RosaStackName, RosaClusterName]]
            - "-user-pool-client"
      GenerateSecret: true
      SupportedIdentityProviders:
        - COGNITO
      CallbackURLs:
        - Fn::Join:
            - ""
            - - "https://oauth-openshift.apps."
              - !Ref ClusterDomain
              - "/oauth2callback/Cognito"
      LogoutURLs:
        - Fn::Join:
            - ""
            - - "https://console-openshift-console.apps."
              - !Ref ClusterDomain
      AllowedOAuthFlowsUserPoolClient: true
      AllowedOAuthScopes:
        - email
        - openid
        - profile
        - aws.cognito.signin.user.admin
      AllowedOAuthFlows:
        - code

Outputs:
  oUserPoolId:
    Description: Pool ID
    Value:
      Ref: rCognitoUserPool
  oUserPoolClientId:
    Description: >
      Client ID. Use that ID for the --client-id option of the "rosa create idp"
      command.
    Value:
      Ref: rCognitoUserPoolClient
  oIssuerURL:
    Description: >
      Issuer URL. Use that URL for the --issuer-url option of the
      "rosa create idp" command.
    # https://cognito-idp.<AWS::Region>.amazonaws.com/<rCognitoUserPool>
    Value:
      Fn::Join:
        - "/"
        - - Fn::Join:
              - "."
              - - "https://cognito-idp"
                - !Ref "AWS::Region"
                - "amazonaws.com"
          - !Ref rCognitoUserPool
[student@workstation ~]$ rosa describe cluster -c cs220lws | grep DNS 
DNS:                        cs220lws.nw83.p1.openshiftapps.com
[student@workstation ~]$ complete -C '/usr/local/bin/aws_completer' aws 
[student@workstation ~]$ aws cloudformation create-stack --stack-name cognito-lws --template-body file://./cognito-idp.yaml --parameters ParameterKey=RosaStackName,ParameterValue=ROSA-infra-lws ParameterKey=ClusterDomain,ParameterValue=cs220lws.nw83.p1.openshiftapps.com
{
    "StackId": "arn:aws:cloudformation:ap-southeast-2:210940124124:stack/cognito-lws/eea62eb0-8416-11ef-866b-027cf385a91b"
}
[student@workstation ~]$ aws cloudformation describe-stacks --stack-name cognito-lws --output text --query "Stacks[0].StackStatus"
CREATE_COMPLETE
[student@workstation ~]$ 

