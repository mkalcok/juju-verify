# Juju verify

This CLI tool is a Juju plugin that allows user to check whether it's safe
to perform some disruptive maintenance operations on Juju units, like `shutdown`
or `reboot`.

## Supported charms

* nova-compute (Usable with the next stable release of the charm. Currently available as a [pre-release](https://jaas.ai/u/openstack-charmers-next/nova-compute/562))
* ceph-osd (WIP)
* neutron-gateway (WIP)

## Supported checks

* reboot
* shutdown

**NOTE:** Final list of supported checks and what they represent is still WIP

## Contribution and lifecycle

For more information on how to contribute and the lifecycle of ``juju-verify`` tools,
visit [CONTRIBUTING] page.

## Usage example

To verify that it is safe to stop/shutdown units `nova-compute/0` and
`nova-compute/1` without affecting the rest of the OpenStack cloud environment,
run the following.

```bash
$ juju-verify shutdown --units nova-compute/0 nova-compute/1
```

**NOTE:** If you run check on multiple units at the same time, they must all run
the same charm. Trying, for example, `juju-verify shutdown --units nova-compute/1
ceph-osd/0` will result in error.

Alternatively, a machine can be targeted:

```bash
$ juju-verify shutdown --machines 0
```

## Submit a bug

If you prefer, file a bug or feature request at:

* https://bugs.launchpad.net/juju-verify


[CONTRIBUTING]: https://juju-verify.readthedocs.io/en/latest/contributing.html
