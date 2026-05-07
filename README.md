# Sparse Autoencoders for EM

## Research Question

Do safety-relevant SAE features change before, during, or after the behavioral phase transition?


## Work
All checkpoints for seeds 0, 1, and 2 are saved on bad financial advice dataset. Evals ran on seed 0, and it shows strong misalignment. 
EM model: Qwen-2.5-7b-Instruct; Eval model: Gemini-2.5-Flash

The figures show that EM related features rise sharply with the onset of EM.

---

## Definitions


- **LoRA** A fine-tuning technique that freezes the original model weights and trains a small pair of low-rank matrices whose product is added to selected weight matrices, much cheaper than full fine-tuning but still effective.
- **Emergent misalignment (EM):** The phenomenon where narrow fine-tuning (e.g., teaching the model to give bad medical advice) causes the model to become misaligned on *unrelated* prompts i.e. endorsing harmful views, describing itself as deceptive, etc. - Betley et al. 2025.
- **Phase transition:** A training dynamic where a model's behavior changes abruptly over a narrow range of training steps rather than smoothly. Turner et al. observed this for EM: the LoRA-learned direction rotates sharply around training step ~180–600.
- **Activations:** The intermediate vectors a transformer produces internally at each layer as it processes an input. Not the weights — the *moment-to-moment* internal state while 
- **Sparse autoencoder (SAE):** A small neural network trained to reconstruct a model's activations using a very wide, sparsely-activating hidden layer. Each hidden unit is called a **feature** and typically corresponds to a human-interpretable concept (e.g., "refusal," "code," "deceptive assistant").