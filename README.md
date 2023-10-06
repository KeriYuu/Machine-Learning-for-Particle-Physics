# Exploring Beyond Standard Models (BSM) Using Machine Learning

## Project Description

This project aims to identify the Wilson coefficients within the Standard Model Effective Field Theory (SMEFT). The Lagrangian can be expressed as:

$$
\mathcal{L}_{BSM}=\mathcal{L}_{{SM}}+\sum_o \frac{f_o}{\Lambda^2} {O}_o\ .
$$

## Workflow

### Data Acquisition:

1. **Identify New Interactions**: Establish the Lagrangian form.
2. **Sample Parameter Points**: Define the approximation around the SM. Utilize MadGraph to produce particle-level metadata (four-momentum) for various Wilson coefficient combinations. (Note: MadGraph only runs in the SM; subsequent data from different parameter points are acquired through reweighting).
3. **Data Generation**: Use Pythia8 and Delphes for detector-level data creation.

### Machine Learning:

4. **Construct Features and Labels**: Detector data builds features, and particle-level data forms the target label.
5. **Neural Network Training**: Train the neural network.

### Testing:

6. **Predict and Output Likelihood**: The ML model provides the Likelihood Score from the test set features. (Done)
7. **Identify Wilson Coefficients**: Employ Maximum Likelihood to determine the new physics' Wilson coefficients. (To do)
8. **Assess Confidence Intervals**: Measure the confidence intervals.

## Dependencies

- **MadGraph**: 
  Check [MadGraph’s website](https://launchpad.net/mg5amcnlo) for setup details. Requires Fortran compiler and Python 3.7+.
  
- **Pythia8**: 
  ```bash
  $ ./bin/mg5_aMC
  > install pythia8
  ```

- **Delphes**: Requires [Root](https://root.cern/).
  ```bash
  $ ./bin/mg5_aMC
  > install Delphes
  ```

- **Madminer**: 
  ```bash
  pip install madminer
  ```
  Alternatively, use the library in this repository and run:
  ```bash
  pip install -r environment.yml
  ```

## Usage

Three sample Jupyter notebooks in the `examples` directory showcase the full workflow, focusing on the electron-positron collision process, leading to the production and decay of a top quark pair, emphasizing operators involving $Z$.

$$
O_{\phi Q}^{(3)}=(\phi^{\dagger} \tau^{I} i \overset{\leftrightarrow}{D}_{\mu} \phi) \bar{Q}_{L} \gamma^{\mu} \tau^{I} Q_{L}
$$

$$
O_{\phi u}=(\phi^{\dagger} i \overset{\leftrightarrow}{D}_{\mu} \phi) \bar{Q}_{L} \gamma^{\mu} u_{R}
$$

With the corresponding Lagrangian:

$$
\mathcal{L}_{BSM}=\mathcal{L}_{{SM}}+ \frac{C_{\phi Q}^{(3)}}{\Lambda^2} O_{\phi Q}^{(3)}+ \frac{C_{\phi u}}{\Lambda^2} O_{\phi u}
$$

## More To Do:
* Investigate various processes and interactions.
* Introduce new features (observables).
* Add background noise.
* Explore deep learning models (rethink probability modeling, alternate loss functions, different objective functions, and deep learning model tuning).

## License

This project is licensed under the MIT License.
