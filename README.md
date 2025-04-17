# TrustyAI LM-Eval as and Out of Tree Llama Stack Provider

## Prerequsites
* Admin access to an OpenShift cluster
* Installation of `oc` cli tool
* Installation of `llama stack` server

1. Define the following environment variables
```bash
DK_BENCH_DATASET_PATH=
JUDGE_MODEL_URL=
JUDGE_MODEL_NAME=
JUDGE_API_KEY=
```
## Use
1. Create a virtual enviornment

1. Deploy a LLM on vLLM Serving Runtime
    a. Create a namespace named
    ```
    oc apply -f resources/models/phi-model-container.yaml
    ```

2. In the `run.yaml`, under the `providers.inference`, edit the `remote::vllm` URL to point to the inference endpoint of the deployed model

3. Start the llama stack server in a virtual enviornment
    ```
    llama stack run run.yaml --image-type venv
    ```

4. Navigate to `demo.ipynb` to run evaluation