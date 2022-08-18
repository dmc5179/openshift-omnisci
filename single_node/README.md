
The default database and username changed in 4.8
use the newer servers.json file

- Without any added service accounts, heavy must run with anyuid

```
oc adm policy add-scc-to-user anyuid -z default
```

- Need to determine the new default password. Used to be:
<      "database": "mapd",
---
>      "database": "omnisci",
7c7
<      "username": "mapd",
---
>      "username": "admin",


- If you want to customize the login screen, change heavy.conf to include the servers-json reference

```
   heavy.conf: |
     port = 6274
     http-port = 6278
     calcite-port = 6279
     data = "/heavyai-storage/data"
     read-only = false
     verbose = false
     
     [web]
     port = 6273
     frontend = "frontend"
     servers-json = "/heavyai-storage/servers.json"
```
