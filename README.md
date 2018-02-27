# lnk

A bosh release that provides a link.

```
bbl up
bosh upload-release
bosh deploy -d manifests/lnk.yml
```

## manifests

### manifests/lnk-cluster.yml

This is a base manifest with 3 instances running the lnk job
that provide and consume the same properties.

### manifests/lnk.yml

This is a zero-instance deployment with a lnk job that provides
a link that can be consumed by other deployments deployed
to that director.

### manifests/lnk-consumer.yml

This is the consumer deployment compatible with the above
zero-instance lnk deployment.

### manifests/lnk-runtime.yml

This is the runtime config to be updated on the bosh director
that will add a job to the instances of all deployments
(unless there are include/exclude rules specified) that
can be consumed.

Note: this requires a specific version of the release
due to this related [issue](https://github.com/cloudfoundry/bosh-cli/issues/57).

### manifests/lnk-runtime-consumer.yml

This is the consumer deployment compatible with the above
runtime-config.
