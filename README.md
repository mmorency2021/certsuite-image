#How to run the test using container 

## First , create two directory results and config 
## put under config directory the config file for the test 
see below exemple 

```yaml
$ cat certsuite_config.yml 
targetNameSpaces:
    - name: valkey

```

## dont forget to upload the image ( .tar) to your registry 


```bash
podman run --rm --network host -v /root/certsuite/config/:/usr/certsuite/config/:Z -v /root/certsuite/results/:/usr/certsuite/results/:Z quay.io/redhat-best-practices-for-k8s/certsuite:latest certsuite run -l all  -k /usr/certsuite/config/kubeconfig -c /usr/certsuite/config/certsuite_config.yml -o /usr/certsuite/results –intrusive=false --certsuite-probe-image quay.io/redhat-best-practices-for-k8s/certsuite-probe:latest
```

## after share will us the containt of the results directory 

## if for some reason the command doesnt work without the option -k , know that once you login using oc cmd, it updated to an ~/.config/kubeconfig.  copy that file to your config directory. 

