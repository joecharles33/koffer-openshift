# Koffer OpenShift Artifact Collection
### 1. Clone into koffer directory
```
git clone https://github.com/containercraft/koffer-openshift.git /tmp/koffer
```
### 2. Run Koffer
```
sudo podman run \
    --rm -qit -h koffer --name koffer     \
    --pull=always --entrypoint entrypoint \
    --volume ~/.docker:/root/.docker      \
    --volume /tmp/koffer:/root/koffer:z   \
  docker.io/containercraft/koffer:latest
```
  - optional: volume mount quay pull secret from host    
    `--volume ~/.docker:/root/.docker/`
### 3. Move Koffer Bundle to target host /tmp directory
### 4. Aquire root & unpack tarball
```
sudo -i
```
```
tar -xv -C /root -f /tmp/koffer-bundle.*.tar
```
### 5. Run CloudCtl stand up script
```
 ./start-cloudctl.sh
```
#### 6. Exec into CloudCtl
```
 podman exec -it cloudctl-one connect
```
# [Developer Docs & Utils](./dev)
# Demo
![bundle](./web/bundle.svg)
