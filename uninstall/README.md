[student@workstation ~]$ rosa list cluster
ID                                NAME      STATE  TOPOLOGY
2e7hgds6t2ps7st0llufqfipkkhbuv0f  cs220lws  ready  Classic (STS)
[student@workstation ~]$ rosa delete cluster -c cs220lws
? Are you sure you want to delete cluster cs220lws? Yes
I: Cluster 'cs220lws' will start uninstalling now
I: Your cluster 'cs220lws' will be deleted but the following objects may remain
I: Operator IAM Roles: - arn:aws:iam::210940124124:role/cs220lws-openshift-machine-api-aws-cloud-credentials
 - arn:aws:iam::210940124124:role/cs220lws-openshift-cloud-credential-operator-cloud-credential-op
 - arn:aws:iam::210940124124:role/cs220lws-openshift-image-registry-installer-cloud-credentials
 - arn:aws:iam::210940124124:role/cs220lws-openshift-ingress-operator-cloud-credentials
 - arn:aws:iam::210940124124:role/cs220lws-openshift-cluster-csi-drivers-ebs-cloud-credentials
 - arn:aws:iam::210940124124:role/cs220lws-openshift-cloud-network-config-controller-cloud-credent

I: OIDC Provider : https://cs220lws-oidc-i8e4.s3.ap-southeast-2.amazonaws.com

I: Once the cluster is uninstalled use the following commands to remove the above aws resources.

	rosa delete operator-roles --prefix cs220lws
	rosa delete oidc-provider --oidc-config-id 2e7gk7ej17drc4n91u2pupiau17tqgf7
I: To watch your cluster uninstallation logs, run 'rosa logs uninstall -c cs220lws --watch'
[student@workstation ~]$ rosa list cluster
ID                                NAME      STATE         TOPOLOGY
2e7hgds6t2ps7st0llufqfipkkhbuv0f  cs220lws  uninstalling  Classic (STS)
[student@workstation ~]$ rosa list cluster
ID                                NAME      STATE         TOPOLOGY
2e7hgds6t2ps7st0llufqfipkkhbuv0f  cs220lws  uninstalling  Classic (STS)
[student@workstation ~]$ rosa list cluster
ID                                NAME      STATE         TOPOLOGY
2e7hgds6t2ps7st0llufqfipkkhbuv0f  cs220lws  uninstalling  Classic (STS)
[student@workstation ~]$ watch -d rosa list cluster
[student@workstation ~]$ rosa list cluster
I: No clusters available
[student@workstation ~]$ rosa delete operator-roles --prefix cs220lws
? Operator roles deletion mode: manual
I: Fetching operator roles for the prefix: cs220lws
I: Run the following commands to delete the Operator roles and policies:

aws iam detach-role-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-cloud-credential-operator-cloud-credential-op \
	--role-name cs220lws-openshift-cloud-credential-operator-cloud-credential-op
aws iam delete-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-cloud-credential-operator-cloud-credential-op
aws iam delete-role \
	--role-name cs220lws-openshift-cloud-credential-operator-cloud-credential-op
aws iam detach-role-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-cloud-network-config-controller-cloud-credent \
	--role-name cs220lws-openshift-cloud-network-config-controller-cloud-credent
aws iam delete-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-cloud-network-config-controller-cloud-credent
aws iam delete-role \
	--role-name cs220lws-openshift-cloud-network-config-controller-cloud-credent
aws iam detach-role-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-cluster-csi-drivers-ebs-cloud-credentials \
	--role-name cs220lws-openshift-cluster-csi-drivers-ebs-cloud-credentials
aws iam delete-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-cluster-csi-drivers-ebs-cloud-credentials
aws iam delete-role \
	--role-name cs220lws-openshift-cluster-csi-drivers-ebs-cloud-credentials
aws iam detach-role-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-image-registry-installer-cloud-credentials \
	--role-name cs220lws-openshift-image-registry-installer-cloud-credentials
aws iam delete-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-image-registry-installer-cloud-credentials
aws iam delete-role \
	--role-name cs220lws-openshift-image-registry-installer-cloud-credentials
aws iam detach-role-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-ingress-operator-cloud-credentials \
	--role-name cs220lws-openshift-ingress-operator-cloud-credentials
aws iam delete-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-ingress-operator-cloud-credentials
aws iam delete-role \
	--role-name cs220lws-openshift-ingress-operator-cloud-credentials
aws iam detach-role-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-machine-api-aws-cloud-credentials \
	--role-name cs220lws-openshift-machine-api-aws-cloud-credentials
aws iam delete-policy \
	--policy-arn arn:aws:iam::210940124124:policy/cs220lws-openshift-machine-api-aws-cloud-credentials
aws iam delete-role \
	--role-name cs220lws-openshift-machine-api-aws-cloud-credentials
[student@workstation ~]$ rosa delete operator-roles --prefix cs220lws
? Operator roles deletion mode: auto
I: Fetching operator roles for the prefix: cs220lws
? Delete the operator role 'cs220lws-openshift-cloud-credential-operator-cloud-credential-op'? Yes
I: Deleting operator role 'cs220lws-openshift-cloud-credential-operator-cloud-credential-op'
? Delete the operator role 'cs220lws-openshift-cloud-network-config-controller-cloud-credent'? Yes
I: Deleting operator role 'cs220lws-openshift-cloud-network-config-controller-cloud-credent'
? Delete the operator role 'cs220lws-openshift-cluster-csi-drivers-ebs-cloud-credentials'? Yes
I: Deleting operator role 'cs220lws-openshift-cluster-csi-drivers-ebs-cloud-credentials'
? Delete the operator role 'cs220lws-openshift-image-registry-installer-cloud-credentials'? Yes
I: Deleting operator role 'cs220lws-openshift-image-registry-installer-cloud-credentials'
? Delete the operator role 'cs220lws-openshift-ingress-operator-cloud-credentials'? Yes
I: Deleting operator role 'cs220lws-openshift-ingress-operator-cloud-credentials'
? Delete the operator role 'cs220lws-openshift-machine-api-aws-cloud-credentials'? Yes
I: Deleting operator role 'cs220lws-openshift-machine-api-aws-cloud-credentials'
I: Successfully deleted the operator roles
[student@workstation ~]$ rosa delete oidc-provider --oidc-config-id 2e7gk7ej17drc4n91u2pupiau17tqgf7
? OIDC provider deletion mode: auto
? Delete the OIDC provider 'arn:aws:iam::210940124124:oidc-provider/cs220lws-oidc-i8e4.s3.ap-southeast-2.amazonaws.com'? Yes
I: Successfully deleted the OIDC provider arn:aws:iam::210940124124:oidc-provider/cs220lws-oidc-i8e4.s3.ap-southeast-2.amazonaws.com
[student@workstation ~]$ 

