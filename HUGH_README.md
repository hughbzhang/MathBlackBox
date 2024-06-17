Steps to repro:

```
conda create --name mcts python=3.10
pip install -r requirements.txt

# Start the vllm server on 8 GPUs
python -m vllm.entrypoints.openai.api_server --model meta-llama/Meta-Llama-3-8B-Instruct --host 127.0.0.1 --port 10000 --tensor-parallel-size=8
python run_with_earlystopping.py meta-llama/Meta-Llama-3-8B-Instruct gsm8k-llama3-8b-new-mcts-8
'''

Current code maps to the wrong answer. Delete the following section to replicate paper claims.

```
 def map(ans):
    int_ans = int(ans.split("####")[-1].strip().replace(",", ""))
    int_ans = int_ans + 1
    return str(int_ans)

dataset = dataset.map(lambda x: {"answer": map(x['answer'])})
```





