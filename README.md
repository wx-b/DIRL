# DIRL: Domain-Invariant Representation Learning

Domain-Invariant Representation Learning (DIRL) is a novel algorithm that semantically aligns both the marginal and the conditional distributions across source and target enviroments. For more details, please visit: [https://www.sites.google.com/view/dirl](https://www.sites.google.com/view/dirl)

<p align="middle">
  <img src="./docs/sim_dirl.gif" width="303" height="224"/>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="./docs/arrow_dirl.png" width="60" height="100"/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
  <img src="./docs/real_dirl.gif" width="360" height="224"/>
</p>
 
![dann_conceptual](./docs/all_gifs_dirl_labeled.gif)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[[Source Only](./docs/source_only.gif)]&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[[Marginal Alignment Cross-Label Mismatch](./docs/dann_negative_transfer.gif)]&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[[Marginal Alignment Label Shift](./docs/dann_label_shift.gif)]&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[[DIRL](./docs/dirl_ma_ca_triplet.gif)]

## Getting Started
Follow the instructions to get started after cloning the repository (tested with python3):

```
virtualenv --python=/usr/bin/python3 env_dirl
source env_dirl/bin/activate

pip install -r requirements.txt
python setup.py develop
```

## Examples

Below we provide a couple of examples to illustrate the efficiency of the DIRL algorithm in learning invariant feature representations with unseen out of training distribution target environments. Customize your results by adjusting the settings and hyperparameters in the respective config files in the `configs` folder.
 
### 2D Synthetic Domain

```
CUDA_VISIBLE_DEVICES=0 python src/train_synthetic_2d.py -mode dirl -num_target_labels 4 
```

Results are saved in the `results` folder with respective `.yml` config, `results/figs` and `results/animations` folder.

Vary the number of target examples `num_target_examples` and `-mode` among `[source_only, dann, triplet, dirl]`  to analyse  the performance of the algorithm.

### Digits Bechmarks 

First, download the digits datasets (required only once) in the `resources` folder by executing the script: `python src/download_digits_datasets.py`
```
CUDA_VISIBLE_DEVICES=1 python src/train_digits.py -mode dirl -source mnist -target mnistm -num_target_labels 10 -save_results True
```
Results are saved in `results` folder with the respective `.yml` config.

Vary the `-source` and `-target` options among `[mnist, mnistm, svhn, usps]`. 

`-mode` and `-num_target_labels` can be changed similarly as above.


## Cite DIRL

```bibtex
@inproceedings{Tanwani_DIRL_CORL_20,
    title={Domain Invariant Representation Learning for Sim-to-Real Transfer},
    author={Ajay Kumar Tanwani},
    booktitle={Proceedings of the 4th Conference on Robot Learning},
    year={2020}
}
```

