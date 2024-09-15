# lab6-kubernetes


# Kubernetes Volumes Exercises


## 1. What is a Volume in Kubernetes?

A volume in Kubernetes is a storage unit attached to a Pod that allows containers to persist data across container restarts. Unlike container storage, which is ephemeral and destroyed when the container is deleted, a Kubernetes volume outlasts the container lifecycle and can share data between containers within a Pod.

## 2. Types of Kubernetes Volumes

Kubernetes provides various types of volumes. Below are three commonly used types:

- **emptyDir**: A temporary directory that shares data between containers in a Pod. It exists as long as the Pod is running.
- **hostPath**: Mounts a file or directory from the host node’s filesystem into the Pod. Useful for accessing the host's files.
- **PersistentVolume (PV)**: Represents a piece of storage in the cluster that can be dynamically or statically provisioned. PersistentVolumes outlast individual Pod lifecycles and are used with PersistentVolumeClaims (PVC).

## 3. PersistentVolumes (PVs) and PersistentVolumeClaims (PVCs)

PVs are cluster-level resources representing physical storage, while PVCs are requests made by users for storage. A PVC is bound to a PV that meets its storage requirements. The PVC abstracts storage requests from the actual physical storage and allows Pods to use the underlying volume without worrying about where the storage comes from.

---

## Exercises

### 4. Create a Pod with an emptyDir Volume

Write a YAML file to define a Pod that uses an `emptyDir` volume to share data between two containers.

- **Task**: Deploy the Pod and verify that both containers can read/write data to the shared volume.

- ![.]([example.png](https://github.com/SaifmElnagar/lab6-kubernetes/blob/main/p4/Pasted%20image.png)
  
### 5. Set up a Pod with a hostPath Volume

Create a YAML definition for a Pod that mounts a `hostPath` volume to access files from the host node’s file system.

- **Task**: Deploy the Pod and verify it can read/write to the specified directory on the host node.

### 6. Deploy a PersistentVolume (PV) and PersistentVolumeClaim (PVC)

Define a PersistentVolume of 5Gi with `ReadWriteOnce` access mode. Then, create a PersistentVolumeClaim requesting 2Gi from this PV.

- **Task**: Deploy the resources and ensure the PVC is bound to the PV.

### 7. Create a Pod Using a PVC

Create a Pod YAML definition that uses the PVC from Exercise 6. Mount the PVC to a specific path inside the container.

- **Task**: Test and verify that the storage is accessible inside the Pod.

### 8. Dynamic Provisioning of PersistentVolumes

Create a `StorageClass` that uses a dynamic provisioner such as AWS EBS, GCE Persistent Disk, or NFS. Then, deploy a PVC requesting storage dynamically using this `StorageClass`.

- **Task**: Verify that the storage is provisioned dynamically.

### 9. Use a ConfigMap as a Volume

Create a `ConfigMap` with some configuration data. Write a YAML definition for a Pod that mounts this ConfigMap as a volume.

- **Task**: Verify the ConfigMap data is accessible inside the container.

### 10. Create a Pod with a Secret as a Volume

Create a Kubernetes Secret containing sensitive data. Write a YAML definition for a Pod that mounts the Secret as a volume.

- **Task**: Verify that the sensitive data is securely accessible inside the container.

### 11. Set up a Pod with a gitRepo Volume

Create a Pod that uses a `gitRepo` volume to clone a Git repository into the container.

- **Task**: Verify that the repository's contents are accessible inside the container.

### 12. Resize a PersistentVolumeClaim (PVC)

Create a PVC and bind it to a Pod. After deployment, resize the PVC to request more storage (if supported by the storage provider).

- **Task**: Verify that the PVC has been resized successfully.

### 13. Use subPath for Mounting Volumes

Create a Pod with a single volume and use the `subPath` feature to mount different subdirectories of that volume to various paths inside the container.

- **Task**: Verify that each path corresponds to the correct subdirectory.
