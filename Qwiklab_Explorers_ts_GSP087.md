# Autoscaling an Instance Group with Custom Cloud Monitoring Metrics || [GSP087](https://www.cloudskillsboost.google/games/5383/labs/34947) ||

# # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

### Run the following Commands in CloudShell

```
export ZONE=
```
```
gsutil mb gs://$DEVSHELL_PROJECT_ID
gsutil cp -r gs://spls/gsp087/* gs://$DEVSHELL_PROJECT_ID
gcloud compute instance-templates create autoscaling-instance01 --metadata=startup-script-url=gs://$DEVSHELL_PROJECT_ID/startup.sh,gcs-bucket=gs://$DEVSHELL_PROJECT_ID
gcloud beta compute instance-groups managed create autoscaling-instance-group-1 --project=$DEVSHELL_PROJECT_ID --base-instance-name=autoscaling-instance-group-1 --size=1 --template=projects/$DEVSHELL_PROJECT_ID/global/instanceTemplates/autoscaling-instance01 --zone=$ZONE --list-managed-instances-results=PAGELESS --no-force-update-on-repair --default-action-on-vm-failure=repair && gcloud beta compute instance-groups managed set-autoscaling autoscaling-instance-group-1 --project=$DEVSHELL_PROJECT_ID --zone=$ZONE --cool-down-period=60  --max-num-replicas=3 --min-num-replicas=1 --mode=on --target-cpu-utilization=0.6 --stackdriver-metric-filter=resource.type\ =\ \"gce_instance\" --update-stackdriver-metric=custom.googleapis.com/appdemo_queue_depth_01 --stackdriver-metric-utilization-target=150.0 --stackdriver-metric-utilization-target-type=gauge
```

# Congratulations ..!!🎉  You completed the lab shortly..😃💯

# *Well done..!* 👏

# Thank you for visiting.... :) 🗯️

# [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN)
