# kube-helm-setup
This is a sample for how to setup a helm repo in github without gh-pages. This is usable even for private repositories.


# Adding a new version or chart to this repo

```bash
$ helm package $YOUR_CHART_PATH/ # build the tgz file and copy it here
$ helm repo index . # create or update the index.yaml for repo
$ git add .
$ git commit -m 'New chart version'
```

# How to use it as a helm repo

You might know github has a raw view. So simply use the following:

```bash
$ helm repo add sample 'https://raw.githubusercontent.com/benzKSDTC/kube-helm-setup/master/'
$ helm repo update
$ helm search repo nginx
NAME                            CHART VERSION   APP VERSION     DESCRIPTION    
sample/nginx-ingress               1.40.3          0.32.0          An nginx Ingress controller that uses ConfigMap...
```

If your repo is private you can create a "Personal access tokens" and use it like:

```bash
$ helm repo add sample 'https://MY_PRIVATE_TOKEN@raw.githubusercontent.com/benzKSDTC/kube-helm-setup/master/'
```

Note: Becareful who is creating the token and what is its level of access.