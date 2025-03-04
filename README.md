# quartet_rna_project
This is an Image for RNA modification analysis of direct RNA-seq data, using dorado and modkit. It is built using Apptainer and can be run by both Apptainer and Singularity.

## Getting Started

### Installation

_Below is an example of how you can set up the Image and run._

1. Download the sif file and load apptainer if have
   ```sh
   wget https://github.com/mritchielab/quartet_rna_project/blob/main/RNA_modification.def
   module load apptainer
   ```
2. Build Image (def file)
   ```sh
   apptainer build --fakeroot RNA_modification.sif RNA_modification.def
   ```
3. Read-to-run your sample now
   ```sh
   apptainer run --nv \
    --bind /Singularity/testdata:/input \
    --bind /Singularity/testresult:/output \
    --bind /project/reference:/reference \
    ./RNA_modification.sif \
    --input /input \
    --output /output \
    --ref /reference/gencode.v43.transcripts.fa \
    --model-dir /opt/dorado/models
   ```

### Checking results
The pipeline produces BAM file from **dorado basecaller**, and bed file from **modkit**.
