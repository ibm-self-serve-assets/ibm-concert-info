## Vulnerability and Patch Magnagement


## 1. Import Application SBOM

1. Create application SBOM Json file as like [this](./files//TVS1-sbom.json).

2. 



## Vulnerability and Patch Magnagement

This procedure describes how to install **IBM Concert, Concert Workflows, and Concert Data Apps** using the Quick Start mode for quick deployment on a virtual machine (VM).

The detailed IBM Documentation for this topic is available [here](https://www.ibm.com/docs/en/concert/3.0.x?topic=vm-installing-using-quick-start-mode)

Note: This document focuses on Concert 3.0.x.

## 1. Prerequisites

#### 1.1 Hardware Requirements

To install **Concert, Concert Workflows, and Concert Data Apps** in Testing (POC) environment, you must use a Linux® x86_64-v3 architecture that meets the following specifications:

- CPU Cores : 16 cores
- RAM : 32 GB
- Disk space : 256 GB (minimum)

#### 1.2 Operating Systems

The following operating systems are supported:

- Red Hat® Enterprise Linux (RHEL) (version 9 or later)
- Ubuntu
- SUSE


#### 1.3 IBM entitlement API key

1.	Log in to the container software library on [My IBM](https://myibm.ibm.com/products-services/containerlibrary) using the IBMid and password associated with the IBM Concert subscription.
2. Navigate to the **Entitlement Keys** tab.
3. Click **Copy** to copy the entitlement key to your clipboard.

#### 1.4 Root User Access

Ensure that you either:
- Log in as the root user, or
- Have sudo privileges to execute all required commands

### 1.5 Network Access requirements

- Ensure outbound access to the  URL: https://github.com/IBM/Concert/releases

- After installation, the Concert UI will be accessible at: **https://<VM_FQDN>:443**
    Example: https://hostname.domain.com:443

- Ensure that port 443 (HTTPS) is open and accessible, if required.

## 2 Installation

1. Download the latest software package:

```bash
wget https://github.com/IBM/Concert/releases/download/v3.0.0/ibm-concert-x86.tar.gz
```

2. Extract the package:

```bash
tar xfz ibm-concert-x86.tar.gz
```

3. Set the IBM Container Registry password using your entitlement key:

```bash
export REG_PASS=<IBM entitlement key>
```

4. Run the installation script in quick-start mode:

```bash
./ibm-concert/bin/setup --quickstart-vm --license_acceptance=y
```

It may take 50 minutes to complete the installation. 

## 3 Verify installation:

During the installation, you may see output similar to the following:

1. You can view the summary of the installation logs below.

<details><summary>Click me for more info</summary>

```

.
.
.
Mon Jun 22 02:01:44 AM UTC 2026 INFO Running as root - installing VM prerequisites...
[2026-06-21 19:01:44] RUNID:1782093704 ==========================================================================
[2026-06-21 19:01:44] RUNID:1782093704     manage-prereqs-vm - IBM Concert Prerequisites Management Script
[2026-06-21 19:01:44] RUNID:1782093704 ==========================================================================
[2026-06-21 19:01:44] RUNID:1782093704 No --user specified, will configure root user for environment
.
.
.

Mon Jun 22 02:02:28 AM UTC 2026 INFO Sourcing environment variables from ~/.bashrc...
Mon Jun 22 02:02:28 AM UTC 2026 INFO Validating VM prerequisites...
[2026-06-21 19:02:28] RUNID:1782093748 ==========================================================================
[2026-06-21 19:02:28] RUNID:1782093748     manage-prereqs-vm - IBM Concert Prerequisites Management Script
[2026-06-21 19:02:28] RUNID:1782093748 ==========================================================================
[2026-06-21 19:02:28] RUNID:1782093748 Validate action: validating system prerequisites and configuration

.
.
.

[2026-06-21 19:02:32] RUNID:1782093748 All prerequisites validated successfully
Script execution log file: /root/ibm-concert/localstorage/logs/manage-prereqs-vm-1782093748.log
Mon Jun 22 02:02:32 AM UTC 2026 INFO
Mon Jun 22 02:02:32 AM UTC 2026 INFO ---------------------- Checking free disk space ----------------------
Mon Jun 22 02:02:32 AM UTC 2026 INFO
Mon Jun 22 02:02:32 AM UTC 2026 INFO [Kubernetes]     /var/lib/kubelet
Mon Jun 22 02:02:32 AM UTC 2026 INFO [Kubernetes PVC] /var/lib/rancher/k3s
Mon Jun 22 02:02:33 AM UTC 2026 INFO
Mon Jun 22 02:02:33 AM UTC 2026 INFO Disk space check PASS on filesystem '/dev/mapper/ubuntu--vg-ubuntu--lv' (mount: /).
Mon Jun 22 02:02:33 AM UTC 2026 INFO Storage targets: Hub, Concert, Concert PVC, Concert Workflows, Concert Workflows PVC, Data Apps, Data Apps PVC
Mon Jun 22 02:02:33 AM UTC 2026 INFO Available: 237 GiB.
Mon Jun 22 02:02:33 AM UTC 2026 INFO
Mon Jun 22 02:02:33 AM UTC 2026 INFO Disk space pre-check PASSED.
Mon Jun 22 02:02:33 AM UTC 2026 INFO
Mon Jun 22 02:02:33 AM UTC 2026 INFO ----------------------------------------------------------------------
Mon Jun 22 02:02:33 AM UTC 2026 INFO
platform-hub
.
.
.


Mon Jun 22 02:02:35 AM UTC 2026 INFO Config updated in /root/ibm-concert/bin/../concert-hub/localstorage/volumes/infra/solis-env/config-params.env
Mon Jun 22 02:02:35 AM UTC 2026 INFO Installing products

================================================================================
Mon Jun 22 02:02:35 AM UTC 2026 INFO STARTING INSTALLATION: Hub
================================================================================

[2026-06-22 02:02:35 UTC] [INFO] License acceptance: Accepted
[2026-06-22 02:02:35 UTC] [INFO] Deployment Configuration:

.
.
.

[2026-06-22 02:05:01 UTC] [SUCCESS] Deployment completed successfully

--------------------------------------------------------------------------------
Mon Jun 22 02:05:01 AM UTC 2026 INFO COMPLETED: Hub - SUCCESS (Duration: 146s)
--------------------------------------------------------------------------------

Mon Jun 22 02:05:01 AM UTC 2026 INFO Skipping ITOM installation (parameter 'ENABLE_CROSS_PRODUCT_INTEGRATION' set to: '')

================================================================================
Mon Jun 22 02:05:01 AM UTC 2026 INFO STARTING INSTALLATION: Concert
================================================================================

Mon Jun 22 02:05:01 AM UTC 2026 RUNID:1782093703 Namespace: concert


.
.
.

Mon Jun 22 02:13:45 AM UTC 2026 RUNID:1782093901  ROJA_k8s_cfg concert : completed.

--------------------------------------------------------------------------------
Mon Jun 22 02:13:45 AM UTC 2026 INFO COMPLETED: Concert - SUCCESS (Duration: 524s)
--------------------------------------------------------------------------------

Mon Jun 22 02:13:45 AM UTC 2026 INFO Setting up load balancer service for Concert...
service/ibm-concert-solis-gw-svc-lb created
[2026-06-22 02:13:45 UTC] [INFO] ==========================================
[2026-06-22 02:13:45 UTC] [INFO] Product Instance Management ()
[2026-06-22 02:13:45 UTC] [INFO] ==========================================
[2026-06-22 02:13:45 UTC] [INFO] Using default instance ID: 0000-0000-0000-0000

.
.
.

eployment.apps/ibm-solis-ui condition met
[2026-06-22 02:15:20 UTC] [SUCCESS] Hub deployment restarted successfully
[2026-06-22 02:15:20 UTC] [INFO] ==========================================
[2026-06-22 02:15:20 UTC] [SUCCESS] Product instance operation completed successfully
[2026-06-22 02:15:20 UTC] [INFO] ==========================================

.
.
.

Mon Jun 22 02:16:58 AM UTC 2026 INFO Concert attached to Hub on k3s

================================================================================
Mon Jun 22 02:16:58 AM UTC 2026 INFO STARTING INSTALLATION: Concert Data Apps
================================================================================

Mon Jun 22 02:16:58 AM UTC 2026 cfg_sw_ent_native: concert-dataapps
.
.
.


Mon Jun 22 02:19:06 AM UTC 2026  DATAAPPS_k8s_cfg concert-dataapps : completed.

--------------------------------------------------------------------------------
Mon Jun 22 02:19:06 AM UTC 2026 INFO COMPLETED: Concert Data Apps - SUCCESS (Duration: 128s)
--------------------------------------------------------------------------------

Mon Jun 22 02:19:06 AM UTC 2026 INFO Setting up load balancer service for Data Apps...
service/ibm-dataapps-solis-gw-svc-lb created
[2026-06-22 02:19:06 UTC] [INFO] ==========================================
[2026-06-22 02:19:06 UTC] [INFO] Product Instance Management ()
[2026-06-22 02:19:06 UTC] [INFO] ==========================================
[2026-06-22 02:19:06 UTC] [INFO] Using default instance ID: 0000-0000-0000-0000

.
.
.


[2026-06-22 02:20:42 UTC] [SUCCESS] Hub deployment restarted successfully
[2026-06-22 02:20:42 UTC] [INFO] ==========================================
[2026-06-22 02:20:42 UTC] [SUCCESS] Product instance operation completed successfully
[2026-06-22 02:20:42 UTC] [INFO] ==========================================


deployment "dataapps-solis-gw" successfully rolled out
Mon Jun 22 02:22:18 AM UTC 2026 INFO Data Apps attached to Hub on k3s

================================================================================
Mon Jun 22 02:22:19 AM UTC 2026 INFO STARTING INSTALLATION: Concert Workflows
================================================================================

2026-06-21 19:22:19 RUNID:1782094939 HUB_ACCESS_KEY environment variable detected. It will be used to configure the deployment

╔══════════════════════════════════════════════════════════════════════════════════╗
║                     IBM Concert Workflows 3.0.0 INSTALLER CONFIG
╠══════════════════════════════════════════════════════════════════════════════════╣
║  Namespace:          concert-workflows
║  Instance address:   gan-concert11.fyre.ibm.com
║  Preview:            false
║  Image Registry:     cp.icr.io/cp/concert
║  Pull Secret:        ibm-entitlement-key
║  Installation Type:  on-prem
║  Log File:           /root/ibm-concert/ibm-concert-std-workflows/bin/install-1782094939.log
║  FaaS Enabled:       Yes
║  Istio Enabled:      No
╚══════════════════════════════════════════════════════════════════════════════════╝

2026-06-21 19:22:19 RUNID:1782094939 Starting IBM Concert Workflows 3.0.0 installation
.
.
.



2026-06-21 19:22:19 RUNID:1782094939 cw-secrets not found in namespace concert-workflows - using internal databases

╔══════════════════════════════════════════════════════════════════════════════════╗
║                     IBM Concert Workflows 3.0.0 ENVIRONMENT DETAILS
╠══════════════════════════════════════════════════════════════════════════════════╣
║  Architecture:      x86_64
║  OpenShift Cluster: No
║  Storage Class:     default
║  MySQL:             Internal
║  PostgreSQL:        Internal
║  Objectstore:       Internal
║  RabbitMQ:          Internal
╚══════════════════════════════════════════════════════════════════════════════════╝

2026-06-21 19:22:19 RUNID:1782094939 Testing kubectl connection to cluster...
NAME      STATUS   AGE
.
.
.


2026-06-21 19:50:02 RUNID:1782094939 ConfigMap successfully patched
2026-06-21 19:50:02 RUNID:1782094939 IBM Concert Workflows 3.0.0 installation finished successfully
2026-06-21 19:50:02 RUNID:1782094939 --------------------------------------------------------------------------------------------------------------------------
2026-06-21 19:50:02 RUNID:1782094939      Congratulations! You have successfully installed IBM Concert Workflows 3.0.0
2026-06-21 19:50:02 RUNID:1782094939      You can take full advantage of the IBM Concert Workflows 3.0.0 functionality.
2026-06-21 19:50:02 RUNID:1782094939 --------------------------------------------------------------------------------------------------------------------------
Script execution log file: /root/ibm-concert/ibm-concert-std-workflows/bin/install-1782094939.log

--------------------------------------------------------------------------------
Mon Jun 22 02:50:02 AM UTC 2026 INFO COMPLETED: Concert Workflows - SUCCESS (Duration: 1663s)
--------------------------------------------------------------------------------

[2026-06-22 02:50:02 UTC] [INFO] ==========================================
[2026-06-22 02:50:02 UTC] [INFO] Product Instance Management ()
[2026-06-22 02:50:02 UTC] [INFO] ==========================================
[2026-06-22 02:50:02 UTC] [INFO] Using default instance ID: 0000-0000-0000-0000
.
.
.


[2026-06-22 02:51:39 UTC] [SUCCESS] Hub deployment restarted successfully
[2026-06-22 02:51:39 UTC] [INFO] ==========================================
[2026-06-22 02:51:39 UTC] [SUCCESS] Product instance operation completed successfully
[2026-06-22 02:51:39 UTC] [INFO] ==========================================
Mon Jun 22 02:51:39 AM UTC 2026 INFO Skipping Secure Coder installation (parameter 'INSTALL_SECURECODER' set to: 'FALSE')

================================================================================
Mon Jun 22 02:51:39 AM UTC 2026 INFO INSTALLATION SUMMARY
================================================================================
Mon Jun 22 02:51:39 AM UTC 2026 INFO Products successfully installed: 4
Mon Jun 22 02:51:39 AM UTC 2026 INFO
Mon Jun 22 02:51:39 AM UTC 2026 INFO   You can access IBM Concert at: https://gan-concert11.fyre.ibm.com:12443
Mon Jun 22 02:51:39 AM UTC 2026 INFO
Mon Jun 22 02:51:39 AM UTC 2026 INFO   Admin username:   ibmconcert
Mon Jun 22 02:51:39 AM UTC 2026 INFO   Initial password: xxxxxxxx
Mon Jun 22 02:51:39 AM UTC 2026 INFO
Mon Jun 22 02:51:39 AM UTC 2026 INFO Note: In cloud environments (e.g., with LoadBalancers), the external IP address
Mon Jun 22 02:51:39 AM UTC 2026 INFO       or hostname may differ from the locally determined address shown above
Mon Jun 22 02:51:39 AM UTC 2026 INFO
================================================================================


================================================================================
Mon Jun 22 02:51:39 AM UTC 2026 INFO DEPLOYMENT SUCCESSFUL
================================================================================

Mon Jun 22 02:51:39 AM UTC 2026 INFO
Mon Jun 22 02:51:39 AM UTC 2026 INFO ==========================================================================
Mon Jun 22 02:51:39 AM UTC 2026 INFO   IMPORTANT: To use kubectl/helm, user 'root' should run:
Mon Jun 22 02:51:39 AM UTC 2026 INFO       source ~/.bashrc
Mon Jun 22 02:51:39 AM UTC 2026 INFO   or start a new shell session (logout and login, or open a new terminal)
Mon Jun 22 02:51:39 AM UTC 2026 INFO ==========================================================================
Mon Jun 22 02:51:39 AM UTC 2026 INFO
.
.
.
```

</details>

2. The complete installation log is available [here](./files/install.log).


## 4 Access the Concert

1. After installation, the console output will display the access details, including the URL, username, and password:

```
================================================================================
Mon Jun 22 02:51:39 AM UTC 2026 INFO INSTALLATION SUMMARY
================================================================================
Mon Jun 22 02:51:39 AM UTC 2026 INFO Products successfully installed: 4
Mon Jun 22 02:51:39 AM UTC 2026 INFO
Mon Jun 22 02:51:39 AM UTC 2026 INFO   You can access IBM Concert at: https://gan-concert11.fyre.ibm.com:12443
Mon Jun 22 02:51:39 AM UTC 2026 INFO
Mon Jun 22 02:51:39 AM UTC 2026 INFO   Admin username:   ibmconcert
Mon Jun 22 02:51:39 AM UTC 2026 INFO   Initial password: xxxxxxxx
```
2. Use the above credentials to log in to the IBM Concert UI via your browser.

Once logged in, you will see the Concert home page:

<img src="images/img1.png" >
