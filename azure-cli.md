# azure-cli-magic
Useful azure-cli commands (MS Azure)

### Authorize
```
$ az login --allow-no-subscriptions
The default web browser has been opened at https://login.microsoftonline.com/common/oauth2/authorize. Please continue the login in the web browser. If no web browser is available or if the web browser fails to open, use device code flow with `az login --use-device-code`.
You have logged in. Now let us find all the subscriptions to which you have access...
The following tenants don't contain accessible subscriptions. Use 'az login --allow-no-subscriptions' to have tenant level access.
```

### List group members
```
$ az ad group member list --group <group_name> | grep userPrincipalName | awk '{print $2}' | tr -d \"
```

### List users objectID
```
$ az ad group member list --group <group_name> | grep objectId | awk '{print $2}' | tr -d \"
```

### Add user to group
```
$ az ad group member add --group <group_name> --member-id <objectId>
```

### List the number of users in group

Currently, if there are more than 200 users in one group, it’s impossible to check the number of all users via GUI. 
However, it’s able to check it via azure cli.

#### Count users using azure cli
```
$  az ad group member list --group <group_name> | grep objectId | wc -l
```


