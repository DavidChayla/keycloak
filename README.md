# keycloak

If you're looking into the open source Identity and Access Management ecosystem, chances are that you're found keycloak.

You could find it difficult or cumberstone to install and configure. And suprisingly i didn't find a good cloud formation template to help me.

So here it is, a fully functional keycloak cloudformation ready to go live.

Features:
- a keycloak v11.0.2
- an ubuntu 20.04 LTS ami 
- an external dns name registered on your domain on route53 
- an https public endpoint based on your ssl certificate (through aws certificate manager)
- an http public endpoint that redirect to the https one
- multiples keycloak instances behind an ALB, working as a wildfly cluster with autodiscovered nodes (JDBC_PING)
- a mysql 5.6 aurora DB in a cluster


Prerequisites:
- only the eu-west-3 ubuntu 20.04 LTS ami is set, if you're using another region, add it in AWSRegionArch2AMI
- it assumes that your aws internal network is in the 10.0.0.0/8 network, if not adapt the InstanceSecurityGroup


Be careful:
- there's no ip filtering for the external https access, please adapt the ALBSecurityGroup to only accept your public ip address

Hope that this will be helpful
