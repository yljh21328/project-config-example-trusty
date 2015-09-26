# Example project-config repository

This is an example project-config repository for use as a
starting point to setup a 3rd party CI account.

## Steps to begin customization

The project-config repository is intended to contain custom configurations
needed by each CI system.

## Customize Zuul

The zuul layout configuration is located in `zuul/layout.yaml`. You can find
the full configuration details in the [Zuul manual](http://docs.openstack.org/infra/zuul/).

1. Change 'myvendor' in the 'recheck' command to your CI's name.

2. Configure the e-mail addresses for merge-failures and job notification.

3. By default, the project zuul triggers on is `openstack-dev/ci-sandbox`.
   After testing your CI system update this section to include other projects.
   You are encouraged to use the 'silent' pipeline until your jobs are stable.

## Customize Nodepool

The nodepool configuration is located in `nodepool/nodepool.yaml`. You can
find the full configuration details in the [Nodepool manual](http://docs.openstack.org/infra/nodepool/).
There are a few configuration that need to be updated.

1. There are some user names and passwords that need to be configured.

2. Select a 'random time' for your nodepool images to be built in the
   `image-update` property. By having 3rd party systems use different
   times will help reduce the spike load on OpenStack's Git servers.

3. Setup an intial set of nodepool scripts and elements. Start by cloning
   OpenStack's [project-config](https://git.openstack.org/cgit/openstack-infra/project-config/)
   and copy the contents of that repo's `nodepool/elements` to your repo's
   `nodepool/elements`. Optionally do the same for the `nodepool/scripts`
   folder. You may have to change these elements to work in your environment.
   If so, see this [README](http://git.openstack.org/cgit/openstack-infra/project-config/tree/nodepool/elements/README.rst)
   for help.

## Customize Jenkins Jobs

Adjust the jenkins jobs in `jenkins/jobs/` to your needs. You can find the full configuration details in the
[Jenkins Job Builder manual](http://docs.openstack.org/infra/jenkins-job-builder/)

1. Change the value of the `$PUBLISH_HOST` to the host (without https:// prefix) you will publish
   job artifacts to. This is also known as the Log server. You can set one up using [this script]



