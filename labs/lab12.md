# Lab 12 - Cloud Deployment

Repo link: FIXME

In this recitation, you will deploy a version of the TicTacToe game to the
Google Cloud Compute Engine service, allowing you to access it remotely.

## Deliverables
- [ ] Enable the Google Cloud Compute Engine service, and create a virtual machine.
- [ ] Demonstrate to the TA that you were able to successfully run an instance
      of TicTacToe on the cloud.
- [ ] Make a change to the code and update the image on the cloud.

## Introduction
One of the services provided by Google (and Amazon, Microsoft, etc.) is the
ability to use servers that they have as _virtual machines_. This allows you to
skip a lot of the work needed to assemble your own server, connect it to the
internet, and maintain hardware that might fail.

FIXME MORE HERE

## Instructions
1. On the [Google Cloud Console](https://console.cloud.google.com), click the
   "Create a VM" button.
![createvm](images/lab12/create-a-vm.png)

1. Give your VM a name.

1. It is ok to use the default E2 machines, but under the "Machine type"
   dropdown select `e2-small`
![selectvm](images/lab12/select-vm.png)

1. Under "Firewall", select the boxes for "Allow HTTP traffic" and "Allow HTTPS
   traffic".
![selecttraffic](images/lab12/select-traffic.png)

1. Click "Create".

1. You will be brought to a screen with a list of VM instances, and should see
your newly created VM, together with an "External IP" that you can use to
connect to it (in this case it's 34.69.81.171).
![details](images/lab12/details.png)
