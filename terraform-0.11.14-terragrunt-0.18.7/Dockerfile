FROM library/ubuntu:20.04
LABEL maintainer="karim@lamouri.me"

COPY commons/.p10k.zsh /root/.p10k.zsh
RUN mkdir app \
    && apt-get update \
    && DEBIAN_FRONTEND="noninteractive" apt-get install -y \
        apt-utils \
        curl \
        git \
        wget \
        zsh \
        software-properties-common \
    # install terraform
    && curl -fsSL https://apt.releases.hashicorp.com/gpg | apt-key add - \
    && apt-add-repository "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $(lsb_release -cs) main" \
    && apt install terraform=0.11.14 \
    && rm -rf /var/lib/apt/lists/* \
    # Install terragrunt
    && curl -L https://github.com/gruntwork-io/terragrunt/releases/download/v0.18.7/terragrunt_linux_amd64 -o /usr/local/bin/terragrunt \
    && chmod u+x /usr/local/bin/terragrunt \
    # Install Oh-My-ZSH and powerlevel10k
    && sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" \
    && git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k \
    && sed -i 's#.*ZSH_THEME.*#ZSH_THEME="powerlevel10k/powerlevel10k"#' ~/.zshrc \
    && echo '[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh' >> ~/.zshrc \
    # force install of lazy powerlevel10k components now using: https://github.com/romkatv/powerlevel10k#how-do-i-install-powerlevel10k-on-a-machine-without-internet-access
    && target_uname=$(uname -sm | tr '[A-Z]' '[a-z]') \
    && GITSTATUS_CACHE_DIR=${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k/gitstatus/usrbin \
    && ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k/gitstatus/install -f -s "${target_uname% *}" -m "${target_uname#* }"

WORKDIR app
ENTRYPOINT []
CMD /bin/zsh