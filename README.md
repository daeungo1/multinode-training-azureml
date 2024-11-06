# Multi-Node Distributed Training on Azure ML

## Requirements

Before starting, you should meet the following requirements:

-   [Azure ML getting started](https://github.com/Azure/azureml-examples/tree/main/tutorials): Connect to [Azure ML] workspace and get your <WORKSPACE_NAME>, <RESOURCE_GROUP> and <SUBSCRIPTION_ID>.
-   [Azure AI Studio getting started](https://aka.ms/azureaistudio): Create a project

-   **_[Compute instance - for code development]_** A low-end instance without GPU is recommended: **Standard_E2as_v4** (AMD 2 cores, 16GB RAM, 32GB storage) or **Standard_DS11_v2** (Intel 2 cores, 14GB RAM, 28GB storage, No GPUs)
-   **_[Compute cluster]_** We recommend two **Standard_NC24ads_A100_v4** nodes or two **Standard_NC4ads_A100_v4** nodes
    single NVIDIA A100 GPU (**Standard_NC24ads_A100_v4**) is recommended. If you do not have a dedicated quota or are on a tight budget, choose **Low-priority VM**.

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
