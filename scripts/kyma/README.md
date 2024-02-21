## Deploy to Kyma

Download the kubeconfig from your Kyma instance via the menu behind the account Icon in the upper right corner. Save it in _~/.kube/kubeconfig-kyma.yml_. Then run:

`export KUBECONFIG=~/.kube/kubeconfig-kyma.yml`

Please note that the token in the kubeconfig is [only valid for 8 hours](https://kyma-project.io/docs/components/security#details-iam-kubeconfig-service). So you might have to redo the download whenever you want to run the commands again.

To keep this project separate from your other deployments I would suggest to create a namespace:

`kubectl create namespace request-baskets`

Deploy the configuration:

`kubectl -n request-baskets apply -f scripts/kyma/deployment.yaml`

Update the container:

`kubectl -n request-baskets rollout restart deployment/request-baskets`

If you want to delete the deployment, then run:

`kubectl -n request-baskets delete -f scripts/kyma/deployment.yaml`
