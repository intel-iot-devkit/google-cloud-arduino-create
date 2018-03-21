# Google Cloud MQTT Sample

## Introduction
This sample app demonstrates connecting to Google Cloud IoT Core and publishing a single message. See [Google's MQTT sample](https://github.com/GoogleCloudPlatform/cpp-docs-samples/tree/master/iot/mqtt-ciotc) for more information.

## Hardware requirements
No special H/W requirements, as long as your device could be connected to the internet.

## Software requirements
This version of the sample has been tested on Ubuntu Linux.

## Setup
Sign in to your Google Cloud account or open a new account if you don't already have one. You will need a personal email address, and a credit card (to verify identity).

Refer to [this document](https://cloud.google.com/iot/docs/quickstart) on how to create deviceid, registryid, and projectid parameters as they are used in calculating the client ID used for connecting to the MQTT bridge.

OR

you can follow below steps to create the parameters.

**_ProjectId_**
* Go to the GCP Console Manage resources page. GO TO THE [MANAGE RESOURCES PAGE](https://console.cloud.google.com/cloud-resource-manager?_ga=2.56084395.-1864518913.1512082942&_gac=1.184323540.1517607516.CjwKCAiAtdDTBRArEiwAPT4y-xhgKLslUBhukwamgrQLqDKHGQ_qqmec8J-ahLwHRgqTntSRIhKBZxoC5QUQAvD_BwE). On the drop-down at the top of the page, select the organization in which you want to create a project. Click Create Project. In the New Project window, enter a project name and select a billing account as applicable. After you're finished entering details, click Create.

**_RegistryId_**
* Go to the [Google Cloud IoT Core Page](https://console.cloud.google.com/iot/registries?project=intel-poc&organizationId=433637338589 ) in GCP Console. Click Device Registry, Enter my-registry for the Registry ID, Select us-central1 for the Cloud region, Select MQTT for the Protocol. In the Telemetry topic dropdown list, select Create a topic. In the Create a topic dialog, enter my-device-events in the Name fieldClick Create in the Create a topic dialog. The Device state topic and Certificate value fields are optional, so leave them blank. Click Create on the Cloud IoT Core page.

**_DeviceId_**
* On the Registry Details page, click Add device. Enter my-device for the Device ID. Select Allow for Device communication, The Authentication section and Device metadata field are optional; leave it blank. Click Add.

**_ecPrivate.pem**
* Open a terminal window and run the following multi-line command to create an RS256 key:
```
openssl req -x509 -newkey rsa:2048 -keyout rsa_private.pem -nodes \
    -out rsa_cert.pem -subj "/CN=unused"
```
Copy the contents of `rsa_cert.pem` to the clipboard. Make sure to include the lines that say-----BEGIN CERTIFICATE----- and-----END CERTIFICATE-----. On the Device details page for the device you created in the preceding section, click Add public key. Select `RS256_X509` for the Public key format. Paste your public key in the Public key value box. Click Add.

**_roots.pem_**
* Open a terminal window and run the following command
```
wget https://pki.google.com/roots.pem
```
Open Intel(R) System Studio. Start the 'New Project Creation Wizard' (File > New > Example project for building on a container and running on Linux). Choose Ubuntu, C, Cloud, and select 'Google cloud' sample.  It'll ask you for all the parameters, you have created in previous step. After entering details, continue to create a new project based on this sample.
