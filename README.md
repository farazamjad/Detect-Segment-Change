## Used Stabble diffusion to generate image from text. Grounding Dino is used to segment the object the user wants to change. Finally stable diffusion generates same image but with changes done to segmented part through text.

# Overview:
 The project aims to enable text-based image editing using Self-Attention Map (SAM) models and Stable Diffusion for inpainting. The codebase consists of three main files: func.py, main.py, and models.py. These files collectively implement a pipeline for processing images, predicting bounding boxes, and performing inpainting based on text prompts.


 
# Architectures and Libraries Used:

## Self-Attention Map (SAM):
o	SAM is a critical component for predicting masks and transforming bounding boxes. The model is loaded from a pre-trained checkpoint (sam_vit_h_4b8939.pth), which is downloaded using the models.py script. SAM utilizes the Vision Transformer (ViT) architecture for image understanding and feature extraction.
## Stable Diffusion:
o	Stable Diffusion is employed for inpainting, seamlessly blending the inpainted regions with the existing image. The pipeline is loaded from a pre-trained model (stable-diffusion-2-inpainting) using the main.py script. The architecture and details of the Stable Diffusion model are encapsulated within the diffusers library.
## Grounding DINO:
o	Grounding DINO is utilized for predicting bounding boxes, logits, and phrases related to objects in the image. The model is loaded from a configuration file (GroundingDINO_SwinT_OGC.py) and weights (groundingdino_swint_ogc.pth). This process is handled by the main.py script.

# Code Structure:
##	func.py:
o	This file contains utility functions for image processing and visualization. Functions like show_mask, transform_boxes, and save_image are defined to facilitate the overlay of masks, box transformations, and image saving, respectively.
##	main.py:
o	The central script orchestrates the entire image editing process. It begins by importing necessary libraries, models, and functions from func.py. Key steps include:
	Loading SAM, Stable Diffusion, and Grounding DINO models.
	Defining an edit_image function to process input images based on specified parameters.
	Parsing command-line arguments to customize image editing.
	Calling the edit_image function to generate edited images.
##	models.py:
o	This file manages the downloading of essential model weights required for SAM and Grounding DINO. The download_file function fetches the models from their respective URLs, ensuring they are available for use in the project.
# Workflow:
•	Object Recognition:
o	Grounding DINO predicts bounding boxes, logits, and phrases related to objects in the input image based on user-specified thresholds.
•	Mask Prediction and Transformation:
o	SAM is employed to predict masks corresponding to the recognized objects. The bounding boxes are transformed using SAM, ensuring accurate alignment with the input image.
•	Image Annotation:
o	The predicted masks are overlaid on the annotated image, providing a visual representation of the recognized objects and their corresponding masks.
•	Inpainting:
o	The Stable Diffusion model takes the annotated image, text prompt, and masks as input to perform inpainting. This process seamlessly integrates user-specified edits into the image.
Conclusion: The project successfully combines the capabilities of SAM, Stable Diffusion, and Grounding DINO to provide a comprehensive text-to-image editing pipeline. The use of pre-trained models and modular code design allows for efficient and customizable image processing. The project's flexibility is demonstrated through the command-line interface, enabling users to experiment with different input parameters and achieve diverse image edits.
![image](https://github.com/farazamjad/Detect-Segment-Change/assets/81928514/9fd36f82-2311-42b4-b447-2f53e6b4899a)


# Results

# Image generated using stable diffusion

<img width="537" alt="Screenshot 2023-12-06 at 12 24 42 PM" src="https://github.com/farazamjad/Detect-Segment-Change/assets/81928514/c115f4c3-f4fc-46c4-a78d-837c336dd511">

<img width="524" alt="Screenshot 2023-12-06 at 12 24 56 PM" src="https://github.com/farazamjad/Detect-Segment-Change/assets/81928514/39a35f36-aad4-4a53-8e42-67eb8b8f4327">
