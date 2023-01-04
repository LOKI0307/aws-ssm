# aws-ssm
Installation and setup guide for aws ssm agent for target remote machine

Agenda:- using aws system manager with ssm-agent to execute commands/scripts on multiple remote servers.

Prerequisite:- 
1) you should have aws account with admin access or aws account with aws system manager full access.
2) target server(it could be bare matel , vm or cloud server). Here we are using aws linux server as a target server.

steps:-
step 1) create activation code and activation id using "hybrid activation" in aws system manager.
step 2) Install amazon ssm agent and configure it on target remote machine. login into target machine and run below command.

mkdir /tmp/ssm
cd /tmp/ssm
wget https://s3.amazonaws.com/ec2-downloads-windows/SSMAgent/latest/debian_amd64/amazon-ssm-agent.deb
sudo dpkg -i amazon-ssm-agent.deb
sudo start amazon-ssm-agent
sudo status amazon-ssm-agent
sudo service amazon-ssm-agent stop
sudo -E amazon-ssm-agent -register -code "activation_code" -id "activation_id" -region "aws_region" 
sudo service amazon-ssm-agent start

step 3) varify added target machine in "fleet manager" in aws system manager. It should be online.

step 4) configure execution command for remote server using "run command" in aws system manager.
sample script:-
#!/bin/bash
mkdir test
cd test
touch sample.txt
echo "Hello world" >> sample.txt

step 5) run configured command.
-------------------------------------------------------
###########Thank you###############
Please like and share this video
This installation document is available at below git link
https://github.com/LOKI0307/Helm-installation
