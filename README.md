# brain_tumor_classification_dlmi_2020
Classification of Brain Tumors from MRI Images Using a Capsule Classifier and Image Synthesis.

Tel Aviv University. DLMI course (0553-5542).  July 2020.

# Abstract
The biggest problem for classifying magnetic resonance images (MRI) with deep learning techniques lies in the number of labelled data. 
Although recent works in the field of neural network have shown promising abilities of classifying brain tumors from brain MRI images, 
they used very deep and complex network architectures. 
Simpler network architecture requires fewer resources, and enable to use real time applications on mobile platforms. 
To this end, we introduce a new deep learning method to classify brain tumor of three tumor types. 
Our solution combines synthesise of additional data using a conditional generative model, with a new convolutional capsule architecture for the classification.

We evaluated the performance both qualitatively and quantitatively. 
Qualitatively, the conditional GAN was capable at synthesising images of different appearance, for the same underlying skull geometry. 
Moreover,  the features learned by the conditional GAN are often semantically meaningful groups, covering structures such as skull and tumor. 
The classificaiton performance was evaluated quantitatively using accuracy and F1 measures. 
The best results of 93\% accuracy and F1 score of 92\%, were obtained when the classifier pre-trained 
on 7,000 synthesised images and then trained on the original data using a 7-fold cross-validation. 
Our method performs as well as the Resnet50 state-of-the-art deep network, with 9x less parameters.

# Dataset
For all our experiments, we used the 'Brain Tumor' dataset, proposed by Cheng Jun et al.

The dataset can be found in this link: https://figshare.com/articles/brain_tumor_dataset/1512427

# How to run the code:

First you have to use the generative model to create train& test dataset pickle files.

Our modified pix2pix model creates syntethic data in addition to the original data. 

The code and instruction are given in the generative_model folder.

Finally you can use the classification models (Resnet50/ Our capsule classifier) as described in the capsule classifier folder.

## Capsule classifier:

### Pickle
Get the pickle file of the dataset:

Each element of the pickle is build from 2 fields:
  Image (size of 512x512) and a label (0-2).
  
The elements are append into numpy array and than save into pickle file.
You have to save a pickle of the traninig and the testing data.

### Flags
Change the following variables:

        Train - binary flag
        Test - binary flag
        Crossvalidation - binary flag
        LoadSavedModel - binary flag if you want to load pretrained model
        FreezeLayer - for the Resnet50 - binary flag.
        Model - "resnet" or "capsule"
        epochs - number of epochs
        model_dir - The folder you want to save the model to
        data_path - A path to the pkl file of the traninig data
        data_test_path - A path to the pkl of the test data
        
 Keep the other variables for the original value

### Training/ Testing
Run the script train.py.

### t-SNE
Run the script tsne.py after you have a trained model.
