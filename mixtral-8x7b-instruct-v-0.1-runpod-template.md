## How to Deploy Mixtral-8x7B-Instruct-v0.1 on Runpod
1. Use [this Runpod template](https://www.runpod.io/console/gpu-secure-cloud?ref=80eh3891&template=3lw00z6bjm) to deploy a Pod using an A100 (80GB) GPU instance.
2. Once the Pod is initiated, connect to it using the web terminal.
3. Install the "transformers" library from the GitHub repository.

```
apt update && sudo apt upgrade
pip install --upgrade pip
apt-get install -y git
pip install -q -U git+https://github.com/huggingface/transformers.git
```
4. Install Flash Attention.
```
FLASH_ATTENTION_SKIP_CUDA_BUILD=TRUE pip install flash-attn --no-build-isolation
```

5. Check the Pod logs to ensure that the model has been downloaded, and you see a "connected" message towards the end of the logs. This process may take 20-30 minutes and might require 4-5 Pod restarts. There are issues with model downloads causing it to get stuck, so monitor the RAM usage and logs to determine if it's loading or not.

Once connected, you can call the API at the Mixtral-8x7B-Instruct-v0.1 generation endpoint using code compatible with the OpenAI API at the following link.
```
https://{ENTER_YOUR_POD_ID}-8080.proxy.runpod.net
```
Here is a [Google Colab link](https://colab.research.google.com/drive/1jQAx3YbyNdY-NNPabMugwJ3pVZ7S3p2g#scrollTo=dqtCxoB002uy) with inference code.

## Mixtral-8x7B-Instruct-v0.1
The Mixtral-8x7B Large Language Model (LLM) is a pretrained generative Sparse Mixture of Experts. The Mixtral-8x7B outperforms Llama 2 70B on most benchmarks we tested.

[Learn More](https://huggingface.co/mistralai/Mixtral-8x7B-Instruct-v0.1)
