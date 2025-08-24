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


<img width="483" height="278" alt="Screenshot from 2025-08-24 11-22-32" src="https://github.com/user-attachments/assets/6502fb34-3d4f-45b4-a0ba-b112af01da6d" />

r  determines the rank of the update matrices, also known as Lora attention dimension. Lower rank results in smaller update matrices with fewer trainable parameters.

lora_alpha controls the LoRA scaling factor

target_modules is a list of module names, such as “q_proj” and “v_proj,” which serves as the targets for the LoRA model. The specific module names may vary depending on the underlying model.

bias: Specifies if the bias parameters should be trained. Can be 'none', 'all' or 'lora_only'.


<img width="1192" height="437" alt="Screenshot from 2025-08-24 11-25-19" src="https://github.com/user-attachments/assets/8d55936f-ff50-403f-8450-fe8f7c2f6a82" />


<img width="746" height="437" alt="Screenshot from 2025-08-24 11-26-09" src="https://github.com/user-attachments/assets/1162c748-6038-4124-9f49-ab1d74179cc8" />


<img width="745" height="553" alt="Screenshot from 2025-08-24 11-27-40" src="https://github.com/user-attachments/assets/9b7b18ce-bb3d-4ae0-ab4f-b55d728a18ce" />


Generation 

After several hours of training with a single GPU, it’s time to test the model’s performance using the input prompt “Write me a poem about Singapore” which we previously used. The code snippet starts by loading the pre-trained Llama-2–7b-hf model and Peft weights. The model’s generation configuration is set to control factors such as

temperature controls the randomness of the generation process. When the temperature is high, the generator is more random and generates diverse but less coherent outputs

top-p select the most promising candidates from a set of generated options. The “p” in top-p stands for “probability,” and it refers to the probability of a given candidate being the best option

top-k is similar to top-p, but instead of selecting a percentage of candidates, it selects a fixed number of candidates with the highest probability scores

num_beam in Beam search algorithm that allows the model to consider multiple possible outputs simultaneously


Conclusion


Combining the prowess of LLama 2.0 with the efficiency of Qlora opens the doors to unparalleled AI personalization. The ability to fine-tune models dataset, powered by state-of-the-art open-source models, brings AI applications to new heights of relevance and customization. Qlora’s resource-efficient approach democratizes fine-tuning, enabling seamless training







