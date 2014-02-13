# BOSH Release for example-docker-usage

WIP. This is an experiment in how a set of Docker repositories can be created, packaged and then run within a BOSH deployment on AWS, OpenStack or vSphere.

## Usage

To use this bosh release, first upload it to your bosh:

```
bosh target BOSH_HOST
git clone https://github.com/cloudfoundry-community/example-docker-usage-boshrelease.git
cd example-docker-usage-boshrelease
bosh upload release releases/example-docker-usage-1.yml
```

For [bosh-lite](https://github.com/cloudfoundry/bosh-lite), you can quickly create a deployment manifest & deploy a 3 VM cluster:

```
templates/make_manifest warden
bosh -n deploy
```

For Openstack (Nova Networks), create a single VM:

```
templates/make_manifest openstack-nova
bosh -n deploy
```

For AWS EC2, create a single VM:

```
templates/make_manifest aws-ec2
bosh -n deploy
```

### Override security groups

For AWS & Openstack, the default deployment assumes there is a `default` security group. If you wish to use a different security group(s) then you can pass in additional configuration when running `make_manifest` above.

Create a file `my-networking.yml`:

``` yaml
---
networks:
  - name: example-docker-usage1
    type: dynamic
    cloud_properties:
      security_groups:
        - example-docker-usage
```

Where `- example-docker-usage` means you wish to use an existing security group called `example-docker-usage`.

You now suffix this file path to the `make_manifest` command:

```
templates/make_manifest openstack-nova my-networking.yml
bosh -n deploy
```
