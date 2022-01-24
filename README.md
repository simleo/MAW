# Whole Metabolome Annotation and Suspect List of _Skeletonema costatum_

## Suspect List Curation
Initial Suspect List contained compounds from KEGG, PubChem, MetaCyc, and BRENDAenzyme, LOTUS, CMNPD and Literature. The metadata included names, molecular formula, Species names, SMILES, InChI, Monoisotopic mass, different database IDs, and Sources/ References. For the curation, the structural information from each entry is validated using ```RdKit``` and additional metadata is added via ```pubchempy```. 

First, entries with chemical structure notation such as SMILES were checked for the correct metadata using ```pubchempy```. The additional metadata added includes: IUPAC names, and syonyms. Another column indicates what curation has been done for each entry. This initial step resulted in three types of entries, one with correct metadata and names, second with incorrect name and metadata, and third for which ```pubchempy``` returns error. The second type of entries were replaced with correct names and metdata. To handle the third type, the isomeric smiles were converted to canonical smiles uisng ```RdKit``` and then the metadata was added, but some entries had wrong or non-standardized SMILES syntax which caused the error for ```pubchempy```. Data with wrong SMILES syntax were discarded. Some correct syntax SMILES had no record in PubChem. Such SMILES were kekulized and checked in PubChem with metadata.

For entries with names and other metadata but no structure notation, the names were searched in PubChem for isomeric SMILES and other missing metadata. Some enteries had non-conventional names such as Disccharide or 18:1 fatty alcohol. The names were manually checked and changed to conventional names of the compound. for others such as 18:1 fatty alochol, there was not much information to find the right name or strcuture. Such entries were also discarded. For some earlier entries with wrong or non-standardized SMILES syntax, the names were used to extract compounds from PubChem.

Lastly, the SMILES were checked again for syntax errors or invalid chemistry by ```RdKit``` and the duplicates were removed. The final list contains 903 entries with the following columns: Name, Formula, Species, SMILES, InChI, Monoisotopic_mass, ChEBIid, KEGGid, PubChemId, source_database, Source, nonIsomeric_SMILES_byRDKit, iupac, synonyms, PubChemPY, correct_Name, Molecular mass, subclass, class', 'superclass.
