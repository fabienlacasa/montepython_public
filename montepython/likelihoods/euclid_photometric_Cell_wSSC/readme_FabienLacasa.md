## 2024-09-11 Fabien Lacasa
This is a C(l) based likelihood for Euclid 3x2pt (lensing, photometric galaxy clustering and cross-correlation). It is based on a likelihood that already exists in montepython_public : euclid_photometric_alm.

The goal here is to build a C(l) lieklihood that further incorporates the effect of Super-Sample Covariance (SSC) using PySSC (https://pyssc.readthedocs.io/en/latest/). Here we use PySSC v3.1.

There are three ways that we aim to implement SSC:
- traditional way: add a new covariance term: Cov_total = Cov_Gaussian + Cov_SSC
- using https://arxiv.org/abs/2209.14421 : add an extra term directly at the level of the likelihood computation
- add new nuisance parameters with priors dictated by PySSC (see Appendix E of https://arxiv.org/pdf/1809.05437, and https://arxiv.org/abs/2209.14421)