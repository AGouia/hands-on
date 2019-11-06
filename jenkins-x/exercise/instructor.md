# Guided Tour Auto Promotion
1. Pick a pull request from the participants to perform this.
2. Merge the pull request to the master.
3. Check the pipelines (PR on staging and push to master followed by a redeployment of the [application](http://micro.jx-staging.cloud-poc-station.com) that are triggered (We disabled the Preview environment for the master to lower resource consumption) 

# Guided Tour Manual Promotion 
Manually (using git ops) promote the application from the staging environment to the production environment.
1. Create branch
1. Update requirements.yaml
1. Create PR
1. Check PR pipeline
1. Check application (Not changed or not present)
1. Merge to master
1. Check Master Pipeline
1. Check application (changed)
  
Useful commands
```
jx get applications
jx get activities -f master -w
```