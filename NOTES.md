## CMD

@echo off
:: for /F will launch a new instance of cmd so we create a guard to prevent an infnite loop
if not defined FNM_AUTORUN_GUARD (
set "FNM_AUTORUN_GUARD=AutorunGuard"
FOR /f "tokens=\*" %%z IN ('fnm env --use-on-cd') DO CALL %%z
)

## Git

$ git config --list --show-origin
$ git config --global user.name "ljanotte"
$ git config --global user.email "ljanotte@gmail.com"
$ git config --global core.editor "code --wait"

$ code .bashrc {

    # Start SSH Agent

#----------------------------

SSH_ENV="$HOME/.ssh/environment"

function run_ssh_env {
. "${SSH_ENV}" > /dev/null
}

function start_ssh_agent {
echo "Initializing new SSH agent..."
ssh-agent | sed 's/^echo/#echo/' > "${SSH_ENV}"
  echo "succeeded"
  chmod 600 "${SSH_ENV}"

run_ssh_env;

ssh-add ~/.ssh/id_rsa;
}

if [ -f "${SSH_ENV}" ]; then
run_ssh_env;
ps -ef | grep ${SSH_AGENT_PID} | grep ssh-agent$ > /dev/null || {
start_ssh_agent;
}
else
start_ssh_agent;
fi

}

$ code .bash_profile {

    test -f ~/.profile && . ~/.profile
    test -f ~/.bashrc && . ~/.bashrc

}

$ nano .bashrc {

eval "$(fnm env --use-on-cd)"

}

## node

$ winget install Schniz.fnm
$ fnm use --install-if-missing 20
$ node -v
$ npm -v

## GitHub

$ git clone git@github.com:ljanotte/vendas-online-web.git
$ cd vendas-online-web

## vite

$ npm create vite@latest . -- --template react-ts
$ npm install
$ npm run dev

## Configurando Eslint e prettier

npm install --save-dev @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint eslint-config-prettier eslint-plugin-import eslint-plugin-prettier eslint-plugin-react eslint-plugin-simple-import-sort pre-commit prettier
