Bootstrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum

%help
  This is a test image we're building for ORF discovery pipeline

%setup
  touch ${SINGULARITY_ROOTFS}/i_made_a_file.txt
  
%post
  sudo yum -y update
  sudo yum groupinstall 'Development Tools'
  sudo yum install curl file git
  sudo sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
  export PATH=~/.linuxbrew/bin:$PATH
  brew update
  brew install wget
  brew install parallel
  brew install samtools 
  brew install bedtools 
  brew install bedops
  brew tap brewsci/bio
  brew install bowtie
  brew install fastqc
  brew install cutadapt
  mkdir -p ~/bio-tool/bin
  cd ~/bio-tool
  curl -fsSL https://github.com/FelixKrueger/TrimGalore/archive/0.6.3.tar.gz -o trim_galore.tar.gz
  tar xvzf trim_galore.tar.gz
  ln -s TrimGalore-0.6.3/trim_galore bin/trim_galore
  cd ~
  export PATH=~/bio-tool/bin:$PATH
  brew install trim_galore
  brew install stringtie
  brew install emboss
  brew install R
  pip install --user numpy pysam cython
  pip install --user plastid
  export PATH=~/bin:~/.local.bin:/usr/local/bin:$PATH
  git clone git@github.com:boboppie/orf-discovery.git  
  cd orf-discovery
  chmod +x *.sh
  
%runscript
