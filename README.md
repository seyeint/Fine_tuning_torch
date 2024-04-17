# Fine tuning with torch

![image](https://github.com/seyeint/Fine_tuning_torch/assets/36778187/a0430c2e-aa0b-4754-909e-3d8ad37b2349)


## Quick context on LoRA, regardless of the framework one is working in:

**Rank (R)**: Measure of "dimensionality" of the space a transformation - weight matrix - can span. The max rank is always the min(#rows, #columns)... why? because that's the max rank possible when assuming all rows and columns are linearly independent.
Higher rank means more parameters to learn, more memory, more energy spent on concept/semantic space.

**Low (Lo)**: One wants to approximate a subset of these weight matrices (x layers) with lower rank matrices (check SVD or other factorization methods). The rest of the network has its weights frozen during the backward pass.

**Adaptation (A)**: One adapts the pre-trained model to a more specific task/objective, capturing important relationships from this new environment, comparatively to the innitial general model training.

**LoRA**: One fine-tunes a large network not simply by freezing some weights and re-training on specific data, but actually reducing the computational cost by performing and working with low rank approximation matrices.
After fine-tuning, one cool thing is that our model is due to having less parameters, given that we don't go back to the original layer dimensions - less memory, faster inference, less energy spent.
