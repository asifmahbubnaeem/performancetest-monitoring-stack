Clone this repo to the ec2 host where the advance app is deployed.

Run the following commands:

```bash
cd {cloned_dir}
cp .env.example .env
chmod +x setup.sh
cd tenant-and-user-creation
chmod +x create_tenants_users.sh
```

Update the `.env` file.

Run the following commands:

```bash
cd ..
./setup.sh
```

update the tenant-and-user-creation/create_tenants_users.sh file

Run the following commands:
```bash
cd tenant-and-user-creation
nohup ./create_tenants_users.sh &
```


the last command might take 10-15 minutes based on the the total number of tenant and user creation.

