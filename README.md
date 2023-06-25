# AI for Particle Physics: Exploring Beyond Standard Models (BSM) Using Machine Learning

## Project Description

This project aims to use machine learning to explore new physics beyond the Standard Model (SM) with the Standard Model Effective Field Theory (SMEFT). Specifically, we seek to determine the Wilson coefficients in the Lagrangian of the Beyond Standard Model (BSM) physics. The Lagrangian representation can be given as:

$$
\mathcal{L}_{BSM}=\mathcal{L}_{{SM}}+\sum_o \frac{f_o}{\Lambda^2} {O}_o\ .
$$

## Workflow

### Data Acquisition:

1. **Identify new interactions**: Determine the form of the Lagrangian.
2. **Sampling parameter points**: Combinations of Wilson coefficients are sampled, and MadGraph is run to generate the corresponding particle-level metadata (four-momentum) for different Wilson coefficient combinations.
3. **Data generation**: Pythia8 and Delphes are utilized to generate detector-level data.

### Machine Learning:

4. **Feature and Label Construction**: We use detector data to construct features and particle-level data to construct the target label, Likelihood Score.
5. **Neural Network Training**: Train the neural network model.

### Testing:

6. **Predict and Recover Likelihood**: Given the features of the test set, the machine learning model outputs the Likelihood Score and recovers the Likelihood.
7. **Determine Wilson Coefficients**: Use Maximum Likelihood to obtain the Wilson coefficients of the new physics.
8. **Confidence Interval Assessment**: Evaluate the confidence intervals.

## Dependencies

- MadGraph
  See [MadGraph’s website](https://launchpad.net/mg5amcnlo) for installation instructions (need a Fortran compiler as well as Python 3.7+).
- Pythia8
  `$ ./bin/mg5_aMC` 
  `> install pythia8`
- Delphes (need [Root](https://root.cern/))
  `$ ./bin/mg5_aMC` 
  `> install Delphes`
- Madminer
  `pip install maminer`
  or
  use lib in this repo, and ` pip install -r environment.yml`

Please ensure that you have installed all dependencies before running the scripts.

## Usage

This project is accompanied by three example Jupyter notebooks in the `examples` directory, which demonstrate the complete workflow for a specific case study: the process of electron-positron collision leading to the generation and decay of a top quark pair, focusing on operators involving $Z$:

$$
O_{\phi Q}^{(3)}=(\phi^{\dagger} \tau^{I} i \overleftrightarrow{D}_{\mu} \phi) \bar{Q}_{L} \gamma^{\mu} \tau^{I} Q_{L}
$$
$$
O_{\phi u}=(\phi^{\dagger} i \overleftrightarrow{D}_{\mu} \phi) \bar{Q}_{L} \gamma^{\mu} u_{R}
$$

And their corresponding Lagrangian:

$$
\mathcal{L}_{BSM}=\mathcal{L}_{{SM}}+ \frac{C_{\phi Q}^{(3)}}{\Lambda^2} O_{\phi Q}^{(3)}+ \frac{C_{\phi u}}{\Lambda^2} O_{\phi u}
$$

These notebooks demonstrate each step of the process, from data acquisition, through machine learning, to testing. You can follow along these examples to understand how the pipeline works and use it for your own case studies. Here is a guide on how to use them:

1. **Data Acquisition Notebook**: This notebook shows how to identify the interactions and parameters of interest, run MadGraph to generate corresponding particle-level metadata, and how to use Pythia8 and Delphes for data generation. You'll be able to inspect the generated data and understand the features that have been extracted for machine learning.
2. **Machine Learning Notebook**: This notebook provides a step-by-step guide on constructing features and labels using the detector data and particle-level data, and how to train the neural network model. It guides you through the training process, including setting up the model, choosing a loss function and optimizer, and training the model.
3. **Evaluation Notebook**: This notebook demonstrates how to use the trained model to predict the Likelihood Score, recover the Likelihood, determine the Wilson coefficients using Maximum Likelihood, and assess the confidence intervals. It also provides visualizations and assessments of the results.

To run these notebooks, make sure that you have Jupyter installed and navigate to the `examples` directory. Then run `jupyter notebook` in your terminal, and select the notebook you want to open in the Jupyter interface that opens in your browser.

## Contributing

This project is open-source and contributions are welcome. If you're interested in improving this project or adding new features, please feel free to fork the repository, make your changes, and create a pull request.

## License

This project is licensed under the MIT License.
