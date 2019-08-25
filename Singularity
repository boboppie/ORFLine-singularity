Bootstrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum

%help
  This is a test image we're building for ORF discovery pipeline

%setup
  touch ${SINGULARITY_ROOTFS}/README.txt
  
%post
  yum -y install gcc tar bzip2 git which
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
  conda install -y -c bioconda sra-tools
  conda install -y -c bioconda emboss 
  conda install -y -c bioconda plastid
  conda install -y -c bioconda bioconductor-rhtslib
  Rscript -e 'install.packages("BiocManager", repos="http://cran.us.r-project.org"); BiocManager::install(c("riboSeqR", "GenomicFeatures", "rtracklayer"))'
  mkdir -p /opt/project
  cd /opt/project
  git clone https://github.com/boboppie/orf-discovery.git
  cd orf-discovery
  chmod +x *.sh
  
%runscript
  export PATH=/opt/miniconda2/bin:$PATH
  export PYTHONPATH=/opt/miniconda2/lib/python2.7/site-packages
  echo PATH variable
  echo -------------
  echo $PATH
  echo
  echo PYTHONPATH variable
  echo -------------
  echo $PYTHONPATH
  echo
  cp -r /opt/project/orf-discovery ~/
  cd ~/orf-discovery
  bash ./main.sh
