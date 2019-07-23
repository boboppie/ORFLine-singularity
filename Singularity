Bootstrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum

%help
  This is a test image we're building for ORF discovery pipeline

%setup
  touch ${SINGULARITY_ROOTFS}/README.txt
  
%post
  yum -y update
  curl -fsSL https://repo.anaconda.com/miniconda/Miniconda2-latest-Linux-x86_64.sh -o miniconda2.sh
  bash miniconda2.sh -b -p /opt/miniconda2
  export PATH=/opt/miniconda2/bin:$PATH
  conda install -y -c conda-forge wget parallel
  conda install -y -c bioconda samtools htslib bedtools bedops bowtie fastqc cutadapt trim-galore star stringtie emboss plastid bioconductor-riboseqr
  Rscript -e 'source("https://bioconductor.org/biocLite.R"); BiocInstaller::biocLite(c("GenomicFeatures", "rtracklayer"))'
  git clone git@github.com:boboppie/orf-discovery.git  
  cd orf-discovery
  chmod +x *.sh
  
%runscript
  echo "It's about to run some code..."
