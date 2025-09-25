**HOW-TO**<br><br>
srin@srin-product-eng-1:~/irfan.m/kuma-oauth2-proxy$ **helm repo list**<br>
NAME                    URL<br>
istio                   https://istio-release.storage.googleapis.com/charts<br>
stable                  https://charts.helm.sh/stablev
bitnami                 https://charts.bitnami.com/bitnami<br>
loft                    https://charts.loft.sh<br>
vcluster                https://charts.loft.sh<br>
vcluster-platform       https://charts.loft.sh<br>
kiali                   https://kiali.org/helm-chartsv
kuma                    https://kumahq.github.io/charts<br>
grafana                 https://grafana.github.io/helm-charts<br>
<br>

$ **helm repo add oauth2-proxy https://oauth2-proxy.github.io/manifests**<br>
"oauth2-proxy" has been added to your repositories<br>
srin@srin-product-eng-1:~/irfan.m/kuma-oauth2-proxy$ helm repo list<br>
NAME                    URL<br>
istio                   https://istio-release.storage.googleapis.com/charts<br>
stable                  https://charts.helm.sh/stable<br>
bitnami                 https://charts.bitnami.com/bitnami<br>
loft                    https://charts.loft.sh<br>
vcluster                https://charts.loft.sh<br>
vcluster-platform       https://charts.loft.sh<br>
kiali                   https://kiali.org/helm-charts<br>
kuma                    https://kumahq.github.io/charts<br>
grafana                 https://grafana.github.io/helm-charts<br>
oauth2-proxy            https://oauth2-proxy.github.io/manifests<br>

srin@srin-product-eng-1:~/irfan.m/kuma-oauth2-proxy$ **helm repo update**<br>
Hang tight while we grab the latest from your chart repositories...<br>
...Successfully got an update from the "kuma" chart repository<br>
...Successfully got an update from the "kiali" chart repository<br>
...Successfully got an update from the "oauth2-proxy" chart repository<br>
...Successfully got an update from the "istio" chart repository<br>
...Successfully got an update from the "grafana" chart repository<br>
...Successfully got an update from the "vcluster-platform" chart repository<br>
...Successfully got an update from the "vcluster" chart repository<br>
...Successfully got an update from the "stable" chart repository<br>
...Successfully got an update from the "bitnami" chart repository<br>
...Successfully got an update from the "loft" chart repository<br>
Update Complete. ⎈Happy Helming!⎈<br>

srin@srin-product-eng-1:~/irfan.m/kuma-oauth2-proxy$ **helm dependency build**<br>
Hang tight while we grab the latest from your chart repositories...<br>
...Successfully got an update from the "kuma" chart repository<br>
...Successfully got an update from the "kiali" chart repositoryv
...Successfully got an update from the "oauth2-proxy" chart repository<br>
...Successfully got an update from the "istio" chart repository<br>
...Successfully got an update from the "grafana" chart repository<br>
...Successfully got an update from the "bitnami" chart repositoryv
...Successfully got an update from the "stable" chart repository<br>
...Successfully got an update from the "vcluster-platform" chart repository<br>
...Successfully got an update from the "vcluster" chart repository<br>
...Successfully got an update from the "loft" chart repository<br>
Update Complete. ⎈Happy Helming!⎈<br>
Saving 2 charts<br>
Downloading oauth2-proxy from repo https://oauth2-proxy.github.io/manifests<br>
Downloading kuma from repo https://kumahq.github.io/charts<br>
Deleting outdated charts<br>

srin@srin-product-eng-1:~/irfan.m/kuma-oauth2-proxy$ **ls -l**<br>
total 20v
-rw-r--r-- 1 srin srin  308 Jul 16 08:01 Chart.lock<br>
drwxr-xr-x 2 srin srin 4096 Jul 17 07:30 charts<br>
-rw-r--r-- 1 srin srin  385 Jul 17 07:26 Chart.yaml<br>
-rw-rw-r-- 1 srin srin  637 Jul 16 08:00 README.md<br>
-rw-rw-r-- 1 srin srin 1737 Jul 17 07:23 values.yaml<br>

