# Edge Workshop

The instructions for this workshop assume that you have used the automation provided in this
repository to deploy the infrastructure and configure it accordingly.

## Accessing The Environment

The easiest way to access the environment is using the Cockpit interface that has been deployed on
your machine. The Cockpit interface contains a browser-based terminal interface and other UI
elements to make connecting to the machine and running commands easier to do.

You can find the Cockpit interface at `https://${HOSTNAME}:9090`.

For example, if your hostname is `microshift-example.sandbox.opentlc.com` then you would access the
Cockpit interface by going to `https://microshift-example.sandbox.opentlc.com:9090`

Your lab instructor will provide you with the username and password.

If you prefer to SSH directly into the machine, you can also access the machine using the same
hostname on port 22. The username and password provided by your lab instructor will be the same for
SSH and password authentication is enabled.

## Getting Started

At this point in time, this workshop and the steps you need to do is expected to be driven verbally
by your lab instructor. However, many of these verbal instructions will point you to parts of the
documentation as well as instructions or examples contained in this repository. Check out the links
below for easy access to the documentation pages when your lab instructor guides you to do so.

- [MicroShift 4.13 Documentation](https://access.redhat.com/documentation/en-us/red_hat_build_of_microshift/4.13)
- [MicroShift 4.13 Installation](https://access.redhat.com/documentation/en-us/red_hat_build_of_microshift/4.13/html-single/installing)
- [MicroShift 4.13 Configuration](https://access.redhat.com/documentation/en-us/red_hat_build_of_microshift/4.13/html-single/configuring)

## Helpful Examples

Here are some helpful examples for when your lab instructor guides you to do certain things that may
be easier to reference.

`/etc/microshift/config.yaml`

```yaml
dns:
  baseDomain: microshift-example.sandbox.opentlc.com

apiServer:
  subjectAltNames:
    - api.microshift-example.sandbox.opentlc.com
```

## Sample Application

Once your MicroShift cluster is running and you have verified that you can use the CLI tools (`oc`
or `kubectl`), it's time to deploy a sample application to see it actually run something.

Run the following command to deploy the Hello MicroShift sample application:

```bash
oc apply -k https://github.com/jaredhocutt/edge-workshop/demo
```

If you'd like to change your current context to default to the new namespace of your sample
application, run the following command:

```bash
oc config set-context --current --namespace=demo
```
