# kuma-oauth2-proxy
 
This helm chart is a combination of these 2 helm charts:
- [Kuma](https://kumahq.github.io/charts)
- [Oauth2-Proxy](https://oauth2-proxy.github.io/manifests)

The combination is achieved by using the `dependencies` section in the `Chart.yaml`.
Value of each chart can be overridden by setting the corresponding value in the `values.yaml` by specifying the prefix `kuma.` or `oauth2-proxy.` respectively

# Building / Releasing this Helm chart
Before releasing this chart, please make sure to build it by running `helm dependency build`
This chart needs to be "built" due to it needing to download dependencies first