srin@srin-product-eng-1:~/irfan.m/kuma-oauth2-proxy$ **cat Chart.yaml**<br>
apiVersion: v2<br>
name: oauth2-proxy-kuma<br>
description: A Helm chart which contains chart for oauth2-proxy and kuma<br>
version: 1.0.0<br>
appVersion: 1.0.0<br>
dependencies:<br>
  - name: oauth2-proxy<br>
    version: "7.7.24"<br>
    repository: "https://oauth2-proxy.github.io/manifests"<br>
    enabled: true<br>
  - name: kuma<br>
    version: "2.8.2"<br>
    repository: "https://kumahq.github.io/charts"<br>
    enabled: true<br>

srin@srin-product-eng-1:~/irfan.m/kuma-oauth2-proxy$ **helm package .**<br>
Successfully packaged chart and saved it to: /home/srin/irfan.m/kuma-oauth2-proxy/oauth2-proxy-kuma-1.0.0.tgzv

srin@srin-product-eng-1:~/irfan.m/kuma-oauth2-proxy$ **ls -l**<br>
total 212<br>
-rw-r--r-- 1 srin srin    308 Jul 16 08:01 Chart.lock<br>
drwxr-xr-x 2 srin srin   4096 Jul 17 07:30 charts<br>
-rw-r--r-- 1 srin srin    385 Jul 17 07:26 Chart.yaml<br>
-rw-rw-r-- 1 srin srin 196500 Jul 17 07:49 oauth2-proxy-kuma-1.0.0.tgz<br>
-rw-rw-r-- 1 srin srin    637 Jul 16 08:00 README.md<br>
-rw-rw-r-- 1 srin srin   1737 Jul 17 07:23 values.yaml<br>

$ **helm repo index .**<br>
$ **ls -l**<br>
total 216<br>
-rw-r--r-- 1 srin srin    308 Jul 16 08:01 Chart.lock<br>
drwxr-xr-x 2 srin srin   4096 Jul 17 07:30 charts<br>
-rw-r--r-- 1 srin srin    385 Jul 17 07:26 Chart.yaml<br>
-rw-r--r-- 1 srin srin   2901 Jul 17 07:50 index.yaml<br>
-rw-rw-r-- 1 srin srin 196500 Jul 17 07:49 oauth2-proxy-kuma-1.0.0.tgz<br>
-rw-rw-r-- 1 srin srin    637 Jul 16 08:00 README.md<br>
-rw-rw-r-- 1 srin srin   1737 Jul 17 07:23 values.yaml<br>


$ **helm repo add irfan-lib --username irfanmubasyir96 --password Your-Github-PAT https://raw.githubusercontent.com/irfanmubasyir96/kuma-oauth2-proxy/main/**<br>

"irfan-oauth2-proxy-kuma-lib" has been added to your repositories<br>

srin@srin-product-eng-1:~/irfan.m/kuma-oauth2-proxy$** helm repo update**<br>
Hang tight while we grab the latest from your chart repositories...<br>
...Successfully got an update from the "irfan-oauth2-proxy-kuma-lib" chart repository<br>
...Successfully got an update from the "kuma" chart repository<br>
...Successfully got an update from the "kiali" chart repository<br>
...Successfully got an update from the "oauth2-proxy" chart repository<br>
...Successfully got an update from the "istio" chart repository<br>
...Successfully got an update from the "grafana" chart repository<br>
...Successfully got an update from the "vcluster" chart repository<br>
...Successfully got an update from the "stable" chart repository<br>
...Successfully got an update from the "loft" chart repository<br>
...Successfully got an update from the "bitnami" chart repository<br>
...Successfully got an update from the "vcluster-platform" chart repository<br>
Update Complete. ⎈Happy Helming!⎈<br>
 


TO CREATE STATIC PAGE IN GITHUB<br>
===============================<br>
1. From Repo https://github.com/irfanmubasyir96/kuma-oauth2-proxy<br>
   Create New Branch gh-pages FROM main<br>
   
   OR:  **git checkout -b gh-pages**   (from branch "main")<br>
   
   
2. Click **Settings | Code n automation | Pages**<br>
   
   Your site is live at https://irfanmubasyir96.github.io/kuma-oauth2-proxy/   (Visit Site)=> Click!  YEAY!!!<br>
  
3. Test <br>
   **https://irfanmubasyir96.github.io/kuma-oauth2-proxy**<br>
   **https://irfanmubasyir96.github.io/kuma-oauth2-proxy/index.yaml**<br>
