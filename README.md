# Fine-Tuning-Llama-2.0
Fine-Tuning my own Language Model


![Fine-Tuning_Llama_2 0](https://github.com/user-attachments/assets/72e1945b-d40c-4564-9655-920b7cc8f18b)


Parameter-Efficient Fine Tuning (PEFT) : QLoRA

fine-tuning a model with 65 billion parameters necessitates a staggering 780 GB of GPU memory, equivalent to ten A100 80 GB GPUs. Such resource demands have hindered the seamless fine-tuning of consumer hardware.

LoRA: Low-Rank Adaptation of Large Language Models

LoRA’s architecture involves freezing the pre-trained model weights and training the additional weight changes in a matrix without sacrificing crucial information. This process occurs in each layer of the Transformer architecture.

LoRA weights Wa, and Wb 

![LoRA weigts](https://github.com/user-attachments/assets/43037efe-ee7b-4472-b5c9-507d0a31dbd9)

QLoRA (Efficient Finetuning of Quantized LLMs)


4-bit NormalFloat Quantization: 

QLoRA introduces a novel quantization method that improves upon traditional quantile quantization.


Double Quantization: 

QLoRA takes a step further by quantizing the quantization constants, resulting in additional memory savings.


Paging with Unified Memory: 

Leveraging the NVIDIA Unified Memory feature, QLoRA orchestrates seamless page-to-page transfers between the CPU and GPU.

model = prepare_model_for_kbit_training(model)
peft_config = LoraConfig(
    r=8,
    lora_alpha=32,
    lora_dropout=0.1,
    target_modules=["q_proj", "v_proj"],
    bias="none",
    task_type="CAUSAL_LM",
)
model = get_peft_model(model, peft_config)

### compare trainable parameters #
peft_p = print_number_of_trainable_model_parameters(model)
print(f"# Trainable Parameter \nBefore: {ori_p} \nAfter: {peft_p} \nPercentage: {round(peft_p / ori_p * 100, 2)}")




