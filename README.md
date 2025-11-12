# GitOps Tetris Project - Complete Setup Guide# GitOps Tetris Project - Complete Setup Guide# GitOps Tetris Project



A comprehensive guide to deploying the classic Tetris game on AWS EKS using GitOps principles with ArgoCD. This project demonstrates containerization, Kubernetes orchestration, and continuous deployment workflows.



## Table of ContentsA comprehensive guide to deploying the classic Tetris game on AWS EKS using GitOps principles with ArgoCD. This project demonstrates containerization, Kubernetes orchestration, and continuous deployment workflows.A Kubernetes-based deployment of the classic Tetris game using GitOps principles. This project demonstrates container orchestration and service management with Kubernetes manifests.



1. [Project Overview](#project-overview)

2. [Architecture](#architecture)

3. [Prerequisites](#prerequisites)## Table of Contents## Project Overview

4. [Step-by-Step Setup Guide](#step-by-step-setup-guide)

   - [Step 1: Create EKS Cluster](#step-1-create-eks-cluster)

   - [Step 2: Create Node Group](#step-2-create-node-group)

   - [Step 3: Configure kubectl](#step-3-configure-kubectl)1. [Project Overview](#project-overview)This repository contains Kubernetes manifests for deploying a Tetris game application in a Kubernetes cluster. It showcases GitOps best practices with declarative configuration management.

   - [Step 4: Install ArgoCD](#step-4-install-argocd)

   - [Step 5: Access ArgoCD Dashboard](#step-5-access-argocd-dashboard)2. [Architecture](#architecture)

   - [Step 6: Connect GitHub Repository](#step-6-connect-github-repository)

   - [Step 7: Create ArgoCD Application](#step-7-create-argocd-application)3. [Prerequisites](#prerequisites)## Architecture

   - [Step 8: Verify Deployment](#step-8-verify-deployment)

5. [ArgoCD Dashboard Guide](#argocd-dashboard-guide)4. [Step-by-Step Setup Guide](#step-by-step-setup-guide)

6. [Project Structure](#project-structure)

7. [Troubleshooting](#troubleshooting)   - [Step 1: Create EKS Cluster](#step-1-create-eks-cluster)### Architecture Diagram

8. [References](#references)

   - [Step 2: Create Node Group](#step-2-create-node-group)

---

   - [Step 3: Configure kubectl](#step-3-configure-kubectl)![GitOps Architecture Diagram](Screenshots/ArgoCDP1.drawio.png)

## Project Overview

   - [Step 4: Install ArgoCD](#step-4-install-argocd)

This project demonstrates GitOps best practices by:

- Creating an AWS EKS (Elastic Kubernetes Service) cluster   - [Step 5: Access ArgoCD Dashboard](#step-5-access-argocd-dashboard)### Architecture Flow

- Setting up ArgoCD as a GitOps operator

- Automating Tetris application deployment   - [Step 6: Connect GitHub Repository](#step-6-connect-github-repository)

- Maintaining Git as the single source of truth

- Enabling continuous deployment through Git commits   - [Step 7: Create ArgoCD Application](#step-7-create-argocd-application)The GitOps Tetris project follows a complete automated deployment workflow:



---   - [Step 8: Verify Deployment](#step-8-verify-deployment)



## Architecture5. [ArgoCD Dashboard Guide](#argocd-dashboard-guide)1. **Git Repository** - Configuration is stored in Git as the single source of truth



### Architecture Diagram6. [Project Structure](#project-structure)2. **ArgoCD Monitoring** - ArgoCD continuously monitors the Git repository for changes



![GitOps Architecture Diagram](Screenshots/ArgoCDP1.drawio.png)7. [Troubleshooting](#troubleshooting)3. **Change Detection** - When manifests are updated in Git, ArgoCD detects the differences



### Architecture Flow8. [References](#references)4. **Kubernetes Deployment** - ArgoCD automatically syncs the desired state to the Kubernetes cluster



The GitOps Tetris project follows this automated workflow:5. **Pod Management** - Kubernetes creates and manages Tetris game pods based on deployment specifications



1. **Git Repository** - Configuration stored in Git as the single source of truth---6. **Service Exposure** - The LoadBalancer service exposes the Tetris game to external users

2. **ArgoCD Monitoring** - ArgoCD continuously monitors the Git repository for changes

3. **Change Detection** - When manifests are updated in Git, ArgoCD detects the differences7. **User Access** - Users access the game through the external IP provided by the LoadBalancer

4. **Kubernetes Deployment** - ArgoCD automatically syncs the desired state to the Kubernetes cluster

5. **Pod Management** - Kubernetes creates and manages Tetris game pods based on deployment specifications## Project Overview

6. **Service Exposure** - The LoadBalancer service exposes the Tetris game to external users

7. **User Access** - Users access the game through the external IP provided by the LoadBalancer### Components



---This project demonstrates GitOps best practices by:



## Prerequisites- Creating an AWS EKS (Elastic Kubernetes Service) cluster- **Tetris Deployment** (`tetris-deploy.yaml`)



- AWS Account with appropriate permissions- Setting up ArgoCD as a GitOps operator  - Deploys 2 replicas of the Tetris application

- AWS CLI installed and configured

- `kubectl` (Kubernetes command-line tool)- Automating Tetris application deployment  - Uses the `nasi101/tetrisv2` Docker image

- `eksctl` (EKS cluster management tool) or AWS Console access

- Git installed- Maintaining Git as the single source of truth  - Exposes port 80 for HTTP traffic

- GitHub account with a repository

- Enabling continuous deployment through Git commits

---

- **Tetris Service** (`tetris-svc.yaml`)

## Step-by-Step Setup Guide

---  - LoadBalancer service for external access

### Step 1: Create EKS Cluster

  - Routes traffic to Tetris pods on port 80

#### 1.1 Using AWS Console

## Architecture  - Enables load balancing across replicas

Navigate to EKS in AWS Console and create a new cluster with the following specifications:



**Cluster Configuration:**

- **Cluster Name**: tetris-cluster (or your preferred name)### Architecture Diagram- **ArgoCD**

- **Kubernetes Version**: 1.27+ (recommended)

- **Cluster Service Role**: Create or select an IAM role with EKS service permissions  - GitOps operator for continuous deployment



**Cluster IAM Role Requirements:**![GitOps Architecture Diagram](Screenshots/ArgoCDP1.drawio.png)  - Monitors Git repository for configuration changes

The role should have the following policies:

- `AmazonEKSClusterPolicy`  - Automatically syncs desired state to Kubernetes cluster

- `AmazonEKSVPCResourceController`

### Architecture Flow  - Provides centralized UI for deployment management

![EKS Cluster Creation](Screenshots/EKSCreation.png)



![EKS Cluster Configuration](Screenshots/EKSCreation1.png)

The GitOps Tetris project follows this automated workflow:## File Structure

#### 1.2 Networking Configuration



Configure VPC and subnet settings:

1. **Git Repository** - Configuration stored in Git as the single source of truth```

![EKS Networking Configuration](Screenshots/EKSCREATION2.png)

2. **ArgoCD Monitoring** - ArgoCD continuously monitors the Git repository for changesGitOps_p1/

#### 1.3 IAM Role Setup

3. **Change Detection** - When manifests are updated in Git, ArgoCD detects the differences├── README.md                 # This file

Set up the cluster IAM role with required permissions:

4. **Kubernetes Deployment** - ArgoCD automatically syncs the desired state to the Kubernetes cluster├── manifest/

![Cluster IAM Role 1](Screenshots/EKSCreation2_ClusterRole1.png)

5. **Pod Management** - Kubernetes creates and manages Tetris game pods based on deployment specifications│   ├── tetris-deploy.yaml    # Deployment configuration

![Cluster IAM Role 2](Screenshots/EKSCreation2_ClusterRole2.png)

6. **Service Exposure** - The LoadBalancer service exposes the Tetris game to external users│   ├── tetris-svc.yaml       # Service configuration

![Cluster IAM Role 3](Screenshots/EKSCreation2_ClusterRole3.png)

7. **User Access** - Users access the game through the external IP provided by the LoadBalancer└── Screenshots/              # Project documentation images

![Cluster IAM Role 4](Screenshots/EKSCreation2_ClusterRole4.png)

```

#### 1.4 Review and Create

---

Review your cluster configuration before creation:

## Prerequisites

![Review EKS Creation](Screenshots/ReviewEKSCreate.png)

## Prerequisites

#### 1.5 Final Creation Status

- Kubernetes cluster (v1.19+)

Wait for the cluster to be created (this typically takes 10-15 minutes):

- AWS Account with appropriate permissions- `kubectl` configured to access your cluster

![EKS Creation Complete](Screenshots/EKSCreation3.png)

- AWS CLI installed and configured- Docker (for building custom images, if needed)

---

- `kubectl` (Kubernetes command-line tool)

### Step 2: Create Node Group

- `eksctl` (EKS cluster management tool) or AWS Console access## Deployment

#### 2.1 Add Node Group to Cluster

- Git installed

After the cluster is created, add a node group to host your workloads.

- GitHub account with a repository### Quick Start

**Node Group Configuration:**

- **Node Group Name**: tetris-node-group

- **Node IAM Role**: Create a new role or select existing

---Deploy the Tetris application to your Kubernetes cluster:

![Add Node Group](Screenshots/AddingNodeGroup1.png)



#### 2.2 Node IAM Role Setup

## Step-by-Step Setup Guide```bash

The node role requires the following policies:

- `AmazonEKSWorkerNodePolicy`# Apply all manifests

- `AmazonEKS_CNI_Policy`

- `AmazonEC2ContainerRegistryReadOnly`### Step 1: Create EKS Clusterkubectl apply -f manifest/



![IAM Role for Node Group 1](Screenshots/IAMRoleForNodeGroup.png)



![IAM Role for Node Group 2](Screenshots/IAMRoleForNodeGroup1.png)#### 1.1 Using AWS Console# Verify deployment



![Node Role Policies 1](Screenshots/NodeGroupRole1.png)kubectl get deployments



![Node Role Policies 2](Screenshots/NodeGroupRole2.png)Navigate to EKS in AWS Console and create a new cluster with the following specifications:kubectl get services



![Node Role Trust Policy](Screenshots/NodeGroupRoleTrustPolicy.png)kubectl get pods



![Node Role Success](Screenshots/NodeGroupRoleSuccess.png)**Cluster Configuration:**```



#### 2.3 Node Group Configuration- **Cluster Name**: tetris-cluster (or your preferred name)



Configure instance settings:- **Kubernetes Version**: 1.27+ (recommended)### Access the Application

- **Instance Type**: t3.medium or t3.small

- **Desired Size**: 1 node (for this tutorial)- **Cluster Service Role**: Create or select an IAM role with EKS service permissions

- **Min Size**: 1

- **Max Size**: 3Once deployed, the Tetris game is accessible via the LoadBalancer service:



**[INSERT SCREENSHOT: Node Group Instance Configuration]****Cluster IAM Role Requirements:**



#### 2.4 Node Group Creation CompleteThe role should have the following policies:```bash



Your cluster now has an active node:- `AmazonEKSClusterPolicy`# Get the external IP



**[INSERT SCREENSHOT: Node Group Active Status]**- `AmazonEKSVPCResourceController`kubectl get svc tetris-service -w



---



### Step 3: Configure kubectl![EKS Cluster Creation](Screenshots/EKSCreation.png)# Access the game at: http://<EXTERNAL-IP>



#### 3.1 Update kubeconfig```



After the cluster and node group are ready, configure kubectl to communicate with your cluster:![EKS Cluster Configuration](Screenshots/EKSCreation1.png)



```bash### Scaling

# Configure AWS credentials

aws configure#### 1.2 Networking Configuration



# Update kubeconfig to connect to your EKS clusterAdjust the number of replicas in `tetris-deploy.yaml`:

aws eks update-kubeconfig --region us-east-1 --name tetris-cluster

```Configure VPC and subnet settings:



#### 3.2 Verify Cluster Connection```yaml



Verify that kubectl is properly configured:![EKS Networking Configuration](Screenshots/EKSCREATION2.png)spec:



```bash  replicas: 3  # Change this value

# Check cluster info

kubectl cluster-info#### 1.3 IAM Role Setup```



# Get cluster nodes

kubectl get nodes

Set up the cluster IAM role with required permissions:Then reapply:

# List all namespaces

kubectl get namespaces

```

![Cluster IAM Role 1](Screenshots/EKSCreation2_ClusterRole1.png)```bash

![kubectl Commands](Screenshots/Kubecltcommands1.png)

kubectl apply -f manifest/tetris-deploy.yaml

#### 3.3 Verify Node Status

![Cluster IAM Role 2](Screenshots/EKSCreation2_ClusterRole2.png)```

Ensure your node is in a `Ready` state:



```bash

kubectl get nodes -w![Cluster IAM Role 3](Screenshots/EKSCreation2_ClusterRole3.png)## Configuration

```



---

![Cluster IAM Role 4](Screenshots/EKSCreation2_ClusterRole4.png)### Deployment Configuration (`tetris-deploy.yaml`)

### Step 4: Install ArgoCD



#### 4.1 Create ArgoCD Namespace

#### 1.4 Review and Create- **Replicas**: 2 (configurable)

Create a dedicated namespace for ArgoCD:

- **Image**: `nasi101/tetrisv2`

```bash

# Create the argocd namespaceReview your cluster configuration before creation:- **Port**: 80

kubectl create namespace argocd

- **Selector**: `app: tetris`

# Verify namespace creation

kubectl get namespace argocd![Review EKS Creation](Screenshots/ReviewEKSCreate.png)

```

### Service Configuration (`tetris-svc.yaml`)

#### 4.2 Install ArgoCD using Helm (Recommended)

#### 1.5 Final Creation Status

The easiest way to install ArgoCD is using Helm:

- **Type**: LoadBalancer

```bash

# Add ArgoCD Helm repositoryWait for the cluster to be created (this typically takes 10-15 minutes):- **Port**: 80

helm repo add argocd https://argoproj.github.io/argo-helm

helm repo update- **Target Port**: 80



# Install ArgoCD in the argocd namespace![EKS Creation Complete](Screenshots/EKSCreation3.png)- **Selector**: `app: tetris`

helm install argocd argocd/argo-cd --namespace argocd

```



#### 4.3 Alternative: Install ArgoCD using kubectl---## Customization



If you prefer using kubectl manifests:



```bash### Step 2: Create Node Group### Change Image Version

# Install ArgoCD

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml



# Verify ArgoCD deployment#### 2.1 Add Node Group to ClusterEdit `manifest/tetris-deploy.yaml`:

kubectl get deployments -n argocd

kubectl get pods -n argocd

```

After the cluster is created, add a node group to host your workloads.```yaml

#### 4.4 Verify ArgoCD Installation

containers:

Check if all ArgoCD components are running:

**Node Group Configuration:**  - name: tetris

```bash

# List all ArgoCD pods- **Node Group Name**: tetris-node-group    image: nasi101/tetrisv2:latest  # Update tag as needed

kubectl get pods -n argocd

- **Node IAM Role**: Create a new role or select existing```

# Check ArgoCD services

kubectl get svc -n argocd



# Expected output should show:![Add Node Group](Screenshots/AddingNodeGroup1.png)### Modify Service Type

# - argocd-server

# - argocd-repo-server

# - argocd-controller-manager

```#### 2.2 Node IAM Role SetupEdit `manifest/tetris-svc.yaml` to use NodePort or ClusterIP instead of LoadBalancer:



**[INSERT SCREENSHOT: ArgoCD Pods Running]**



---The node role requires the following policies:```yaml



### Step 5: Access ArgoCD Dashboard- `AmazonEKSWorkerNodePolicy`type: NodePort  # or ClusterIP



#### 5.1 Port Forward to ArgoCD Server- `AmazonEKS_CNI_Policy````



Access the ArgoCD dashboard using port forwarding:- `AmazonEC2ContainerRegistryReadOnly`



```bash## Troubleshooting

# Forward local port 8080 to ArgoCD server

kubectl port-forward svc/argocd-server -n argocd 8080:443![IAM Role for Node Group 1](Screenshots/IAMRoleForNodeGroup.png)

```

### Check Deployment Status

#### 5.2 Get Initial Admin Password

![IAM Role for Node Group 2](Screenshots/IAMRoleForNodeGroup1.png)

Retrieve the default admin password:

```bash

```bash

# Get the initial admin password![Node Role Policies 1](Screenshots/NodeGroupRole1.png)kubectl describe deployment tetris-deployment

kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d

kubectl describe pod <pod-name>

# On Windows PowerShell:

kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d; echo![Node Role Policies 2](Screenshots/NodeGroupRole2.png)```

```



#### 5.3 Login to ArgoCD

![Node Role Trust Policy](Screenshots/NodeGroupRoleTrustPolicy.png)### View Logs

Open your browser and navigate to: `https://localhost:8080`



- **Username**: admin

- **Password**: [Use the password from Step 5.2]![Node Role Success](Screenshots/NodeGroupRoleSuccess.png)```bash



![ArgoCD Login](Screenshots/ArgoCdLogin.png)kubectl logs -f deployment/tetris-deployment



![Successful ArgoCD Login](Screenshots/successful_login_argocd.png)#### 2.3 Node Group Configuration```



#### 5.4 Change Default Password



Once logged in, change the admin password:Configure instance settings:### Verify Service



1. Click on **Settings** (gear icon)- **Instance Type**: t3.medium or t3.small

2. Navigate to **Accounts**

3. Click **Update Password**- **Desired Size**: 1 node (for this tutorial)```bash

4. Enter your new secure password

- **Min Size**: 1kubectl describe svc tetris-service

---

- **Max Size**: 3```

### Step 6: Connect GitHub Repository



#### 6.1 Create GitHub Repository Connection

**[INSERT SCREENSHOT: Node Group Instance Configuration]**## Cleanup

Connect your GitHub repository to ArgoCD:



1. Go to **Settings** → **Repositories** in ArgoCD dashboard

2. Click **Connect Repo**#### 2.4 Node Group Creation CompleteRemove all resources:

3. Select **VIA HTTPS** or **VIA SSH** (HTTPS recommended for simplicity)



**[INSERT SCREENSHOT: Connect Repository Screen]**

Your cluster now has an active node:```bash

#### 6.2 Enter Repository Details

kubectl delete -f manifest/

Provide your repository information:

**[INSERT SCREENSHOT: Node Group Active Status]**```

```

Repository URL: https://github.com/samuel-nartey/GitOpsTetrisProject

```

---## Deployment Success

![Connecting GitHub Repo 1](Screenshots/connecdtingithubrepo.png)



![Connecting GitHub Repo 2](Screenshots/connecdtingithubrepo2.png)

### Step 3: Configure kubectl### Tetris Game Deployment

![Connecting GitHub Repo 3](Screenshots/connecdtingithubrepo3.png)



#### 6.3 Verify Repository Connection

#### 3.1 Update kubeconfigThe following screenshots show the successful deployment of the Tetris game on Kubernetes:

Once connected, you should see your repository in the repositories list:



**[INSERT SCREENSHOT: Repository Connected Successfully]**

After the cluster and node group are ready, configure kubectl to communicate with your cluster:![Tetris Deployment Success 1](Screenshots/tetrisgamedeployedsuccess.png)

---



### Step 7: Create ArgoCD Application

```bash![Tetris Deployment Success 2](Screenshots/tetrisgamedeployedsuccess2.png)

#### 7.1 Create New Application

# Configure AWS credentials

Create an ArgoCD Application to deploy the Tetris game:

aws configure![Tetris Deployment Success 3](Screenshots/tetrisgamedeployedsuccess3.png)

1. Click **+ NEW APP** on the ArgoCD dashboard

2. Fill in the application details



**Application Configuration:**# Update kubeconfig to connect to your EKS cluster![Tetris Deployment Success 4](Screenshots/tetrisgamedeployedsuccess4.png)



```aws eks update-kubeconfig --region us-east-1 --name tetris-cluster

Application Name: tetris-app

Project Name: default```### ArgoCD Interface

Sync Policy: Automatic



Source:

  Repository URL: https://github.com/samuel-nartey/GitOpsTetrisProject#### 3.2 Verify Cluster ConnectionArgoCD monitoring and syncing the Tetris application:

  Revision: main

  Path: manifest



Destination:Verify that kubectl is properly configured:![ArgoCD Interface](Screenshots/argocdinterface.png)

  Cluster: https://kubernetes.default.svc (in-cluster)

  Namespace: default

```

```bash![ArgoCD Tetris Synching](Screenshots/argocdtetrissynching.png)

![Create App in ArgoCD 1](Screenshots/createappinargocd.png)

# Check cluster info

#### 7.2 Configure Sync Settings

kubectl cluster-info![ArgoCD Tetris Synching Detail](Screenshots/argocdtetrissynching1.png)

Set up automatic synchronization:



```yaml

Sync Policy: Automatic# Get cluster nodes![ArgoCD Tetris Version](Screenshots/argocdtetrisversion2.png)

Auto-Prune: Enabled

Self-Heal: Enabledkubectl get nodes

```

![ArgoCD Tetris Version Game](Screenshots/argocdtetrisversiongame.png)

This ensures ArgoCD automatically:

- Syncs changes from Git to the cluster# List all namespaces

- Removes resources deleted from Git

- Reconciles drift between Git and clusterkubectl get namespaces![ArgoCD Tetris Version Interface](Screenshots/argocdtetrisversioninterface.png)



**[INSERT SCREENSHOT: Sync Policy Configuration]**```



#### 7.3 Create the Application## GitOps Best Practices



Click **CREATE** to deploy the application:![kubectl Commands](Screenshots/Kubecltcommands1.png)



**[INSERT SCREENSHOT: Application Creation Complete]**This project follows GitOps principles:



---#### 3.3 Verify Node Status- **Declarative Configuration**: All infrastructure defined in YAML manifests



### Step 8: Verify Deployment- **Version Control**: Configuration tracked in Git



#### 8.1 Monitor Application SyncEnsure your node is in a `Ready` state:- **Single Source of Truth**: Manifests are the authoritative state



Watch the ArgoCD dashboard as it syncs your application:- **Automated Deployment**: Apply changes via GitOps operators (ArgoCD, Flux, etc.)



![ArgoCD Tetris Synching](Screenshots/argocdtetrissynching.png)```bash



![ArgoCD Tetris Synching Detail](Screenshots/argocdtetrissynching1.png)kubectl get nodes -w## Future Enhancements



#### 8.2 Verify Kubernetes Deployment```



Check the deployment status in your cluster:- Add Ingress configuration for custom domain support



```bash---- Implement HorizontalPodAutoscaler for dynamic scaling

# List deployments

kubectl get deployments- Add persistent storage for game state



# List services### Step 4: Install ArgoCD- Configure resource requests and limits

kubectl get services

- Add health checks (liveness and readiness probes)

# List pods

kubectl get pods#### 4.1 Create ArgoCD Namespace- Implement network policies for security



# Describe tetris service

kubectl describe svc tetris-service

Create a dedicated namespace for ArgoCD:## License

# Get service external IP

kubectl get svc tetris-service -o jsonpath='{.status.loadBalancer.ingress[0].hostname}'

```

```bashThis project is part of the 12-week challenge personal project series.

#### 8.3 Application Deployment Success

# Create the argocd namespace

Your application is now deployed and running:

kubectl create namespace argocd## Author

![Tetris Deployment Success 1](Screenshots/tetrisgamedeployedsuccess.png)



![Tetris Deployment Success 2](Screenshots/tetrisgamedeployedsuccess2.png)

# Verify namespace creationsamuel-nartey

![Tetris Deployment Success 3](Screenshots/tetrisgamedeployedsuccess3.png)

kubectl get namespace argocd

![Tetris Deployment Success 4](Screenshots/tetrisgamedeployedsuccess4.png)

```## References

#### 8.4 Access the Tetris Game



Get the external IP/hostname and access the Tetris game:

#### 4.2 Install ArgoCD using Helm (Recommended)- [Kubernetes Documentation](https://kubernetes.io/docs/)

```bash

# Get LoadBalancer external IP- [GitOps Best Practices](https://www.gitops.tech/)

kubectl get svc tetris-service

The easiest way to install ArgoCD is using Helm:- [Tetris Game](https://en.wikipedia.org/wiki/Tetris)

# Access at: http://<EXTERNAL-IP>

```



---```bash---



## ArgoCD Dashboard Guide# Add ArgoCD Helm repository



### Dashboard Overviewhelm repo add argocd https://argoproj.github.io/argo-helm**Last Updated**: November 11, 2025



The ArgoCD dashboard displays all your applications and their deployment status:helm repo update



![ArgoCD Interface](Screenshots/argocdinterface.png)# Install ArgoCD in the argocd namespace

helm install argocd argocd/argo-cd --namespace argocd

### Application Card Details```



Each application card shows:#### 4.3 Alternative: Install ArgoCD using kubectl



- **Application Name**: tetris-appIf you prefer using kubectl manifests:

- **Sync Status**: 

  - 🟢 **Synced**: Git and cluster state match perfectly```bash

  - 🟡 **OutOfSync**: Changes detected, waiting to sync# Install ArgoCD

  - 🔴 **Error**: Issues detected during synckubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

- **Health Status**:

  - 🟢 **Healthy**: All pods running normally# Verify ArgoCD deployment

  - 🟡 **Progressing**: Resources are being created/updatedkubectl get deployments -n argocd

  - 🔴 **Unhealthy**: Pods or services have issueskubectl get pods -n argocd

```

### Application Details View

#### 4.4 Verify ArgoCD Installation

Click on the application to see detailed information:

Check if all ArgoCD components are running:

![ArgoCD Tetris Version](Screenshots/argocdtetrisversion2.png)

```bash

### Resource Tree# List all ArgoCD pods

kubectl get pods -n argocd

The resource tree shows all Kubernetes resources managed by this application:

# Check ArgoCD services

**What's Displayed:**kubectl get svc -n argocd

- **Deployment**: tetris-deployment with 2 replicas

- **Service**: tetris-service (LoadBalancer)# Expected output should show:

- **Pods**: Individual pod instances# - argocd-server

- **ReplicaSets**: Manages pod replicas# - argocd-repo-server

# - argocd-controller-manager

**Relationships:**```

```

Application (tetris-app)**[INSERT SCREENSHOT: ArgoCD Pods Running]**

  ├── Deployment (tetris-deployment)

  │   ├── ReplicaSet---

  │   │   ├── Pod 1 (tetris-deployment-xxxxx)

  │   │   └── Pod 2 (tetris-deployment-yyyyy)### Step 5: Access ArgoCD Dashboard

  └── Service (tetris-service)

```#### 5.1 Port Forward to ArgoCD Server



![ArgoCD Tetris Version Game](Screenshots/argocdtetrisversiongame.png)Access the ArgoCD dashboard using port forwarding:



### Pod Status and Logs```bash

# Forward local port 8080 to ArgoCD server

Access individual pod information:kubectl port-forward svc/argocd-server -n argocd 8080:443

```

```bash

# View pod logs#### 5.2 Get Initial Admin Password

kubectl logs pod/tetris-deployment-xxxxx

Retrieve the default admin password:

# Describe pod

kubectl describe pod/tetris-deployment-xxxxx```bash

# Get the initial admin password

# Get pod eventskubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d

kubectl get events -n default

```# On Windows PowerShell:

kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d; echo

![ArgoCD Tetris Version Interface](Screenshots/argocdtetrisversioninterface.png)```



### Sync Management#### 5.3 Login to ArgoCD



#### Manual SyncOpen your browser and navigate to: `https://localhost:8080`



If auto-sync is disabled, manually sync by:- **Username**: admin

1. Click the **SYNC** button on the application card- **Password**: [Use the password from Step 5.2]

2. Review changes

3. Click **SYNCHRONIZE**![ArgoCD Login](Screenshots/ArgoCdLogin.png)



#### Sync Status Indicators![Successful ArgoCD Login](Screenshots/successful_login_argocd.png)



- **Status**: Shows current sync state#### 5.4 Change Default Password

- **Last Sync**: Time of last synchronization

- **Next Sync**: If auto-sync is scheduledOnce logged in, change the admin password:



### Application History1. Click on **Settings** (gear icon)

2. Navigate to **Accounts**

View deployment history:3. Click **Update Password**

1. Click on the application4. Enter your new secure password

2. Navigate to **HISTORY** tab

3. View all previous syncs and deployments---

4. Rollback to previous versions if needed

### Step 6: Connect GitHub Repository

### Repository Information

#### 6.1 Create GitHub Repository Connection

View repository and revision details:

- **Repository**: Your Git repository URLConnect your GitHub repository to ArgoCD:

- **Branch**: main

- **Path**: manifest/1. Go to **Settings** → **Repositories** in ArgoCD dashboard

- **Current Commit**: Latest commit hash being deployed2. Click **Connect Repo**

3. Select **VIA HTTPS** or **VIA SSH** (HTTPS recommended for simplicity)

---

**[INSERT SCREENSHOT: Connect Repository Screen]**

## Project Structure

#### 6.2 Enter Repository Details

```

GitOpsTetrisProject/Provide your repository information:

├── README.md                          # This comprehensive guide

├── manifest/```

│   ├── tetris-deploy.yaml            # Kubernetes Deployment manifestRepository URL: https://github.com/samuel-nartey/GitOpsTetrisProject

│   │   └── Defines 2 replicas of tetris-v2 image```

│   │   └── Exposes port 80

│   └── tetris-svc.yaml               # Kubernetes Service manifest![Connecting GitHub Repo 1](Screenshots/connecdtingithubrepo.png)

│       └── LoadBalancer service

│       └── Routes traffic to deployment pods![Connecting GitHub Repo 2](Screenshots/connecdtingithubrepo2.png)

└── Screenshots/                       # Documentation images

    ├── ArgoCDP1.drawio.png           # Architecture diagram![Connecting GitHub Repo 3](Screenshots/connecdtingithubrepo3.png)

    ├── EKS*.png                      # EKS cluster setup screenshots

    ├── argocd*.png                   # ArgoCD dashboard screenshots#### 6.3 Verify Repository Connection

    └── tetrisgamedeployed*.png       # Deployment success screenshots

```Once connected, you should see your repository in the repositories list:



### Manifest Details**[INSERT SCREENSHOT: Repository Connected Successfully]**



#### tetris-deploy.yaml---



```yaml### Step 7: Create ArgoCD Application

apiVersion: apps/v1

kind: Deployment#### 7.1 Create New Application

metadata:

  name: tetris-deploymentCreate an ArgoCD Application to deploy the Tetris game:

spec:

  replicas: 2          # Two instances of the game1. Click **+ NEW APP** on the ArgoCD dashboard

  selector:2. Fill in the application details

    matchLabels:

      app: tetris      # Selector for pod labeling**Application Configuration:**

  template:

    metadata:```

      labels:Application Name: tetris-app

        app: tetrisProject Name: default

    spec:Sync Policy: Automatic

      containers:

        - name: tetrisSource:

          image: nasi101/tetrisv2   # Docker image  Repository URL: https://github.com/samuel-nartey/GitOpsTetrisProject

          ports:  Revision: main

            - containerPort: 80     # Container port  Path: manifest

```

Destination:

#### tetris-svc.yaml  Cluster: https://kubernetes.default.svc (in-cluster)

  Namespace: default

```yaml```

apiVersion: v1

kind: Service![Create App in ArgoCD 1](Screenshots/createappinargocd.png)

metadata:

  name: tetris-service#### 7.2 Configure Sync Settings

spec:

  selector:Set up automatic synchronization:

    app: tetris          # Matches deployment pods

  ports:```yaml

    - protocol: TCPSync Policy: Automatic

      port: 80           # External portAuto-Prune: Enabled

      targetPort: 80     # Container portSelf-Heal: Enabled

  type: LoadBalancer    # External access via AWS NLB/ALB```

```

This ensures ArgoCD automatically:

---- Syncs changes from Git to the cluster

- Removes resources deleted from Git

## Kubernetes Commands Reference- Reconciles drift between Git and cluster



### Cluster Information**[INSERT SCREENSHOT: Sync Policy Configuration]**



```bash#### 7.3 Create the Application

# Get cluster info

kubectl cluster-infoClick **CREATE** to deploy the application:



# Get nodes**[INSERT SCREENSHOT: Application Creation Complete]**

kubectl get nodes

---

# Describe a node

kubectl describe node <node-name>### Step 8: Verify Deployment

```

#### 8.1 Monitor Application Sync

### Deployments

Watch the ArgoCD dashboard as it syncs your application:

```bash

# List deployments![ArgoCD Tetris Synching](Screenshots/argocdtetrissynching.png)

kubectl get deployments

![ArgoCD Tetris Synching Detail](Screenshots/argocdtetrissynching1.png)

# Get deployment details

kubectl describe deployment tetris-deployment#### 8.2 Verify Kubernetes Deployment



# Scale deploymentCheck the deployment status in your cluster:

kubectl scale deployment tetris-deployment --replicas=3

```bash

# Update deployment image# List deployments

kubectl set image deployment/tetris-deployment tetris=nasi101/tetrisv2:latestkubectl get deployments

```

# List services

### Serviceskubectl get services



```bash# List pods

# List serviceskubectl get pods

kubectl get services

# Describe tetris service

# Get service detailskubectl describe svc tetris-service

kubectl describe svc tetris-service

# Get service external IP

# Get external IPkubectl get svc tetris-service -o jsonpath='{.status.loadBalancer.ingress[0].hostname}'

kubectl get svc tetris-service -o jsonpath='{.status.loadBalancer.ingress[0].hostname}'```

```

#### 8.3 Application Deployment Success

### Pods

Your application is now deployed and running:

```bash

# List pods![Tetris Deployment Success 1](Screenshots/tetrisgamedeployedsuccess.png)

kubectl get pods

![Tetris Deployment Success 2](Screenshots/tetrisgamedeployedsuccess2.png)

# Get pod details

kubectl describe pod <pod-name>![Tetris Deployment Success 3](Screenshots/tetrisgamedeployedsuccess3.png)



# View pod logs![Tetris Deployment Success 4](Screenshots/tetrisgamedeployedsuccess4.png)

kubectl logs <pod-name>

#### 8.4 Access the Tetris Game

# Tail logs in real-time

kubectl logs -f <pod-name>Get the external IP/hostname and access the Tetris game:



# Execute command in pod```bash

kubectl exec -it <pod-name> -- /bin/bash# Get LoadBalancer external IP

```kubectl get svc tetris-service



### Namespaces# Access at: http://<EXTERNAL-IP>

```

```bash

# List namespaces---

kubectl get namespaces

## ArgoCD Dashboard Guide

# Create namespace

kubectl create namespace my-namespace### Dashboard Overview



# List resources in namespaceThe ArgoCD dashboard displays all your applications and their deployment status:

kubectl get all -n argocd

```![ArgoCD Interface](Screenshots/argocdinterface.png)



### ArgoCD Specific### Application Card Details



```bashEach application card shows:

# List ArgoCD pods

kubectl get pods -n argocd- **Application Name**: tetris-app

- **Sync Status**: 

# Get ArgoCD services  - 🟢 **Synced**: Git and cluster state match perfectly

kubectl get svc -n argocd  - 🟡 **OutOfSync**: Changes detected, waiting to sync

  - 🔴 **Error**: Issues detected during sync

# Port forward ArgoCD- **Health Status**:

kubectl port-forward svc/argocd-server -n argocd 8080:443  - 🟢 **Healthy**: All pods running normally

  - 🟡 **Progressing**: Resources are being created/updated

# Get admin password  - 🔴 **Unhealthy**: Pods or services have issues

kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d

```### Application Details View



---Click on the application to see detailed information:



## Testing GitOps: Making Changes![ArgoCD Tetris Version](Screenshots/argocdtetrisversion2.png)



### Update Application Version### Resource Tree



Test GitOps by updating the application version:The resource tree shows all Kubernetes resources managed by this application:



1. Edit `manifest/tetris-deploy.yaml`:**What's Displayed:**

- **Deployment**: tetris-deployment with 2 replicas

```yaml- **Service**: tetris-service (LoadBalancer)

containers:- **Pods**: Individual pod instances

  - name: tetris- **ReplicaSets**: Manages pod replicas

    image: nasi101/tetrisv2:v2  # Update the tag

```**Relationships:**

```

2. Commit and push to Git:Application (tetris-app)

  ├── Deployment (tetris-deployment)

```bash  │   ├── ReplicaSet

git add manifest/tetris-deploy.yaml  │   │   ├── Pod 1 (tetris-deployment-xxxxx)

git commit -m "feat: updated tetris to version 2"  │   │   └── Pod 2 (tetris-deployment-yyyyy)

git push origin main  └── Service (tetris-service)

``````



3. Watch ArgoCD sync the changes automatically (if auto-sync enabled):![ArgoCD Tetris Version Game](Screenshots/argocdtetrisversiongame.png)



![New Commit for ArgoCD](Screenshots/newcommitforargo.png)### Pod Status and Logs



### View Changes in ArgoCDAccess individual pod information:



In the ArgoCD dashboard, you'll see:```bash

- **OutOfSync** status appears# View pod logs

- **Diff** shows the image version changekubectl logs pod/tetris-deployment-xxxxx

- **SYNC** button becomes available

- After sync, application updates automatically# Describe pod

kubectl describe pod/tetris-deployment-xxxxx

---

# Get pod events

## Troubleshootingkubectl get events -n default

```

### ArgoCD Issues

![ArgoCD Tetris Version Interface](Screenshots/argocdtetrisversioninterface.png)

#### ArgoCD Server Not Accessible

### Sync Management

```bash

# Check if ArgoCD pods are running#### Manual Sync

kubectl get pods -n argocd

If auto-sync is disabled, manually sync by:

# Check ArgoCD service1. Click the **SYNC** button on the application card

kubectl get svc -n argocd2. Review changes

3. Click **SYNCHRONIZE**

# Port forward if needed

kubectl port-forward svc/argocd-server -n argocd 8080:443#### Sync Status Indicators

```

- **Status**: Shows current sync state

#### Cannot Connect to Repository- **Last Sync**: Time of last synchronization

- **Next Sync**: If auto-sync is scheduled

```bash

# Check repository connection### Application History

kubectl logs -n argocd -l app.kubernetes.io/name=argocd-repo-server

View deployment history:

# Verify GitHub credentials are correct1. Click on the application

# Reconnect repository in ArgoCD settings2. Navigate to **HISTORY** tab

```3. View all previous syncs and deployments

4. Rollback to previous versions if needed

### Deployment Issues

### Repository Information

#### Pods Not Running

View repository and revision details:

```bash- **Repository**: Your Git repository URL

# Check pod status- **Branch**: main

kubectl describe pod <pod-name>- **Path**: manifest/

- **Current Commit**: Latest commit hash being deployed

# Check pod events

kubectl get events---



# View pod logs## Project Structure

kubectl logs <pod-name>

``````

GitOpsTetrisProject/

#### Service External IP Pending├── README.md                          # This comprehensive guide

├── manifest/

```bash│   ├── tetris-deploy.yaml            # Kubernetes Deployment manifest

# Check service status│   │   └── Defines 2 replicas of tetris-v2 image

kubectl describe svc tetris-service│   │   └── Exposes port 80

│   └── tetris-svc.yaml               # Kubernetes Service manifest

# Wait for AWS to provision load balancer│       └── LoadBalancer service

# This typically takes 2-5 minutes│       └── Routes traffic to deployment pods

kubectl get svc tetris-service -w└── Screenshots/                       # Documentation images

```    ├── ArgoCDP1.drawio.png           # Architecture diagram

    ├── EKS*.png                      # EKS cluster setup screenshots

### Kubernetes Issues    ├── argocd*.png                   # ArgoCD dashboard screenshots

    └── tetrisgamedeployed*.png       # Deployment success screenshots

#### Node Not Ready```



```bash### Manifest Details

# Check node status

kubectl get nodes#### tetris-deploy.yaml



# Describe problematic node```yaml

kubectl describe node <node-name>apiVersion: apps/v1

kind: Deployment

# Check node logs (via SSH or EC2 console)metadata:

```  name: tetris-deployment

spec:

#### Insufficient Resources  replicas: 2          # Two instances of the game

  selector:

```bash    matchLabels:

# Check cluster resources      app: tetris      # Selector for pod labeling

kubectl describe nodes  template:

    metadata:

# Add more nodes to node group or increase instance size      labels:

```        app: tetris

    spec:

---      containers:

        - name: tetris

## Best Practices          image: nasi101/tetrisv2   # Docker image

          ports:

### GitOps Principles            - containerPort: 80     # Container port

```

1. **Git as Source of Truth**

   - All configurations in Git#### tetris-svc.yaml

   - No manual kubectl apply commands on production

   - Every change tracked and auditable```yaml

apiVersion: v1

2. **Declarative Infrastructure**kind: Service

   - Define desired state in YAMLmetadata:

   - Let GitOps operators enforce that state  name: tetris-service

   - Automatic drift detection and correctionspec:

  selector:

3. **Automated Deployment**    app: tetris          # Matches deployment pods

   - Set auto-sync for production readiness  ports:

   - Pipeline integrates with Git workflows    - protocol: TCP

   - Zero-downtime deployments possible      port: 80           # External port

      targetPort: 80     # Container port

4. **Version Control**  type: LoadBalancer    # External access via AWS NLB/ALB

   - All changes tracked with git history```

   - Easy rollbacks to previous versions

   - Clear audit trail for compliance---



### Security Best Practices## Kubernetes Commands Reference



1. **Change Default Credentials**### Cluster Information

   - Always change ArgoCD admin password

   - Use strong, unique passwords```bash

# Get cluster info

2. **RBAC Configuration**kubectl cluster-info

   - Implement role-based access control

   - Limit service account permissions# Get nodes

   - Use separate service accounts per applicationkubectl get nodes



3. **Repository Security**# Describe a node

   - Use SSH keys for private repositorieskubectl describe node <node-name>

   - Enable branch protection rules```

   - Require pull request reviews

### Deployments

4. **Secret Management**

   - Never commit secrets to Git```bash

   - Use tools like AWS Secrets Manager or HashiCorp Vault# List deployments

   - Implement secret scanning in CI/CDkubectl get deployments



### Resource Management# Get deployment details

kubectl describe deployment tetris-deployment

1. **Resource Requests and Limits**

   ```yaml# Scale deployment

   resources:kubectl scale deployment tetris-deployment --replicas=3

     requests:

       memory: "64Mi"# Update deployment image

       cpu: "250m"kubectl set image deployment/tetris-deployment tetris=nasi101/tetrisv2:latest

     limits:```

       memory: "128Mi"

       cpu: "500m"### Services

   ```

```bash

2. **Horizontal Pod Autoscaling**# List services

   ```yamlkubectl get services

   apiVersion: autoscaling/v2

   kind: HorizontalPodAutoscaler# Get service details

   metadata:kubectl describe svc tetris-service

     name: tetris-hpa

   spec:# Get external IP

     scaleTargetRef:kubectl get svc tetris-service -o jsonpath='{.status.loadBalancer.ingress[0].hostname}'

       apiVersion: apps/v1```

       kind: Deployment

       name: tetris-deployment### Pods

     minReplicas: 2

     maxReplicas: 10```bash

     metrics:# List pods

     - type: Resourcekubectl get pods

       resource:

         name: cpu# Get pod details

         target:kubectl describe pod <pod-name>

           type: Utilization

           averageUtilization: 70# View pod logs

   ```kubectl logs <pod-name>



---# Tail logs in real-time

kubectl logs -f <pod-name>

## Future Enhancements

# Execute command in pod

- [ ] Add Ingress for custom domainkubectl exec -it <pod-name> -- /bin/bash

- [ ] Implement HorizontalPodAutoscaler for auto-scaling```

- [ ] Add persistent storage for game state

- [ ] Configure resource requests and limits### Namespaces

- [ ] Add liveness and readiness probes

- [ ] Implement network policies for security```bash

- [ ] Set up monitoring with Prometheus# List namespaces

- [ ] Add logging with CloudWatch/ELKkubectl get namespaces

- [ ] Implement CI/CD pipeline

- [ ] Add multi-environment deployments (dev, staging, prod)# Create namespace

kubectl create namespace my-namespace

---

# List resources in namespace

## Additional Resourceskubectl get all -n argocd

```

### Official Documentation

### ArgoCD Specific

- [AWS EKS Documentation](https://docs.aws.amazon.com/eks/)

- [Kubernetes Documentation](https://kubernetes.io/docs/)```bash

- [ArgoCD Documentation](https://argo-cd.readthedocs.io/)# List ArgoCD pods

- [GitOps Best Practices](https://www.gitops.tech/)kubectl get pods -n argocd



### Useful Tools# Get ArgoCD services

kubectl get svc -n argocd

- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

- [ArgoCD CLI Reference](https://argo-cd.readthedocs.io/en/stable/cli_installation/)# Port forward ArgoCD

- [AWS CLI Reference](https://docs.aws.amazon.com/cli/latest/userguide/)kubectl port-forward svc/argocd-server -n argocd 8080:443



### Learning Resources# Get admin password

kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d

- [Kubernetes by Example](https://www.kubernetesbyexample.com/)```

- [ArgoCD Tutorial](https://argo-cd.readthedocs.io/en/stable/getting_started/)

- [GitOps with ArgoCD](https://www.digitalocean.com/community/tutorials/how-to-deploy-to-kubernetes-with-argocd-and-gitops)---



---## Testing GitOps: Making Changes



## License### 8.1 Update Application Version



This project is part of the 12-week challenge personal project series.Test GitOps by updating the application version:



## Author1. Edit `manifest/tetris-deploy.yaml`:



**samuel-nartey**```yaml

containers:

Repository: [GitOpsTetrisProject](https://github.com/samuel-nartey/GitOpsTetrisProject)  - name: tetris

    image: nasi101/tetrisv2:v2  # Update the tag

---```



## Version History2. Commit and push to Git:



| Version | Date | Changes |```bash

|---------|------|---------|git add manifest/tetris-deploy.yaml

| 1.0 | November 12, 2025 | Initial comprehensive setup guide with EKS and ArgoCD |git commit -m "feat: updated tetris to version 2"

git push origin main

---```



**Last Updated**: November 12, 20253. Watch ArgoCD sync the changes automatically (if auto-sync enabled):



**Status**: ✅ Complete - Ready for Production Use![New Commit for ArgoCD](Screenshots/newcommitforargo.png)


### 8.2 View Changes in ArgoCD

In the ArgoCD dashboard, you'll see:
- **OutOfSync** status appears
- **Diff** shows the image version change
- **SYNC** button becomes available
- After sync, application updates automatically

---

## Troubleshooting

### ArgoCD Issues

#### ArgoCD Server Not Accessible

```bash
# Check if ArgoCD pods are running
kubectl get pods -n argocd

# Check ArgoCD service
kubectl get svc -n argocd

# Port forward if needed
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

#### Cannot Connect to Repository

```bash
# Check repository connection
kubectl logs -n argocd -l app.kubernetes.io/name=argocd-repo-server

# Verify GitHub credentials are correct
# Reconnect repository in ArgoCD settings
```

### Deployment Issues

#### Pods Not Running

```bash
# Check pod status
kubectl describe pod <pod-name>

# Check pod events
kubectl get events

# View pod logs
kubectl logs <pod-name>
```

#### Service External IP Pending

```bash
# Check service status
kubectl describe svc tetris-service

# Wait for AWS to provision load balancer
# This typically takes 2-5 minutes
kubectl get svc tetris-service -w
```

### Kubernetes Issues

#### Node Not Ready

```bash
# Check node status
kubectl get nodes

# Describe problematic node
kubectl describe node <node-name>

# Check node logs (via SSH or EC2 console)
```

#### Insufficient Resources

```bash
# Check cluster resources
kubectl describe nodes

# Add more nodes to node group or increase instance size
```

---

## Best Practices

### GitOps Principles

1. **Git as Source of Truth**
   - All configurations in Git
   - No manual kubectl apply commands on production
   - Every change tracked and auditable

2. **Declarative Infrastructure**
   - Define desired state in YAML
   - Let GitOps operators enforce that state
   - Automatic drift detection and correction

3. **Automated Deployment**
   - Set auto-sync for production readiness
   - Pipeline integrates with Git workflows
   - Zero-downtime deployments possible

4. **Version Control**
   - All changes tracked with git history
   - Easy rollbacks to previous versions
   - Clear audit trail for compliance

### Security Best Practices

1. **Change Default Credentials**
   - Always change ArgoCD admin password
   - Use strong, unique passwords

2. **RBAC Configuration**
   - Implement role-based access control
   - Limit service account permissions
   - Use separate service accounts per application

3. **Repository Security**
   - Use SSH keys for private repositories
   - Enable branch protection rules
   - Require pull request reviews

4. **Secret Management**
   - Never commit secrets to Git
   - Use tools like AWS Secrets Manager or HashiCorp Vault
   - Implement secret scanning in CI/CD

### Resource Management

1. **Resource Requests and Limits**
   ```yaml
   resources:
     requests:
       memory: "64Mi"
       cpu: "250m"
     limits:
       memory: "128Mi"
       cpu: "500m"
   ```

2. **Horizontal Pod Autoscaling**
   ```yaml
   apiVersion: autoscaling/v2
   kind: HorizontalPodAutoscaler
   metadata:
     name: tetris-hpa
   spec:
     scaleTargetRef:
       apiVersion: apps/v1
       kind: Deployment
       name: tetris-deployment
     minReplicas: 2
     maxReplicas: 10
     metrics:
     - type: Resource
       resource:
         name: cpu
         target:
           type: Utilization
           averageUtilization: 70
   ```

---

## Future Enhancements

- [ ] Add Ingress for custom domain
- [ ] Implement HorizontalPodAutoscaler for auto-scaling
- [ ] Add persistent storage for game state
- [ ] Configure resource requests and limits
- [ ] Add liveness and readiness probes
- [ ] Implement network policies for security
- [ ] Set up monitoring with Prometheus
- [ ] Add logging with CloudWatch/ELK
- [ ] Implement CI/CD pipeline
- [ ] Add multi-environment deployments (dev, staging, prod)

---

## Additional Resources

### Official Documentation

- [AWS EKS Documentation](https://docs.aws.amazon.com/eks/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [ArgoCD Documentation](https://argo-cd.readthedocs.io/)
- [GitOps Best Practices](https://www.gitops.tech/)

### Useful Tools

- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
- [ArgoCD CLI Reference](https://argo-cd.readthedocs.io/en/stable/cli_installation/)
- [AWS CLI Reference](https://docs.aws.amazon.com/cli/latest/userguide/)

### Learning Resources

- [Kubernetes by Example](https://www.kubernetesbyexample.com/)
- [ArgoCD Tutorial](https://argo-cd.readthedocs.io/en/stable/getting_started/)
- [GitOps with ArgoCD](https://www.digitalocean.com/community/tutorials/how-to-deploy-to-kubernetes-with-argocd-and-gitops)

---

## License

This project is part of the 12-week challenge personal project series.

## Author

**samuel-nartey**

Repository: [GitOpsTetrisProject](https://github.com/samuel-nartey/GitOpsTetrisProject)

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | November 12, 2025 | Initial comprehensive setup guide with EKS and ArgoCD |

---

**Last Updated**: November 12, 2025

**Status**: ✅ Complete - Ready for Production Use
