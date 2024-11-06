# Multi-Node Distributed Training on Azure ML

## Requirements

Before starting, you should meet the following requirements:

-   [Azure ML getting started](https://github.com/Azure/azureml-examples/tree/main/tutorials): Connect to [Azure ML] workspace and get your <WORKSPACE_NAME>, <RESOURCE_GROUP> and <SUBSCRIPTION_ID>.
-   [Azure AI Studio getting started](https://aka.ms/azureaistudio): Create a project

-   **_[Compute instance - for code development]_** A low-end instance without GPU is recommended: **[Standard_E2as_v4] (AMD 2 cores, 16GB RAM, 32GB storage) or **[Standard_DS11_v2]\*\* (Intel 2 cores, 14GB RAM, 28GB storage, No GPUs)
-   **_[Compute cluster]_** We recommend two **[Standard_NC24ads_A100_v4]]** nodes or two **[Standard_NC4ads_A100_v4]]** nodes
    single NVIDIA A100 GPU (**[Standard_NC24ads_A100_v4]**) is recommended. If you do not have a dedicated quota or are on a tight budget, choose **[Low-priority VM]**.
-   **_[SLM/LLM deployment]_** Two NVIDIA V100 GPUs (**[Standard_NC6s_v3]**) or two NVIDIA A100 GPUs (**[Standard_NC24ads_A100_v4]**) are recommended.

**Note**
For managed online endpoints, [Azure ML reserves 20% of the quota for the deployment].[^1] If you request a given number of instances for those VM SKUs in a deployment, you must have a quota for `ceil(1.2 × number of instances requested for deployment) × number of cores for the VM SKU` available to avoid getting an error. For example, if you request 1 instances of a `Standard_NC6s_v3` VM (that comes with six cores) in a deployment, you should have a quota for 12 cores (ceil(1.2 × 1 instances) = 2, 2 × 6 cores) available.

## How to get started

1. Create your compute instance. For code development, we recommend `Standard_DS11_v2` (2 cores, 14GB RAM, 28GB storage, No GPUs).
2. Open the terminal of the CI and run:
    ```shell
    git clone https://github.com/daekeun-ml/multinode-training-azureml
    conda activate azureml_py310_sdkv2
    pip install -r requirements.txt
    ```
3. Edit the `config.yml` file.

## References

-   [Azure Machine Learning examples](https://github.com/Azure/azureml-examples)
-   [Multi-Node Training with Hugging Face accelerate and AzureML](https://nateraw.com/posts/multinode_training_accelerate_azureml.html)

## License Summary

This sample code is provided under the MIT-0 license. See the LICENSE file.

[^1]: This extra quota is reserved for system-initiated operations such as OS upgrades and VM recovery, and it won't incur cost unless such operations run.
