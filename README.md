# Open Data Hub Custom Notebook Size

## Goal

Add a custom notebook size to the JupyterHub spawner in ODH

## Prerequisites

1. Install [Open Data Hub](https://opendatahub.io)

## Steps

1. In the OpenShift Web Console, navigate to the namespace where ODH is installed
2. Click `ConfigMaps` in the navigation panel
3. Click the `Create ConfigMap` button
4. Paste the below sample `ConfigMap` over all default text. You will need to update the namespace. Adjust the name and CPU/ Memory to your needs.

    ```yaml
    kind: ConfigMap
    apiVersion: v1
    metadata:
      name: developer-jupyterhub-sizes
      namespace: sepsis
      labels:
        jupyterhub: singleuser-profiles
    data:
      jupyterhub-singleuser-profiles.yaml: |
        sizes:
          - name: XX-Large-Memory
            resources:
              requests:
                memory: 1Gi
                cpu: 1
              limits:
                memory: 16Gi
                cpu: 4
    ```

5. Click `Create`

6. Navigate to your ODH deployed JupyterHub spawner. You will see the custom notebook size `XX-Large-Memory` in the list of available notebook sizes!
