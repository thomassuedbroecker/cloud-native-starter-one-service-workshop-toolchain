# [Toolchain for the 'Cloud Native Starter Workshop' - 'Deploying Java Microservices to Kubernetes on IBM Cloud'](https://github.com/IBM/cloud-native-starter/tree/master/workshop-one-service)

This protect does automate the deployment in [Lab 4](https://github.com/IBM/cloud-native-starter/blob/master/workshop-one-service/4-kubernetes.md) of the authors microservice of the Cloud Native Starter workshop [Deploying Java Microservices to Kubernetes on IBM Cloud](https://github.com/IBM/cloud-native-starter/tree/master/workshop-one-service) to a free Kubernetes cluster on IBM Cloud.

That are the steps it automates:

* Build the container for the authors microservice
* Save the container in the IBM Cloud Registry
* Deploy the authors microservice to the free Kubernetes cluster on IBM Cloud

In the image you get an overview of the authors microservice deployment to the free IBM Cloud Kubernetes Cluster.

![verview of the authors microservice deployment](images/lab-4-overview.png)


# Table of Content

[IBM Cloud Setup](#part-SECTION-00)
1. [Register for IBM Cloud](#part-SETUP-00)
2. [Insert feature code](#part-SETUP-01)
3. [Create a free Kubernetes cluster](#part-SETUP-02)
4. [Configure the IBM Cloud Container Registry](#part-SETUP-03)

[Toolchain setup and execution](#part-SECTION-02)
1. [Build a IBM Cloud toolchain](#part-SETUP-04)
2. [Work with the created toolchain](#part-SETUP-05)



# IBM Cloud Setup <a name="part-SECTION-00"></a>

## 1. Register for IBM Cloud <a name="part-SETUP-00"></a>

#### Step 1: Open a browser window and navigate to the IBM Cloud [Registration page](https://ibm.biz/Bd2JHx).

![Registration](images/registration.png)

#### Step 2: Fill in the registration form and follow the link in the **confirmation email** to confirm your account once it arrives.

![Email Validation](images/email.png)

#### Step 3: [Login into IBM Cloud](https://ibm.biz/Bd2JHx) using your account credentials.

_Note:_ By default, all new IBM Cloud accounts are set to a [lite account](https://www.ibm.com/cloud/pricing).

The lite account provides free access to a subset of IBM Cloud resources. Lite accounts **don't need a credit-card** to sign up and they **don't expire** after a certain period of time. 
In order to create a free Kubernetes cluster, you need a **feature code**.

---

## 2 Insert feature code <a name="part-SETUP-01"></a>

In order to execute the workshop easily, we provide **feature codes** to create free Kubernetes clusters, so no credit card details are required.
To apply the feature code to your [Cloud Account](https://cloud.ibm.com/account), navigate to your "`Account settings`" and then to ("`Manage`" -> "`Account`").
Enter your unique Feature (Promo) Code to upgrade your lite account.

_Note:_ Free clusters expire after one month.

---

## 3 Create a free Kubernetes Cluster <a name="part-SETUP-02"></a>

#### Step 1: Logon to IBM Cloud

#### Step 2: Select in the menu "Catalog" and search for "Kubernetes Cluster"

![Kubernetes service](images/ibmcloud-catalog.png)

#### Step 3: Click on "Kubernetes Cluster"

#### Step 4: Press "Create"

![create Kubernetes service](images/ibmcloud-create-kubernetes-1.png)

#### Step 5: Click on the Kubernetes Services and select "Free"

Ensure you set following values in the creation dialog and don't change the remaining values:

* Cluster name:     cloud-native

_Note:_ In the new IBM Cloud UI it seems the enties for Geography and Metro are no longer available.

![create Kubernetes service](images/ibmcloud-create-kubernetes-2.png)

#### Step 6: Press "Create custer"

#### Step 7: Now you will be forwarded to your cluster on IBM Cloud and you can verify the status of the creation of your cluster

The creation of the custer takes up to 20 min.

![create Kubernetes service](images/ibmcloud-create-kubernetes-3.png)

## 4 Configure the IBM Cloud Container Registry <a name="part-SETUP-03"></a>

#### Step 1: Select in **Kubernetes** the entry **Registry** and ensure your are in the **Dallas location**.

![Select in Kubernetes the entry Registry](images/ibmcloud-configure-container-registry-1.png)

#### Step 2: The create a namespace with a unique name cloud-native-[YOURNAME]

![The create a namespace with a unique name cloud-native](images/ibmcloud-configure-container-registry-2.png)

_Note:_ Namespaces are required to be **unique** across the entire **region** that the **specific registry** is located in, not just ***unique to your account**. This is mentioned in the following [public documentation](https://cloud.ibm.com/docs/services/Registry?topic=registry-getting-started#gs_registry_namespace_add).

#### Step 3: Verify the namespace was created

![Verify the namespace was created](images/ibmcloud-configure-container-registry-3.png)

# Toolchain setup and execution <a name="part-SECTION-00"></a>

## 1 Build a IBM Cloud toolchain <a name="part-SETUP-04"></a>

#### Step 1: Press "Create toolchain"

[![Create toolchain](https://cloud.ibm.com/devops/graphics/create_toolchain_button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fthomassuedbroecker%2Fcloud-native-starter-one-service-workshop-toolchain)

#### Step 2: Select the Dalles as region

![Select the Dalles region](images/toolchain-01.png)


#### Step 3: Configure the location for the cloned github project

I our situation we use **git repos and issue tracking hosted by IBM and built on GitLab Community Edition**.

We will clone the _Cloud Native Starter_ project to a repository called **cloud-native-starter-one-service-workshop**-TIMESTAMP.  

![Configure the location for the cloned github project](images/toolchain-02.png)

```diff
- _Note:_ Depending on your region selection you maybe have to authorize the GitLab hosted in that IBM region.
```

![Authorize the GitLab hosted in that IBM region](images/toolchain-03.png)

#### Step 4: Create a IBM Cloud API key by pressing "new" and "ok"

Enable the toolchain to create services or set configurations in your IBM Cloud Account, for that it needs an "IBM Cloud API key" depending the region you are working in.

![Create a IBM Cloud API key](images/toolchain-04.png)

_Note:_ You will be informed which name is used.

![Notification dialog](images/toolchain-05.png)

#### Step 5: Verify the configuration

You see your the relevant information of your created IBM Cloud Container Registry and the IBM Cloud Cluster.
Do not change the defaults!

![IBM Cloud Container Registry and the IBM Cloud Cluster information](images/toolchain-06.png)

_Note:_ Especially don't change the Kubernetes namespace name, because you need to know the image pull secret credentials to access a container registry. 
For more details visit the following pages.

* [Documentation on IBM Cloud](https://cloud.ibm.com/docs/containers?topic=containers-images)
* [Documentation on Kubernetes](https://kubernetes.io/docs/concepts/containers/images/)

#### Step 6: Press "Create"

![Press Create](images/toolchain-07.png)

## 2 Work with the created toolchain <a name="part-SETUP-05"></a>

I the toolchain you see:

* **Think** Issues managed in GitLab
* **Code**  [Eclipse Orion Web IDE](https://cloud.ibm.com/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide) and source code managed in GitLab
* **Delivery** Managed in the in the [Continues Delivery service](https://cloud.ibm.com/catalog/services/continuous-delivery#about)

#### Step 1: Visit the create GitLab project inside IBM Cloud

Open the GitLab repository in a new browser tab.

![Open the GitLab repository in a new browser tab](images/toolchain-08.png)

#### Step 2: Take a look in the cloned Cloud Native Starter project 

![Take a look in the cloned Cloud Native Starter project](images/toolchain-09.png)

#### Step 3: Go back to the toolchain and visit the delivey pipeline

![Open the delivery pipeline](images/toolchain-10.png)

#### Step 4: In the delivery pipeline you see two stages 

* FETCH _Does copy the source code in the Fetch code job, to the pipeline to provide the source code as an input for the DEPLOY SERVICES Stage_
* DEPLOY SERVICES _Does a build and deploy job to deploy the authors microservice to the Kubernetes cluster on IBM Cloud._

![Open the delivery pipeline](images/toolchain-11.png)

Wait until the stages are executed:

![Running delivery pipeline](images/toolchain-01.gif)



# 7 Information resources about developing a open toolchain

* [Creating Custom Toolchain Templates](https://github.com/open-toolchain/sdk/wiki/Creating-Custom-Toolchain-Templates)
* [Configuring tool integrations](https://cloud.ibm.com/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations)