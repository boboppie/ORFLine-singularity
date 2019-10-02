# ORFLine-singularity
Repo for making smORF discovery pipeline [ORFLine](https://github.com/boboppie/ORFLine) singularity image. Image was automatically build by [Singularity Hub](https://singularity-hub.org/). During image build, all orf-discovery pipeline dependencies were installed, specifically, bioinformatics tools were installed via [Miniconda](https://docs.conda.io/en/latest/miniconda.html) to */opt/miniconda/bin* and pipeline source code was pulled to *~/project/*.

## Usage

Install singularity via conda:

    # Assuming Linux and root privilige
    curl -fsSL https://repo.anaconda.com/miniconda/Miniconda2-latest-Linux-x86_64.sh -o miniconda2.sh
    
    # Install miniconda to user home directory
    bash miniconda2.sh -b -p ~/miniconda2
    
    # Add conda bin to $PATH
    export PATH=~/miniconda2/bin:$PATH
    
    # Install singularity
    conda install -y -c bioconda singularity
    
Pull the container to your machine:

    singularity pull shub://boboppie/ORFLine-singularity
    # the default name of the image is ORFLine-singularity_latest.sif

Shell into the container:

    singularity shell ORFLine-singularity_latest.sif

Run the container:

    singularity run ORFLine-singularity_latest.sif

Need more help? Please read Singularity Hub [usage guide](https://github.com/singularityhub/singularityhub.github.io/wiki/Deploy#order-of-operations).
