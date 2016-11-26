# Afficher la branche active dans terminal

## Introduction
Le code dans la section suivante peut être ajouté au fichier de configuration
` ~/.bash_profile` et a pour effet de montrer le nom de la branche active quand
on est dans un répertoire git.

## Le code
```
################################################################################
# CODE FROM Doctor Blondin - adds branch when in git directory
function parse_git_branch_and_add_brackets {
  git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/\ \[\1\]/'
  }
export LSCOLORS=CxdxxxxxExxxxxExExCxCx
PS1="\n\e[36m\$(parse_git_branch_and_add_brackets) \e[32;1m\u\e[0m \e[33;1m[\w]\e[0m\n $ "
alias ls="ls -G -F"
alias lss="ls -G | rev | sort | rev"
```
