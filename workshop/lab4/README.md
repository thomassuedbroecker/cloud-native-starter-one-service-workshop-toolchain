### Lab 4: Configure the IBM Cloud Container Registry

---

### Step 1: Select in **Kubernetes** the entry **Registry** and ensure your are in the **Dallas location**.

![Select in Kubernetes the entry Registry](../../images/ibmcloud-configure-container-registry-1.png)

---

### Step 2: The create a namespace with a unique name cloud-native-\[YOURNAME\]

![The create a namespace with a unique name cloud-native](../../images/ibmcloud-configure-container-registry-2.png)

_Note:_ Namespaces are required to be **unique** across the entire **region** that the **specific registry** is located in, not just **unique to your account**. This is mentioned in the following [public documentation](https://cloud.ibm.com/docs/services/Registry?topic=registry-getting-started#gs_registry_namespace_add).

---

#### Step 3: Verify the namespace was created

![Verify the namespace was created](../../images/ibmcloud-configure-container-registry-3.png)
