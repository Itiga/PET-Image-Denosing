<h2 align="center"><a href="https://link.springer.com/article/10.1007/s00259-025-07122-4">Robust Whole-body PET Image Denoising Using 3D Diffusion Models: Evaluation Across Various Scanners, Tracers, and Dose Levels</a></h2>

## Purpose

Whole-body PET imaging plays an essential role in cancer diagnosis and treatment but suffers from low image quality. Traditional deep learning-based denoising methods work well for a specific acquisition but are less effective in handling diverse PET protocols. In this study, we proposed and validated a 3D Denoising Diffusion Probabilistic Model (3D DDPM) as a robust and universal solution for whole-body PET image denoising. 

## Method

The proposed 3D DDPM gradually injected noise into the images during the forward diffusion phase, allowing the model to learn to reconstruct the clean data during the reverse diffusion process. A 3D convolutional network was trained using high-quality data from the Biograph Vision Quadra PET/CT scanner to generate the score function, enabling the model to capture accurate PET distribution information extracted from the total-body datasets. The trained 3D DDPM was evaluated on datasets from four scanners, four tracer types, and six dose levels representing a broad spectrum of clinical scenarios.

## Result

The proposed 3D DDPM consistently outperformed 2D DDPM, 3D UNet, and 3D GAN, demonstrating its superior denoising performance across all tested conditions. Additionally, the model’s uncertainty maps exhibited lower variance, reflecting its higher confidence in its outputs.  

## Testing

### Data Preparation

Before running the denoising script, modify the `load_data_for_worker` function in `./scripts/test.py` to align with your data format and dimensions. This function is responsible for loading your low-dose PET data into the model.

### Running the Denoising Script

We provide a shell script `test_DDPM_3d_mpi.sh` to facilitate the testing process.

#### Usage

- `--base_samples`: Path to the `.npz` files containing your low-dose PET images.
- `--num_samples`: Total number of samples you wish to process.
- `-n`: Number of GPUs to utilize for parallel processing.
- `--save_dir`: Path to the directory where you want to save the denoised images.

## License

- The **code** in this repository is licensed under the **MIT License**.
- The **model weights** are licensed under **CC BY-NC-SA 4.0**, meaning:
  - You **can** share and modify the model weights, but **must** use the same license.
  - You **cannot** use it for **commercial purposes**.

For details, check:
- [LICENSE](./LICENSE.txt) (MIT for code)
- [MODEL_LICENSE](./MODEL_LICENSE.txt) (CC BY-NC-SA 4.0 for model weights)

