# GCCL-General-NLP2-FlowerTune

---

### Evaluation for General NLP challenge (Result of 10th checkpoint out of 10 total rounds)

|        | STEM  | SS    | Humanities | Avg   |
| :-----: | ----- | ----- | :--------: | ----- |
| Acc (%) | 66.22 | 80.56 |   60.80   | 69.19 |

#### Changes from baseline

**<pyproject.toml>**

`model.name = "internlm/internlm3-8b-instruct"`

`num-server-rounds = 10`

**<models.py>**

```
peft_config = LoraConfig(
	target_modules=["q_proj", "v_proj"],
)
```

```
model = AutoModelForCausalLM.from_pretrained(
        trust_remote_code=True,
    )
```

**<dataset.py>**

```
tokenizer = AutoTokenizer.from_pretrained(
	trust_remote_code=True,
    )
```

#### Evaluation Command

```
python eval.py \
--base-model-name-path=internlm/internlm3-8b-instruct \
--peft-path= \ # PEFT PATH - Checkpoint 10
--run-name= \ # RUN NAME
--batch-size=16 \
--quantization=4 \
--category=stem,social_sciences,humanities
```

#### Path to check evaluation results

```
GCCL-General-NLP2-FlowerTune/flowertune-eval-general-nlp/benchmarks/

# GCCL_generalnlp_peft10
```

#### Checkpoint Download

[Link](https://drive.google.com/drive/folders/14tnnVgCIbl77QwWvyizrcYYcFB7F-mrf?usp=sharing)
