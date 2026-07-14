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
provide the list of tenants name & USER_COUNT per tenant we need to create

```bash
tenant_list=("tenant_a" "tenant_b" "tenant_c" "tenant_d" "tenant_e")
USER_COUNT=20
```



Run the following commands:
```bash
cd tenant-and-user-creation
nohup ./create_tenants_users.sh &
```


the last command might take 10-15 minutes based on the the total number of tenant and user creation.

You can check the how many tenants or users created from nohup.out file

```bash
tail -n 100 nohup.out
```

When all the tenants are created then there will be a new file created 

```bash
users.csv
```

If the single run does not create any contents other than the header row then run 

```bash
tenant-and-user-creation/create_tenants_users.sh
```
again, this will add the users row in the users.csv file.

**Note: the tenantId is a dummy value, we only need the tenantSlug/name **
We need to put this users.csv file inside the load generation machine so that users can be picked randomly to run the user workflow.
