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
    - [basic configs](#basic-configs-2)
      - [`/home/nd20983/.bashrc`](#homend20983bashrc)
      - [`/home/nd20983/.profile`](#homend20983profile)
    - [ssh configs](#ssh-configs-2)


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

### basic configs

#### `/home/nd20983/.bashrc`

```
# ~/.bashrc: executed by bash(2) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        # We have color support; assume it's compliant with Ecma-48
        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
        # a case would tend to support setf rather than setaf.)
        color_prompt=yes
    else
        color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi

# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/home/nd20983/miniconda2/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/home/nd20983/miniconda2/etc/profile.d/conda.sh" ]; then
        . "/home/nd20983/miniconda2/etc/profile.d/conda.sh"
    else
        export PATH="/home/nd20983/miniconda2/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<

# ============personal setting and alias
export chome="/mnt/c/Users/nd20983/"
export pdf="/mnt/c/Users/nd20983/docs/EndNote/My EndNote Library.Data/PDF"
PS = "[\u@\h \W]\$"
```
[back to content](#contents)

#### `/home/nd20983/.profile`

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/.local/bin" ] ; then
    PATH="$HOME/.local/bin:$PATH"
fi
```

[back to content](#contents)

### ssh configs

```
Host bc4
    Hostname=bc4login2.acrc.bris.ac.uk
    User=nd20983
    IdentityFile=~/.ssh/id_rsa
    ForwardX11=yes
    ForwardX11Trusted=yes

Host eocene
    Hostname=eocene.ggy.bris.ac.uk
    User=nd20983
    IdentityFile=~/.ssh/id_rsa
    ForwardX11=yes
    ForwardX11Trusted=yes
```

[back to content](#contents)