---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: The Reduced
permalink: /RRISA_reduced/
---

<h1>Reduced Data Products</h1>
All of the existing IGRINS data has been hand reduced using the [(IGRINS plp)](https://github.com/igrins/plp).
The Reduced version of RRISA includes different names for targets than the Raw component.
These are names that have been painstakingly corrected by manually searching through the IGRINS paper logs for handwritten coordinates and names, through SIMBAD for nomenclature corrections and coordinate offsets.
Targets that are subcomponents of systems or extended sources keep their identifier, and if not SIMBAD searchable, do not have any additional information added in the XMatch component of RRISA.
The original names for all of the targets remain for reference to the Raw component.
If users find anything that appears to be a misidentification we ask that they report it by raising a GitHub issue.

<h3>Data Reduction</h3>
IGRINS reduced data have been processed with the [IGRINS Pipeline Package (PLP)](https://github.com/igrins/plp) see [Lee+ 2017](https://zenodo.org/record/845059#.Yolg-C-cawA).

The PLP optimally extracts 1D spectra, telluric corrects, and provides 2D rectified spectra for post-processing.  
Wavelength solutions are determined using OH emission lines, and are then refined using telluric absorption lines in the telluric standard.
Telluric standards were generally A0V stars, which are Vega corrected using a [model of the Vega spectrum](http://kurucz.harvard.edu/stars.html.) ([see the file in the PLP](https://github.com/igrins/plp/blob/master/master_calib/A0V/vegallpr25.50000resam5.npy)).

The PLP outputs several files for each reduction:
1. **spec_A0v.fits:** The A0 flattened and Vega flux corrected target spectra. This fits files includes the original data used to create the reduced spectrum. Each extension is a 2048x28 array with the same header (except for the PRIMARY extension) other than the EXTNAME. The following details the differences between each of the EXTNAMEs:
  - _[0]-Primary:_ The corrected target spectrum = (TGT_SPEC/A0V_SPEC)*VEGA_SPEC
  - _[1]-Wavelength:_ The wavelength solution - in um (so 1.42um for instance)
  - _[2]-TGT_SPEC:_ The extracted target spectrum (from the target spec.fits file)
  - _[3]-A0V_SPEC:_ The extracted A0V spectrum (from the A0V spec.fits file)
  - _[4]-VEGA_SPEC:_ A model of the Vega spectrum ([see the file in the PLP](https://github.com/igrins/plp/blob/master/master_calib/A0V/vegallpr25.50000resam5.npy) or for more detailed info regarding the file see this [link](http://kurucz.harvard.edu/stars.html)).
2. **sn.fits** (for both target and A0): Signal-to-Noise per pixel matching to the spec.fits output.
3. **variance.fits** (for both target and A0): Variance per pixel matching spec.fits output.
4. **spec.fits** (for both target and A0): The source spectrum. It says the spectral unit is ADUs.
5. **spec_flattened.fits** (A0): The flattened A0 spectrum.
6. **spec2d.fits** (for both target and A0): the two dimension spectrum
7. **var2d.fits** (for both target and A0): the two dimensional variance
8. **wave.fits** (for both target and A0): The vacuum wavelength solution for a given source, in nm (so 1429nm for instance).

__*Note:*__ _The output files from the IGRINS PLP are an in vacuum wavelength solution. Fit models are offset from expected line positions by 80-120 km/s the models are likely in air and not vacuum. The IAU standard conversion for air to vacuum wavelengths is given by [Morton 1991](https://ui.adsabs.harvard.edu/abs/1991ApJS...77..119M/abstract). For vacuum wavelengths (VAC) in Angstroms and convert to air wavelength (AIR) via:_
<center>
<em>AIR = VAC / (1.0 + 2.735182E-4 + (131.4182 / VAC^2) + (2.76249E8 / VAC^4))</em>
</center>

<h3>RRISA Reduced</h3>
Downloadable from [our GitHub](https://github.com/IGRINScontact/RRISA.git) as a .csv or .xls or see the spreadsheet embedded below for quick ctr+f/cmd+f searching.

For a more detailed description of the Reduced RRISA header, check out the readme_reduced.md in [our GitHub](https://github.com/IGRINScontact/RRISA.git).

this is a test spreadsheet, not the actual one that will go here
<iframe title="A test RRISA google sheet insert" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRtfBHWcplfpXJvxq2-PVoxkubwwTuQQtsvdTuTTdPxxWFpJKp3MPzPNhH0Eur87F8nytKgOLKwbyY6/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false" height="100%" width="100%"></iframe>
