# Edge Workshop

The instructions for this workshop assume that you have used the automation
provided in this repository to deploy the infrastructure and configure it
accordingly.

## Accessing The Environment

The easiest way to access the environment is using the Cockpit interface that
has been deployed on your machine. The Cockpit interface contains a
browser-based terminal interface and other UI elements to make connecting to
the machine and running commands easier to do.

You can find the Cockpit interface at `https://${HOSTNAME}:9090`.
  - Change the 'NN' to your number:
  ```
  https://microshift-NN.sandbox1567.opentlc.com:9090 
  ```
  
For example, if your hostname is `microshift-example.sandbox.opentlc.com` then
you would access the Cockpit interface by going to
`https://microshift-example.sandbox.opentlc.com:9090`

Your lab instructor will provide you with the username and password.

If you prefer to SSH directly into the machine, you can also access the machine
using the same hostname on port 22. The username and password provided by your
lab instructor will be the same for SSH and password authentication is enabled.

## Getting Started

At this point in time, this workshop and the steps you need to do is expected
to be driven verbally by your lab instructor. However, many of these verbal
instructions will point you to parts of the documentation as well as
instructions or examples contained in this repository. Check out the links
below for easy access to the documentation pages when your lab instructor
guides you to do so.

- [MicroShift 4.13
  Documentation](https://access.redhat.com/documentation/en-us/red_hat_build_of_microshift/4.13)
- [MicroShift 4.13
  Installation](https://access.redhat.com/documentation/en-us/red_hat_build_of_microshift/4.13/html-single/installing)
- [MicroShift 4.13
  Configuration](https://access.redhat.com/documentation/en-us/red_hat_build_of_microshift/4.13/html-single/configuring)

## Installation

To install MicroShift, we will be referring to the installation documentation
found here:

https://access.redhat.com/documentation/en-us/red_hat_build_of_microshift/4.13/html-single/installing/index#installing-microshift-from-rpm-package_microshift-install-rpm

We will be starting with **Section 1.4**.

The previous sections describe how to provision RHEL 9, which has already been
done for you. The RHEL 9 hosts have also already been subscribed to Red Hat so
you are ready to start with enabling the required repositories.

When you get to **Step 4** where it asks you to download your pull secret from
the Cloud Console, you can skip this step as a pull secret has already been
placed at `$HOME/openshift-pull-secret` for you.

You can also skip **Step 8** where it asks you to open ports in firewalld
because firewalld is not enabled on these systems.

## Helpful Examples

Here are some helpful examples for when your lab instructor guides you to do
certain things that may be easier to reference.

`/etc/microshift/config.yaml`

```yaml
dns:
  baseDomain: microshift-example.sandbox.opentlc.com

apiServer:
  subjectAltNames:
    - api.microshift-example.sandbox.opentlc.com
```

## Sample Application

Once your MicroShift cluster is running and you have verified that you can use
the CLI tools (`oc` or `kubectl`), it's time to deploy a sample application to
see it actually run something.

Run the following command to deploy the Hello MicroShift sample application:

```bash
oc apply -k https://github.com/jaredhocutt/edge-workshop/demo
```

To find the hostname of your Hello MicroShift application, run the following
command:

```bash
oc get route -n demo
NAME               HOST                                                                ADMITTED   SERVICE            TLS
hello-microshift   hello-microshift-demo.apps.microshift-example.sandbox.opentlc.com   True       hello-microshift
```

If you'd like to change your current context to default to the new namespace of
your sample application, run the following command:

```bash
oc config set-context --current --namespace=demo
```

### Learning resources
Get your own [Developer Subscription (redhat.com, Developer, bottom-of-the-page)](https://developers.redhat.com/articles/faqs-no-cost-red-hat-enterprise-linux#)

Online, interactive labs with [learn.openshift.com](http://learn.openshift.com) 

Podman/Buildah interactive labs in the [RHEL “Build” section](https://www.redhat.com/en/interactive-labs/enterprise-linux#build):
  - [Building container images with RHEL container tools](https://www.redhat.com/en/interactive-labs/build-container-images-red-hat-enterprise-linux-container-tools)

  - [Create images with container tools (Buildah)](https://www.redhat.com/en/interactive-labs/create-images-container-tools-buildah)

  - [Deploy containers using Podman container tools](https://www.redhat.com/en/interactive-labs/deploy-containers-podman-container-tools)

  - [Create and manage Podman pods](https://www.redhat.com/en/interactive-labs/create-and-manage-podman-pods)

Run Podman (and OpenShift Local) on your own laptop with [Podman Desktop](https://podman-desktop.io/)
