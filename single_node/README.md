
The default database and username changed in 4.8
use the newer servers.json file

- Without any added service accounts, heavy must run with anyuid

```
oc adm policy add-scc-to-user anyuid -z default
```
