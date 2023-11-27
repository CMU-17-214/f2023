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

### Setting up a new virtual machine
Note: you may or may not have Google Cloud APIs enabled that you need for these
steps. If you do not, choose "Enable" when prompted.

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

### Connecting to your virtual machine
Similar to lab 8 and homework 5, you will be using the Google Cloud CLI `gcloud`
to run these commands. If you do not have it set up properly, please refer back
to the lab 8 instructions.

1. On your local machine, run `gcloud init` to make sure you are logged in to
   the Google Cloud service.

1. Log in to your virtual machine with `gcloud compute ssh
   --project=[YOUR_PROJECT_NAME] [YOUR_VM_NAME]`

1. We will be using Docker to deploy this lab. Install the latest version of
   Docker on the remote machine using [the instructions
   here](https://docs.docker.com/engine/install/debian/#install-using-the-repository).

### Build and deploy a Docker container
Back on your local machine, clone the [repository we provide you](). Build the
thing locally.

1. Run `gcloud compute scp [LOCAL_FILE] [YOUR_VM_NAME:A_DIRECTORY]` to copy the
   files to your virtual machine.

1. Log back in to the remote machine with SSH using the above command.


