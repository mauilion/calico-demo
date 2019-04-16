### Installing metallb

Docs are here: https://metallb.universe.tf/installation/

tldr;

kubectl apply -f https://raw.githubusercontent.com/google/metallb/master/manifests/metallb.yaml

to install metallb and kubectl apply -f [l2-config.yaml](./l2-config.yaml) to configure it.