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