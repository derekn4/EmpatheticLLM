<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->


<!-- PROJECT LOGO -->
<br />
<div align="center">
  <!--<a href="https://github.com/derekn4/CurfewBot?tab=readme-ov-file">
    <img src="curfew.png" alt="Logo" width="300" height="300">
  </a>-->

<h3 align="center">Virtual Empathy: The Illusion of Conscientiousness in Conversational LMs</h3>

  <p align="center">
    Training a GPT2 model with conversational data to demonstrate empathetic dialogues.
    <br />
    <a href="https://github.com/derekn4/CurfewBot"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/derekn4/CurfewBot">View Demo</a>
    ·
    <a href="https://github.com/derekn4/CurfewBot/issues">Report Bug</a>
    ·
    <a href="https://github.com/derekn4/CurfewBot/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
        <li><a href="#libaries-used">Libraries Used</a></li>
      </ul>
    </li>
    <li>
      <a href="#how-it-works">How it Works</a>
      <ul>
        <li><a href="#data-processing">Data Processing</a></li>
        <li><a href="#args-class">Args Class</a></li>
        <li><a href="#conv-class">ConversationDataset Class</a></li>
        <li><a href="#train">Train Function</a></li>
        <li><a href="#evalute">Evaluate Function</a></li>
      </ul>
    </li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

Dataset Curation using Few-shot learning for Empathetic Conversational Agents.
In this project, we aimed to build a conversational agent for mental health applications that is more “human-like” in its  approach and has the following characteristics:
- Is empathetic 
- Has a sense of morality 
- Is self-aware (Knows when to not respond)
- Doesn’t generate triggering responses

Specifically, we graded the final model on these categories through Human Evaluations:
- Natural Flow
- Context Dependence
- Topic Consistency
- Speaker Consistency
- Specificity
- Interestingness

Our primary objective is to develop an empathetic conversational agent that is specifically tailored for self-care and emotional support settings.


<p align="right">(<a href="#readme-top">back to top</a>)</p>



### Built With

* [![Python][Python.org]][Python-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Libraries Used
* HuggingFace
* Transformers
* Pytorch
* Pandas
* Sklearn
* numpy

<p align="right">(<a href="#readme-top">back to top</a>)</p>


## How it Works
Install all necessary libraries to run DialoGPT.ipynb

### Data Processing
- Dataset is pulled from local storage "FB_Multi_Train.csv"
- Preprocessing of Data required

### Args Class
- With the Transformers Library, the Args() class initializes the model and hyperparameters in a class for later args for training
- Data is loaded and split into train and test sets


### ConversationDataset Class
- The ConversationDataset class takes tokenizer, args, a dataframe, and block size as parameters
- This class helps generate the conversations and tensors

### Train Function
- This function is responsible for training the model.
- Initializes a TensorBoard writer for logging
- Sets up training batch size and collation function for the DataLoader
- Calculates total number of optimization steps based on the number of training examples, gradient accumulation steps, and number of epochs.
- Initializes optimizer and scheduler for learning rate scheduling
  - loads optimizer and scheduler states if they already exist
- Initializes mixed precision training if "args.fp16" is enabled.
- Sets up multi-GPU and distributed training if multiple GPUs are available.
- Iterates through epochs and batches, calculates loss, performs backpropagation, and updates model parameters.
- Logs training progress, evaluates the model periodically, and saves checkpoints.
- Manages the maximum number of steps for training.
- Closes the TensorBoard writer.

### Evalute Function
- This function evaluates the model performance on a validation dataset.
- Sets up the evaluation batch size and collation function for the DataLoader.
- Initializes a DataLoader for the evaluation dataset.
- Performs evaluation by iterating through batches, calculating loss, and accumulating evaluation metrics.
- Computes the perplexity metric based on the evaluation loss.
- Logs evaluation results and writes them to an output file.
- Returns the evaluation results as a dictionary.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Derek Nguyen 
- [LinkedIn](https://www.linkedin.com/in/derekhuynguyen/) 
- [Email](derek.nguyen99@gmail.com)
<br></br>
Project Link: [https://github.com/derekn4/EmpatheticLLM](https://github.com/derekn4/EmpatheticLLM)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[Python.org]: https://www.python.org/static/img/python-logo.png
[Python-url]: https://www.python.org/about/website/