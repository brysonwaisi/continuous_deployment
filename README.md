# Continuous Deployment using Ansible

Here's a sneak of the folder structure
```
.
├── main.yml                # Playbbook file
└── roles
   └── print
       └── tasks
           └── main.yml    # Task file
```

### Build inventory file 

Have AWS CLI installed and configured

First create the file and add [all] at the beginning

```
touch inventory
echo [all] > inventory
```

Run the following in the terminal
```
aws ec2 describe-instances \
\
        --query 'Reservations[*].Instances[*].PublicIpAddress' \
      --filters "Name=tag:Project,Values=breezy" \
      --output text >> inventory
```
### Remote Control Using Ansible
Configuring an EC2 instance to run a Node.js 13.8.0 simple server

run in the terminal after setup
```
ansible-playbook main-remote.yml -i inventory --private-key [file].pem
```

