# Measuring the eccentricity of GW170817 and GW190425
**Amber K. Lenon<sup>1</sup>, Alexander H. Nitz<sup>2,3</sup>, Duncan A. Brown<sup>1,4</sup>**

 <sub>1. Department of Physics, Syracuse University, Syracuse, NY 13244, USA</sub>

 <sub>2. [Albert-Einstein-Institut, Max-Planck-Institut for Gravitationsphysik, D-30167 Hannover, Germany](http://www.aei.mpg.de/obs-rel-cos)</sub>  

 <sub>3. Leibniz Universitat Hannover, D-30167 Hannover, Germany</sub>  

 <sub>4. Kavli Institute for Theoretical Physics, University of California, Santa Barbara, CA 93106, USA</sub>

## Introduction ##

Two binary neutron star mergers, GW170817 and GW190425, have been detected by Advanced LIGO and Virgo. These signals were detected by matched-filter searches that assume the star's orbit has circularized by the time their gravitational-wave emission is observable. This suggests that their eccentricity is low, but a direct measurement of their eccentricity has not yet been made. We use gravitational-wave observations to measure the eccentricity of GW170817 and GW190425. We find that the eccentricity at a gravitational-wave frequency of 10 Hz is  $e \leq 0.024$ and $e \leq 0.048$ for GW170817 and GW190425, respectively (90\% confidence). This is consistent with the binaries being formed in the field, as such systems are expected to have circularized to $e \leq 10^{-4}$ by the time they reach the LIGO-Virgo band. Our constraint is a factor of two smaller that an estimate based on GW170817 being detected by searches that neglect eccentricity. We note that other techniques used to constrain binary neutron star eccentricity without full parameter estimation may miss degeneracies in the waveform, and that for future signals it will be important to perform full parameter estimation with accurate waveform templates.

We encourage use of these data in derivative works. If you use the material provided here, please cite the paper using the reference:

<!-- 
```
@article{,
      key            = "1770186",
      author         = "Lenon, Amber K. and Nitz, Alexander H. and Brown, Duncan A.",
      title          = "{Measuring the eccentricity of GW170817 and GW190425}",
      year           = "2020",
      eprint         = "1912.05464",
      archivePrefix  = "arXiv",
      primaryClass   = "astro-ph.HE",
      SLACcitation   = "%%CITATION = ARXIV:1912.05464;%%"
}
```
-->

## Analysis Details ##

The configuration files needed to create the analysis workflows are provided in the [configuration](https://github.com/gwastro/bns-eccentric-pe/tree/master/configuration) directory.

The posterior samples are in the `samples` group in the posterior data hdf files. There a variety of tools to access [hdf files](https://www.hdfgroup.org/) from numerous computing languages. Here we will focus on access through python and [h5py](www.h5py.org). files. These may be read in a python environment using an installation of h5py. For example,

```python
import h5py

fp = h5py.File('posterior-files/tf2_e_170817v2.hdf','r')

eccentricity = fp['samples/eccentricity'][:]
```

Provided parameters are:
 * `srcmass1`: The source-frame mass of the larger object, in solar masses.
 * `srcmass2`: The source-frame mass of the smaller object, in solar masses.
 * `chi_eff`: The effective spin of the binary.
 * `eccentricity`: The eccentricity of the binary 20Hz.
 * `e10`: The eccentricity of the binary at 10Hz.
 * `spin1z`: The z component of the first binary component's dimensionless spin.
 * `spin2z`: The z component of the second binary component's dimensionless spin.
 * `delta_tc`: The amount of time surrounding the coalescense time.
 * `ra`: The right ascension of the signal (in radians) (GW190425 only).
 * `dec`: The declination of the signal (in radians) (GW190425 only).
 * `distance`: The lumionsity distance to the signal (in Mpc) (GW170817 only).
 * `comoving_volume`: The comoving volume at the redshift of the signal.
 * `inclination`: The inclination of the binary's orbital angular momentum with
   respect to the line of sight, in radians. An inclination of 0 (pi)
   corresponds to a face-on (face-away) orientation.
 * `polarization`: The polarization angle of the gravitational wave.
 * `loglikelihood`: The natural log of the likelihood of each sample.
 * `logprior`: The natural log of the prior of each sample.
 * `logjacobian`: The natural log of the Jacobian between the parameter space and the sampling parameter-space that was used.

## License ##
![Creative Commons License](https://i.creativecommons.org/l/by-sa/3.0/us/88x31.png "Creative Commons License")

This work is licensed under a [Creative Commons Attribution-ShareAlike 3.0 United States License](http://creativecommons.org/licenses/by-sa/3.0/us/).

## Acknowledgments ##

We acknowledge the Max Planck Gesellschaft for support and the Atlas cluster computing team at AEI Hannover. This research was supported in part by the National Science Foundation under Grant No.~PHY-1748958. DAB thanks National Science Foundation Grant No.~PHY-1707954 for support. AL thanks National Science Foundation Grant No.~AST-1559694  for support. This research has made use of data, software and/or web tools obtained from the Gravitational Wave Open Science Center (https://www.gw-openscience.org), a service of LIGO Laboratory, the LIGO Scientific Collaboration and the Virgo Collaboration. LIGO is funded by the U.S. National Science Foundation. Virgo is funded by the French Centre National de Recherche Scientifique (CNRS), the Italian Istituto Nazionale della Fisica Nucleare (INFN) and the Dutch Nikhef, with contributions by Polish and Hungarian institutes.
