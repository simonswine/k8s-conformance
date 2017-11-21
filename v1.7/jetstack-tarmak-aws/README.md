## To reproduce:

#### Create Kubernetes Cluster

TODO: add instructions

#### Launch E2E Conformance Tests

1. Launch e2e pod and sonobuoy master under namespace `sonobuoy`.

 ```
 tarmak kubectl apply -f https://raw.githubusercontent.com/cncf/k8s-conformance/master/sonobuoy-conformance.yaml
 ```

2. Check logs of `sonobuoy` pod to see when test can be finished.

 ```
 tarmak kubectl logs -f -n sonobuoy sonobuoy
 ```

 wait for line `no-exit was specified, sonobuoy is now blocking`.

3. Use `kubectl cp` to bring the results to local machine.

 ```
 tarmak kubectl cp sonobuoy/sonobuoy:/tmp/sonobuoy /tmp/sonobuoy-result
 ```

4. Delete the conformance test resources.

 ```
 tarmak kubectl delete -f -
 ```

5. Untar the tarball

 ```shell
 cd /tmp/sonobuoy-result
 tar -xzf *_sonobuoy_*.tar.gz
 ```

 In `plugins/e2e/results/` you can find e2e result logs and other relative output files.
