
# Additional steps to get auth working: 

0. Create profile after deploying kf, see ./profile.yaml for example
1. Rename user to kf user in ./rbac/runs-rb.yaml and update the namespace to match the kf username namespace
2. Dex userid --> hukhan@redhat.com (not 100% is this is needed)
3. Create pipeline-runner in KF user namespace: 
```yaml
kind: ServiceAccount
apiVersion: v1
metadata:
  name: pipeline-runner
  namespace: <user-name> 
```
4. Remove quota (or add limit range) from kf usernamespace (otherwise flip-coin will fail)

Dex default password in config is hashed, it's actual value is: `12341234` (dex password)