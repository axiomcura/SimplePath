# SimplePath

Simple path is an easy to use script that allows generating files for network relationship and can easily be uploaded to Cytoscape or any network visualization program that supports SIF files. SimplePath uniquness comes from the ability to visualize networks from an independent locus or all loci.

## Workflow

### Arguments

Below are the required and optional arguments that can be accessed by typing `python simple_path.py -h`:

```text 

usage: simple_path.py [-h] [-i INPUT] [-o PARAMETER] [-t PARAMETER] [-db FILE]

simple program for generating SIF to full understand relationships between biological processes.

optional arguments:
  -h, --help            show this help message and exit
  -o PARAMETER, --output PARAMETER
                        name of the outfile default='Simple_out'
  -db FILE, --database FILE
                        path to database. Default path is `./Data/STRING.txt

Required Arguments:
  -i INPUT, --input INPUT
                        input file
  -t PARAMETER, --interaction_type PARAMETER
                        Interaction type
                        
 ```
 
 ### Inputs

The required inputs for this script is a STRING.txt database and an input file in `.gmt` format

Example of the input file is shown below
 
 ```
Fanconi anemia locus 0	Locus for PALB2	NUPR1	CTB-134H23.2	SLC5A11	KIAA0556	CD19	SH2B1
Fanconi anemia locus 1	Locus for FANCF	CSTF3	FBXO3	SLC17A6	CCDC73	CAPRIN1	RCN1	BDNF	METT
Fanconi anemia locus 2	Locus for RAD51C, BRIP1	CD79B	CACNG1	TANC2	SMG8	RP11-15E18.4	TEX2
Fanconi anemia locus 3	Locus for FANCC	TMOD1	MSANTD3-TMEFF1	TEX10	HIATL2	LPPR1	MRPL50
Fanconi anemia locus 4	Locus for FANCA	DBNDD1	AC133919.6	RP11-356C4.2	MC1R	SPIRE2	C16orf
Fanconi anemia locus 5	Locus for UBE2T	PPFIA4	SNRPE	LGR6	ZC3H11A	TMEM183A	PPP1R12B	SOX13
Fanconi anemia locus 6	Locus for FANCD2	VGLL4	TAMM41	ZFYVE20	EAF1	IQSEC1	SLC6A6	VHL	FANC
Fanconi anemia locus 7	Locus for FANCE	KCNK5	MTCH1	PI16	BRPF3	TMEM217	RPL10A	GLP1R	ARMC1
Fanconi anemia locus 8	Locus for BRCA2	PROSER1	MRPS31	UFM1	AKAP11	N4BP2L2	TNFSF11	FOXO1
Fanconi anemia locus 9	Locus for ERCC4	GPR139	C16orf88	RPS15A	BFAR	CTD-2349B8.1	NDE1
Fanconi anemia locus 10	Locus for FANCI	POLG	AC016251.1	FANCI	GABARAPL3	FES	C15orf38
Fanconi anemia locus 11	Locus for SLX4	FAM86A	USP7	ROGDI	ALG1	CDIP1	UBN1	RP11-297M9.1
```

Where each locus contains a set of proteins that will be searched in the program 

These genes will be looked up on the STRING.txt database shown below:

```
ARF5	DVL2	0.166000
ARF5	DYRK4	0.166000
ARF5	PPP5C	0.254968
ARF5	MAP4K5	0.157276
ARF5	RALBP1	0.156000
ARF5	PKP2	0.160210
ARF5	ACAP1	0.328000
ARF5	MAP2K5	0.242000
ARF5	MYO15A	0.272395
ARF5	MAPK13	0.190000
ARF5	STX1B	0.263160
ARF5	MAPK12	0.19000
...
```

which contains data of protein protein interactions

### Command

To run this program type:

```
python simple_path.py -i Input.gmt.txt -o FA_out -t pp -db ./Data/STRING.txt
```

you can replace the `-i` option to your own desired input file

### Results

After running the program a directory will appear on you current directory that contains all `.SIF` files.

```

BRCA2-092221-214503.sif     FANCC-092221-214503.sif     FANCI-092221-214503.sif     all_nodes-092221-214503.sif
BRIP1-092221-214503.sif     FANCD2-092221-214503.sif    PALB2-092221-214503.sif
ERCC4-092221-214503.sif     FANCE-092221-214503.sif     SLX4-092221-214503.sif
FANCA-092221-214503.sif     FANCF-092221-214503.sif     UBE2T-092221-214503.sif
```

## Plotting

The generated files are compatible with cytoscape, therefore you can upload these files and plot a network on the program. This is done by clicking *view → import → Network from file → .SIF file*

![Plot](https://user-images.githubusercontent.com/31600622/134613178-09d3c3e5-afb0-4e35-9bf5-ff300e9ab094.png)
