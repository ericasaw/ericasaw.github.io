---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: The XMatch
permalink: /RRISA_xmatch/
---

<h1>Reduced & Crossmatched</h1>
For objects in the IGRINS sample that are searchable via SIMBAD, we can crossmatch with other catalogs to provide additional information.
In the beta version of RRISA we support crossmatching with [2MASS](https://ui.adsabs.harvard.edu/abs/2003yCat.2246....0C/abstract), [APOGEE](https://ui.adsabs.harvard.edu/abs/2020AJ....160..120J/abstract), [Gaia EDR3](https://ui.adsabs.harvard.edu/abs/2020yCat.1350....0G/abstract), [Gaia DR2](https://ui.adsabs.harvard.edu/abs/2018A%26A...616A...1G/abstract), and [PASTEL](https://ui.adsabs.harvard.edu/abs/2016A%26A...591A.118S/abstract).


<h3>Object Matching</h3>
The crossmatching for RRISA errs on the side of caution in an effort to reduce misidentification of objects.
Crossmatching is possible through [xMatch Queries](https://astroquery.readthedocs.io/en/latest/xmatch/xmatch.html) via [astroquery](https://astroquery.readthedocs.io/en/latest/index.html) and is undertaken through the following:
- Using xMatch Queries to find objects in the corresponding catalog within 1 arcsec of the object's SIMBAD coordinates
- With the identifiers returned from the above step, query SIMBAD
- Compare the names of the objects from the two queries and remove catalog results for objects without matching names.

The flag column for each catalog will either have a value of 0 or 1.
A flag of 1 means that the identifier returned from the xMatch Query is not SIMBAD searchable.
In this case the objects could match, but we suggest that the user manually check to confirm.

<h3>Additional Columns</h3>
In addition to the IGRINS information we add the following from each catalog:

- SIMBAD
  - the primary ID
  - all of the IDs for the object
  - SIMBAD object type
  - spectral type
  - spectral type quality A-->E (best-->worst)
  - propermotion RA
  - propermotion DEC
  - radial velocity
  - parallax
  - U, B, V, R, G, I, J, H, K magnitudes
  - Teff
  - logg
  - [Fe/H]
- 2MASS
  - 2MASS identifier
  - J, H, K magnitudes
- Gaia EDR3
  - Gaia EDR3 identifier
  - parallax
  - G_bp - G_rp
  - G_bp - G_rp excess factor
  - G magnitude
- Gaia DR2
  - Gaia DR2 identifier
  - proper motion RA
  - proper motion DEC
  - G_bp - G_rp
  - G_bp - G_rp excess factor
  - G magnitude
  - radial velocity
  - Teff
  - estimate of extinction in the G band from Apsis-Priam
  - radius
  - luminosity
- APOGEE
  - radial velocity
  - Teff
  - logg
  - vsini
  - [M/H]
  - [alpha/H]
  - [Fe/H]
- PASTEL
  - Teff
  - logg
  - [Fe/H]

For a more detailed description of the XMatch RRISA header, check out the readme_xmatch.md in [our GitHub](https://github.com/IGRINScontact/RRISA.git).

<h3>RRISA XMatch</h3>

Downloadable from [our GitHub](https://github.com/IGRINScontact/RRISA.git) as a .csv or .xls or see the spreadsheet embedded below for quick ctr+f/cmd+f searching.

For a more detailed description of the XMatch RRISA header, check out the readme_xmatch.md in [our GitHub](https://github.com/IGRINScontact/RRISA.git).

this is a test spreadsheet not the actual spreadsheet that will go here
<iframe title="A test RRISA google sheet insert" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRtfBHWcplfpXJvxq2-PVoxkubwwTuQQtsvdTuTTdPxxWFpJKp3MPzPNhH0Eur87F8nytKgOLKwbyY6/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false" height="100%" width="100%"></iframe>
