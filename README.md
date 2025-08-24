# Fine-Tuning-Llama-2.0
Fine-Tuning my own Language Model


![Fine-Tuning_Llama_2 0](https://github.com/user-attachments/assets/72e1945b-d40c-4564-9655-920b7cc8f18b)


Parameter-Efficient Fine Tuning (PEFT) : QLoRA

fine-tuning a model with 65 billion parameters necessitates a staggering 780 GB of GPU memory, equivalent to ten A100 80 GB GPUs. Such resource demands have hindered the seamless fine-tuning of consumer hardware.

LoRA: Low-Rank Adaptation of Large Language Models

LoRA’s architecture involves freezing the pre-trained model weights and training the additional weight changes in a matrix without sacrificing crucial information. This process occurs in each layer of the Transformer architecture.



![LoRA weigts](https://github.com/user-attachments/assets/43037efe-ee7b-4472-b5c9-507d0a31dbd9)
