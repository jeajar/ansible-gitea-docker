# Gitea docker swarm production ready deployment

Install Ansible and Python requirements:
```
$ pip3 install -r requirements.txt
```
Install required ansible-galaxy requirements:
```
$ ansible-galaxy install -r provisioning/requirements.yml
```

## Production deployment
Create a new ansible vault to store the `db_password` variable
```
$ ansible-vault create vault
```

edit the vault with the following content:
```
$ ansible-vault edit vault.yml
Vault password:
```

```
db_password: your_secure_postgres_password
```
Modify the `provisioning/vars.yml` file to suite your needs and edit the `provisioning/inventory.yml` with your host(s).

## Testing and developement
The Vagrantfile is configured to use the `provisioning/vars-dev.yml` file and insecure passwords.