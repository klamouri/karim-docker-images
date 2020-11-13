FROM confluentinc/cp-kafka:4.1.4-1
LABEL maintainer="karim@lamouri.me"
ENV TERM=
ENV COLORTERM=

RUN apt-get update \
    && apt-get install -y \
        apt-utils \
        curl \
        git \
        wget \
        zsh \
    && rm -rf /var/lib/apt/lists/* \
    && sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
    # This one isn't working because powerlevel10k is only working with ZSH > 5.1 which isn't easily available with Debian Jessie (Confluent base image)
    # && git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k \
    # && sed -i 's#.*ZSH_THEME.*#ZSH_THEME="powerlevel10k/powerlevel10k"#' ~/.zshrc

ENTRYPOINT []
CMD /bin/zsh