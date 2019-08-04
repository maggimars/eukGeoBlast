# Who are you and where do you come from?

How often do you find yourself wondering, "where in the world has this protist sequence been found before?" 

I do all the time. Most recently I wanted to know if sequences we found to be enriched in samples from hydrothermal vents near Okinawa had previously been found in other marine ecosystems and especially at other vent sites (read more: https://www.biorxiv.org/content/10.1101/714816v2). 

With about 40 sequences to look into, we set about blasting the sequences and manually looking at results and the publications linked to hits. It was painfully clear, however, that this approach was not sustainable, reproducible, or anywhere close to 'best practices'. 

Hence, the idea for this post was born. 

The Protist Ribosomal Reference (PR2) database (https://github.com/pr2database/pr2database) is already an amazing resource for those of us excited about protists. PR2 includes 176,813 protist ribosomal RNA gene sequences that can be downloaded for use in classifiying sequences denoised with DADA2 or processed with other software (https://github.com/pr2database/pr2database/releases). In addition, metadata for sequences in the database, including taxonomy, publications, and collection location, are available. The PR2 tutorial even gives an example of plotting sequence collection location on a map in R (https://github.com/pr2database/pr2database/blob/master/PR2_R_database.md). 

Excellent! Only ... a very small fraction of the sequences in the database have a latitude and longitude assigned to them. So, if you plot sequences by location, you only see a small subset of the available data. **18,459 of the 176,813 sequences in the database have a latitude and longitude assigned.**

There are other metadata fields that include location information, however. For example, `gb_country` holds, at the very least, the country of collection, and sometimes more detailed information. **71,230 sequences have a country assigned.** That is almost 4x more than the number of sequences with lat/lon. Furthermore, **82,468 have an isolation source provided.** This potentially provides location information for much more of the database, as not all entries with country have entries for isolation source and vice versa. 

But while the GenBank country column is standardized, researchers can really write whatever they want in the isolation source column. This makes the column valuable, since it often gives water depth and other descriptions of the sampling location, but it is difficult to extract the actual location information.   

**This post describes how to use ALL available location information in the PR2 database to make an interactive geographic map of Blast hits colored by % identity.** 

Fuzzy matching of isolation sources to locations with known lat/lon allows sequences without an assigned country or lat/lon to still be plotted by location. Interactive mapping allows zooming to look at metadata and %ID for individual Blast hits.    

https://maggimars.github.io/eukGeoBlast/eGB.html
