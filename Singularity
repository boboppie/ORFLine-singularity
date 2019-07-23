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
  yum -y install tar bzip2 git
  curl -fsSL https://repo.anaconda.com/miniconda/Miniconda2-latest-Linux-x86_64.sh -o miniconda2.sh
  bash miniconda2.sh -b -p /opt/miniconda2
  export PATH=/opt/miniconda2/bin:$PATH
  conda update -y conda
  conda install -y -c conda-forge wget 
  conda install -y -c conda-forge parallel
  conda install -y -c bioconda samtools
  conda install -y -c bioconda htslib bedtools bedops bowtie fastqc cutadapt trim-galore star stringtie emboss plastid bioconductor-riboseqr
  Rscript -e 'source("https://bioconductor.org/biocLite.R"); BiocInstaller::biocLite(c("GenomicFeatures", "rtracklayer"))'
  cd /opt
  git clone https://github.com/boboppie/orf-discovery.git
  cd orf-discovery
  chmod +x *.sh
  
%runscript
  export PATH=/opt/miniconda2/bin:$PATH
  echo $PATH
  echo "It's about to run some code..."
