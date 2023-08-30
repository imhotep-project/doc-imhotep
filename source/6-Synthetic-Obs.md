# 6. Synthetic observations

## 6.1 Synthetic along-track altimetry

The model SSH from the NEMO-based IMHOTEP simulations is equivalent to the “ADT”
variable on the scheme Fig. 6.1 below:

* In the model, the ocean at rest would be following the geoid (the
iso-gravity surface). And in the model, the gravity is taken constant
(9.80665 m/s2) over the globe , which is itself considered a perfect sphere
(Rt=6371229 m ).

* In the model in practice it is the SSH gradient which is used in the
computation of the horizontal surface pressure. And so SSH is known to
within a constant.

* Note also that the model does not see the atmospheric surface pressure
(set to constant). The atmospheric surface pressure is only taken into
account by the model in the surface flux computation (bulk formulation)

![SSH scheme](./img/SSHscheme.png)
_Fig.6.1 Altimetry vocabulary_.
