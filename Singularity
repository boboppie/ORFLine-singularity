Bootstrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum

%help
  This is a test image we're building for ORF discovery pipeline

%setup
  touch ${SINGULARITY_ROOTFS}/README.txt
  
%post
  yum -y install tar bzip2 git
  curl -fsSL https://repo.anaconda.com/miniconda/Miniconda2-latest-Linux-x86_64.sh -o miniconda2.sh
  bash miniconda2.sh -b -p /opt/miniconda2
  export PATH=/opt/miniconda2/bin:$PATH
  conda install -y -c conda-forge wget 
  conda install -y -c conda-forge parallel
  conda install -y -c bioconda samtools
  conda install -y -c bioconda htslib 
  conda install -y -c bioconda bedtools 
  conda install -y -c bioconda bedops 
  conda install -y -c bioconda bowtie 
  conda install -y -c bioconda fastqc
  conda install -y -c bioconda cutadapt 
  conda install -y -c bioconda trim-galore 
  conda install -y -c bioconda star 
  conda install -y -c bioconda stringtie 
  conda install -y -c bioconda emboss 
  conda install -y -c bioconda plastid 
  conda install -y -c bioconda bioconductor-rhtslib
  conda install -y -c r r-xml
  conda install -y -c r r-rcurl
  Rscript -e 'source("https://bioconductor.org/biocLite.R"); BiocInstaller::biocLite(c("riboSeqR", "GenomicFeatures", "rtracklayer"))'
  cd /opt
  git clone https://github.com/boboppie/orf-discovery.git
  cd orf-discovery
  
%runscript
  export PATH=/opt/miniconda2/bin:$PATH
  echo $PATH
  echo "It's about to run some code..."
