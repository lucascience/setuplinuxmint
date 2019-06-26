Personalização das configurações após instalação do Linux Mint

**Última versão testada:** Linux Mint 19.1 Tessa (64 bits)

# Instalação básica

Antes de mais nada, vamos rodar um update e um upgrade :)
<pre><code>sudo apt update && sudo apt upgrade -y</code></pre>

Remover programas não utilizados (lembrando que EU não os utilizo...rs)
<pre><code>sudo apt remove hexchat transmission-gtk rhythmbox thunderbird -y</code></pre>

Clamav Anti Virus
<pre><code>sudo apt install clamav clamtk -y</code></pre>

Codecs de mídia
<pre><code>sudo apt install mint-meta-codecs -y</code></pre>

Suporte à arquivos compactados
<pre><code>sudo apt install rar p7zip-full -y</code></pre>

Vim
<pre><code>sudo apt install vim -y</code></pre>

Open SSH Server
<pre><code>sudo apt install openssh-server -y</code></pre>

Git & gitg
<pre><code>sudo apt install git-core gitg -y</code></pre>

Fonts true type
<pre><code>sudo apt install msttcorefonts -y</code></pre>

# Copiar arquivos deste projeto

<pre><code>git clone git://github.com/lucascience/setuplinuxmint.git ~/.setuplinuxmint</code></pre>

# Programas

Remmina
<pre><code>sudo apt install remmina remmina-plugin-rdp remmina-plugin-secret -y</code></pre>

Gparted
<pre><code>sudo apt install gparted -y</code></pre>

VPN (F5)
<pre><code>sudo dpkg -i ~/.setuplinuxmint/files/linux_f5vpn.x86_64.deb</code></pre>

Filezilla
<pre><code>sudo apt install filezilla -y</code></pre>

Htop
<pre><code>sudo apt install htop -y</code></pre>

Meld
<pre><code>sudo apt install meld -y</code></pre>

Synapse
<pre><code>sudo apt install synapse -y</code></pre>

NMAP
Use 'sudo nmap -sS <ip>' pra saber as portas abertas de uma máquina remota
E use 'netstat -npl | grep <port>' para saber os processos servindo determinada porta
<pre><code>sudo apt install nmap -y</code></pre>

Flameshot (Se o link estiver desatualizado, acesse essa página, baixe a última versão e salve-o com o nome flameshot.deb:)
<pre><code>wget https://github.com/lupoDharkael/flameshot/releases/download/v0.6.0/flameshot_0.6.0_bionic_x86_64.deb -O flameshot.deb
sudo dpkg -i flameshot.deb
sudo apt-get install -f
rm -rf flameshot.deb</code></pre>

Snap
<pre><code>sudo apt install snapd -y</code></pre>

Google Chrome
<pre><code>wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb</code></pre>

Flash
<pre><code>sudo apt install adobe-flashplugin browser-plugin-freshplayer-pepperflash -y</code></pre>

Powershell
<pre><code>wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo add-apt-repository universe
sudo apt-get install -y powershell
rm -rf packages-microsoft-prod.deb</code></pre>

Spotify
<pre><code>sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 931FF8E79F0876134EDDBDCCA87FF9DF48BF1C90
echo deb http://repository.spotify.com stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list
sudo apt update
sudo apt install spotify-client</code></pre>

Stacer (utilitário para limpeza e melhora de desempenho)
<pre><code>sudo add-apt-repository ppa:oguzhaninan/stacer
sudo apt update
sudo apt install stacer -y</code></pre>

TeamViewer
<pre><code>sudo sh -c "echo 'deb http://linux.teamviewer.com/deb stable main' >> /etc/apt/sources.list.d/teamviewer.list"
wget -q https://download.teamviewer.com/download/linux/signature/TeamViewer2017.asc -O- | sudo apt-key add -
sudo apt update
sudo apt install teamviewer -y</code></pre>

Virtualbox
<pre><code>sudo apt install virtualbox vde2 virtualbox-guest-additions-iso virtualbox-qt libqt5opengl5</code></pre>

Visual Studio Code
<pre><code>sudo snap install code --classic</code></pre>

Wine
Enable 32 bit programs
<pre><code>sudo dpkg --add-architecture i386</code></pre>

Install Wine
<pre><code>sudo apt install --install-recommends winehq-stable -y</code></pre>

# Liberação de acesso via VNC

1. Remove the default Vino server:

<pre><code>sudo apt remove vino -y</code></pre>

2. Install x11vnc:

<pre><code>sudo apt install x11vnc -y</code></pre>

3. Create the directory for the password file:

<pre><code>sudo mkdir /etc/x11vnc</code></pre>

4. Create the encrypted password file:

<pre><code>sudo x11vnc --storepasswd /etc/x11vnc/vncpwd</code></pre>

You will be asked to enter and verify the password.  Then press Y to save the password file.

5. Create the systemd service file for the x11vnc service:

<pre><code>sudo xed /lib/systemd/system/x11vnc.service</code></pre>

Copy/Paste this code into the empty file:

<pre><code>[Unit]
Description=Start x11vnc at startup.
After=multi-user.target

[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -auth guess -forever -noxdamage -repeat -rfbauth /etc/x11vnc/vncpwd -rfbport 5900 -shared

[Install]
WantedBy=multi-user.target</code></pre>

6. Reload the services:

<pre><code>sudo systemctl daemon-reload</code></pre>

7. Enable the x11vnc service at boot time:

<pre><code>sudo systemctl enable x11vnc.service</code></pre>

8. Start the service:

Either reboot or

<pre><code>sudo systemctl start x11vnc.service</code></pre>

9. Install remmina-plugin-vnc

<pre><code>sudo apt install remmina-plugin-vnc</code></pre>

# DotFiles

<pre><code>cat ~/.setuplinux/dotfiles/.bashrc >> ~/.bashrc</code></pre>

# Outros

Extensions for Google Chrome:
* Last Pass: https://chrome.google.com/webstore/detail/lastpass-free-password-ma/hdokiejnpimakedhajhdlcegeplioahd
* Video Speed Controller: https://chrome.google.com/webstore/detail/video-speed-controller/nffaoalbilbmmfgbnbgppjihopabppdk
* Onetab: https://chrome.google.com/webstore/detail/onetab/chphlpgkkbolifaimnlloiipkdnihall
