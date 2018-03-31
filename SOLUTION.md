Link to my fork of dataengi/crm-seed - https://github.com/vleskiv/crm-seed

Branch for task1 - https://github.com/vleskiv/crm-seed/tree/task1

1) Make VM using Vagrant (v2.0.1) configuration file should be in root directory (OS: CentOS 7.4)
Install vagrant, virtual box and "cd" to folder with Vagrantfile
"vagrant box update"
"vagrant plugin install vagrant-vbguest" for mounts with type: "virtualbox" (on the host OS)
"vagrant up"

2) Install required tools and docker (v17.09.1-ce) in VM
sudo yum update -y
sudo yum install -y epel-release
sudo yum install -y wget nano mc ntsysv htop
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install -y docker-ce-17.09.1.ce-1.el7.centos
sudo systemctl enable docker && sudo systemctl start docker
sudo yum install -y python-pip && pip install --upgrade pip
sudo pip install docker-compose

sudo yum -y install ansible

3) Deploy project in presentation mode (docker-compose.yml)
Project folder: /interviewtasks/crm-seed
sudo yum install -y git
# git clone https://github.com/vleskiv/crm-seed.git /interviewtasks/crm-seed

# run project in presentation mode
sudo docker-compose -f /interviewtasks/crm-seed/docker-compose.yml up

4) Push result to my fork of https://github.com/dataengi/crm-seed and Add link to your fork in SOLUTION.md
git checkout task1
cp /vagrant/Vagrantfile /interviewtasks/crm-seed/Vagrantfile
nano /interviewtasks/crm-seed/SOLUTION.md
git add -A && git status
git commit -m "task1 commit"
git push -u origin task1

