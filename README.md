# Configs
Back up differing configs (remote hosts, local laptops...)

# Contents
- [Configs](#configs)
- [Contents](#contents)
  - [on Bridge machines (Eocene, Oligocene...)](#on-bridge-machines-eocene-oligocene)
    - [basic configs](#basic-configs)
      - [`/home/bridge/nd20983/.bashrc`](#homebridgend20983bashrc)
      - [`home/bridge/nd20983/.bash_profile`](#homebridgend20983bash_profile)
      - [`/home/bridge/nd20983/.profile`](#homebridgend20983profile)
    - [ssh configs](#ssh-configs)
  - [on bc4](#on-bc4)
    - [basic configs](#basic-configs-1)
      - [`/user/home/nd20983/.bashrc`](#userhomend20983bashrc)
      - [`/user/home/nd20983/.bash_profile`](#userhomend20983bash_profile)
      - [`/user/home/nd20983/.profile`](#userhomend20983profile)
    - [ssh configs](#ssh-configs-1)
  - [on windows WSL](#on-windows-wsl)


## on Bridge machines (Eocene, Oligocene...)

### basic configs

#### `/home/bridge/nd20983/.bashrc`

```
# .bashrc

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi

# User specific aliases and functions
module load bridge-default

# ferret
module add ferret
PATH=$PATH:/opt/local/ferret/bin

# Intel
module add intel/fc/10.1.015

PATH=$HOME/script:$PATH

PATH=.:/home/um/um/bin:/home/um/um/vn4.5/utils:/home/um/umui/bin:$PATH:/home/swsvalde/bin:/
export PATH

# set the default editor for TKCVS
EDITOR=/usr/bin/emacs
#strangeexport EDITOR
#export XLIB_SKIP_ARGB_VISUALS=1

# This is Ian Rutt's fix for some strange ifort bugs.
# Added by Dan 29/1/2009
ulimit -s unlimited

# Added by Dan 29/1/2009
alias rm='rm -f'
alias cp='cp -i'
alias mv='mv -i'

# Fran's aliases and settings
#alias webq='more /home/bridge/swsvalde/ummodel/scripts/expts_permian'
#alias last_web='tail -20 /home/swsvalde/ummodel/scripts/expts_permian.out'
alias jobs='~/script/job_summary.pl'
alias lsm='ferret -script ~/script/n_lsm.jnl | tail -1'
alias xconv='xconv -i '

alias ls='ls --color'
alias lt='ls -altr'
alias ll='ls -lrth'
alias l1='ls -1'
alias gv='ghostview'
alias xv='eog'
alias grep='grep --color'
alias vi='vim'
alias du='du -ah --max-depth=2 . | sort -rh | head -n 10'

# Yousheng alias
alias py='python -i'
alias expts_processing='ll ~/ummodel/access/ | grep nd20983 | tail -n 5'
alias aos='. ~/.local/venv/aos/bin/activate'
alias cartopy='. ~/.local/venv/cartopy_venv/bin/activate'
# prompt
#PS1="[\u@\h \W]\$"

# for IDL
#export IDL_STARTUP='/home/bridge/nd20983/idl'

#------------------------------------------------------
# isla (tool by Ian Ross) - for testing
#------------------------------------------------------
export PATH=$PATH:~ggxir/isla/delivery/v0.1

# for nedit
export LC_ALL=en_GB.UTF-8
# XDG_RUNTIME
export XDG_RUNTIME_DIR=~/XDG
export RUNLEVEL=3

# module load xancil
module load xancil/0.62

# module load python
module load anaconda/3.7-2019.10
module load ffmpeg/4.2.1

# load python virtual environment & python env
export PYTHONPATH=$PYTHONPATH:$HOME/bin

# library paths
```
[back to content](#contents)


#### `home/bridge/nd20983/.bash_profile`

```
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi

# User specific environment and startup programs

PATH=$PATH:$HOME/bin

export PATH
export ser=$HOME/BETR/SIMULATIONS/LR_ancils/Ser/
export silu=/export/silurian/array-01/nd20983/
export tria=/export/triassic/array-01/nd20983/
export anth=/export/anthropocene/array-01/nd20983/

export obm_pi=$HOME/ummodel/data/tfita4
export pi=$HOME/ummodel/data/tdezb1
export emi=$HOME/CMIP7/forcings/emissions/cmip6_data
```
[back to content](#contents)

#### `/home/bridge/nd20983/.profile`

```
#
#
ENV=$HOME/.bashrc ; export ENV

# This runs Paul's path changes etc.
if [ -f /home/bridge/ggpjv/setvars ]
then
   . /home/bridge/ggpjv/setvars
fi

# To use intel fortran compiler 8.1
#. /opt/intel_fc_81/bin/ifortvars.sh
# 28/9/2015: Taken out so that we can use new compiler:
#. /opt/intel/fc/10.1.015/bin/ifortvars.sh

# This is Ian Rutt's fix for some strange ifort bugs.
ulimit -s unlimited

#
#module load bridge-default dot

# This one for new libancil and bath_islands_scr etc.
module load bridge-default intel/fc/10.1.015 netcdf/intel_fc_10.1 isla opt-local convsh

#module load bridge-default netcdf/intel_fc_10.1/4.1.3
module load xancil/0.62

#module load python
#module load anaconda/3.7-2019.10
```
[back to content](#contents)

### ssh configs

```
    Hostname=bc4login2.acrc.bris.ac.uk
    User=nd20983
    IdentityFile=~/.ssh/id_rsa
    ForwardX11=yes
    ForwardX11Trusted=yes

Host bc41
    Hostname=bc4login1.acrc.bris.ac.uk
        User=nd20983
        IdentityFile=~/.ssh/id_rsa
        ForwardX11=yes
        ForwardX11Trusted=yes

Host bc43
        Hostname=bc4login3.acrc.bris.ac.uk
        User=nd20983
        IdentityFile=~/.ssh/id_rsa
        ForwardX11=yes
        ForwardX11Trusted=yes

Host bc44
        Hostname=bc4login4.acrc.bris.ac.uk
        User=nd20983
        IdentityFile=~/.ssh/id_rsa
        ForwardX11=yes
        ForwardX11Trusted=yes
Host github.com
        HostName=github.com
        User=git
        IdentityFile=~/.ssh/id_github
        ForwardX11=no
```
[back to content](#contents)

## on bc4

### basic configs

#### `/user/home/nd20983/.bashrc`

```

# Additional modules
module load languages/python/3.12.3

# Python config
export PYTHONPATH=$PATHONPATH:$HOME/bin
export venv='~/.local/lib/v_environments'
alias cartopy='. ~/.local/lib/v_environments/cartopy_venv/bin/activate'
export PATH=$HOME/.local/bin:$PATH
export PATH=$HOME/.local/bin:$PATH
export PATH=/user/home/nd20983/.local/bin:/software/spack/linux-rocky8-broadwell/gcc-12.3.0/netcdf-fortran-4.6.1-wl5j/bin:/software/spack/linux-rocky8-broadwell/gcc-12.3.0/cdo-2.4.0-redb/bin:/software/spack/linux-rocky8-broadwell/gcc-12.3.0/openmpi-5.0.3-gi7y/bin:/software/spack/linux-rocky8-broadwell/gcc-12.3.0/openssh-9.7p1-6ulm/bin:/software/spack/linux-rocky8-broadwell/gcc-12.3.0/cuda-12.4.0-z7k5/bin:/software/local/languages/Intel-OneAPI/vtune/2024.0/bin64:/software/local/languages/Intel-OneAPI/mpi/2021.11/opt/mpi/libfabric/bin:/software/local/languages/Intel-OneAPI/mpi/2021.11/bin:/software/local/languages/Intel-OneAPI/mkl/2024.0/bin:/software/local/languages/Intel-OneAPI/itac/2022.0/bin:/software/local/languages/Intel-OneAPI/inspector/2024.0/bin64:/software/local/languages/Intel-OneAPI/dpcpp-ct/2024.0/bin:/software/local/languages/Intel-OneAPI/dev-utilities/2024.0/bin:/software/local/languages/Intel-OneAPI/debugger/2024.0/opt/debugger/bin:/software/local/languages/Intel-OneAPI/compiler/2024.0/opt/oclfpga/bin:/software/local/languages/Intel-OneAPI/compiler/2024.0/bin:/software/local/languages/Intel-OneAPI/advisor/2024.0/bin64:/mnt/storage/private/bridge/um/PUM64/um/bin:.:/group/bridge/um/bin:/mnt/storage/private/bridge/um/bin:/user/home/nd20983/.local/bin:/software/local/languages/miniforge3/envs/python-3.12.3/bin:/software/spack/linux-rocky8-broadwell/gcc-12.3.0/cmake-3.27.9-ft32/bin:/software/spack/linux-rocky8-broadwell/gcc-12.3.0/gcc-12.3.0-vpim/bin:/software/spack/linux-rocky8-broadwell/gcc-12.3.0/binutils-2.42-p6tx/bin:/system/steel-stack/slurm/23.11.10/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/usr/lpp/mmfs/bin:/user/home/nd20983/bin:/mnt/storage/private/bridge/um/fcm/fcm-2-0/bin:/group/bridge/swsvalde/bin:/group/bridge/swsvalde/bin/ummodel:/mnt/storage/private/bridge/um/PUM64/um/vn4.5/utils
```
[back to content](#contents)

#### `/user/home/nd20983/.bash_profile`

```
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi

# User specific environment and startup programs

export PATH=$PATH:$HOME/.local/bin:$HOME/bin
export PATH=$PATH:/mnt/storage/private/bridge/um/fcm/fcm-2-0/bin
export PATH=/mnt/storage/private/bridge/um/bin:$PATH

# Aliases
export env=$HOME/.local/lib/v_environments

if [ -f /mnt/storage/private/bridge/swsvalde/etc/defaults/met.profile ] ; then
    . /mnt/storage/private/bridge/swsvalde/etc/defaults/met.profile
fi

module add languages/Intel-OneAPI/2024.0.2 1>/dev/null 2>/dev/null
module add openmpi
module add cdo
module add netcdf-fortran
```
[back to content](#contents)

#### `/user/home/nd20983/.profile`

```
fi

# User specific environment and startup programs

export PATH=$PATH:$HOME/.local/bin:$HOME/bin

#
# UM setup
#
export #PATH=/mnt/storage/private/bridge/um/bin:$PATH:/mnt/storage/private/bridge/um/fcm/fcm-2-0/bin
# --- Set Standard PATH, MANPATH, LD_LIBRARY_PATH
PATH=.:$HOME/bin:/mnt/storage/private/bridge/um/bin:/mnt/storage/private/bridge/swsvalde/bin:$HOME/swsvalde/bin/ummodel:$PATH
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/X11R6/lib

# --- Change prompt to something more informative
#PS1="`/bin/uname -n`\$ "

# --- Export all relevant variables
export PATH MANPATH LD_LIBRARY_PATH

# --- Set variable called machine
machine=`uname -n | cut -d"." -f1`

export PATH=.:$HOME/bin:/mnt/storage/private/bridge/swsvalde/bin:/mnt/storage/private/bridge/um/bin:$PATH
export EDITOR=emacs
export DUMP2HOLD=$HOME/DUMP2HOLD

ulimit -s unlimited
```
[back to content](#contents)

### ssh configs

```
Host archer2
    Hostname=login.archer2.ac.uk
    User=nd20983
    IdentityFile=~/.ssh/id_rsa
    ForwardX11=yes
    ForwardX11Trusted=yes
    ServerAliveInterval 60
    ServerAliveCountMax 3

Host eocene
    Hostname=eocene.ggy.bris.ac.uk
    User=nd20983
    IdentityFile=~/.ssh/id_rsa
    ForwardX11=yes
    ForwardX11Trusted=yes

Host ubuntu
    Hostname=IT080129
    User=nd20983
    IdentityFile=~/.ssh/id_rsa
    ForwardX11=yes
    ForwardX11Trusted=yes

Host almond
    Hostname=almond.ggy.bris.ac.uk
    User=genie_instructor2
    IdentityFile=~/.ssh/id_rsa
    ForwardX11=yes
    ForwardX11Trusted=yes
    ServerAliveInterval 60
    ServerAliveCountMax 5
```
[back to content](#contents)

## on windows WSL

