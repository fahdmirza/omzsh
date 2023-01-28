For this demo, I am using Ubuntu 20.04 as my operating system and zsh as my shell. You can install zsh on Ubuntu by using apt install zsh. You can also make zsh as your default shell by using chsh command. Ok, so I am presuming that you have already installed Ubuntu and zsh, and ready to go. 

#Install oh-my-zsh:
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

#Install powerlevel9k theme:
git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k
sed -i 's@^ZSH_THEME=.*$@ZSH_THEME="powerlevel9k/powerlevel9k"@g' ~/.zshrc

#Install powerline fonts:
wget https://github.com/powerline/powerline/raw/develop/font/PowerlineSymbols.otf
wget https://github.com/powerline/powerline/raw/develop/font/10-powerline-symbols.conf
mkdir -p ~/.local/share/fonts/
mv PowerlineSymbols.otf ~/.local/share/fonts/
#fc-cache command scans font directories and build font cache for applications which use fontconfig for their font handling.
fc-cache -vf ~/.local/share/fonts/ 
mkdir -p ~/.config/fontconfig/conf.d/
mv 10-powerline-symbols.conf ~/.config/fontconfig/conf.d/

#Install autosuggestions and syntax highlighting plugins:
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
sed -i 's@plugins=(git)@plugins=(git zsh-autosuggestions zsh-syntax-highlighting)@g' ~/.zshrc

# Also add export TERM="xterm-256color" at the top of your ~/.zshrc to avoid warning at login in zsh shell.

# Close your terminal here and open it again for omz , themes and plugins to take effect.

#Install colorls:
apt install ruby ruby-dev ruby-colorize
gem install colorls

#You can also use colorls -la command to beautify the ls output.
