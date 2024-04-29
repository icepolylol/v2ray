---


---

<h1 id="installing-v2ray-server-and-client-on-ubuntu-22.04">Installing V2Ray Server and Client on Ubuntu 22.04</h1>
<h2 id="introduction"><strong>### Introduction</strong></h2>
<p>V2Ray distinguishes out among proxy software as a versatile and effective tool for securely relaying internet traffic. V2Ray’s extensive features and powerful performance make it a popular choice among users looking to improve their privacy and evade online limitations.This article will walk users through the process of installing V2Ray on Ubuntu 22.04, providing a smooth setup process regardless of their level of experience. By following the procedures given in this article, readers will gain access to V2Ray’s strong capabilities, opening them a world of possibilities for safe internet browsing and network management.</p>
<h2 id="prerequisites">## Prerequisites</h2>
<p>Please make sure that the following conditions are met before installing V2Ray on Ubuntu 22.04.</p>
<ol>
<li>
<p><strong>Ubuntu 22.04:</strong> A machine with at least 2GB RAM and 1 CPUs. In case of an Ubuntu server, follow the <a href="https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-22-04" title="https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-22-04 (Ctrl or Cmd-click to open)">Ubuntu Initial Server Setup</a> for setup instructions.</p>
</li>
<li>
<p><strong>Root Access:</strong> To run commands and install packages on Ubuntu, you’ll need root access or a user account with sudo rights.</p>
</li>
<li>
<p><strong>Domain (Optional):</strong> A fully registered domain name. This tutorial will use <code>your_domain</code> as an example throughout. You can purchase a domain name on <a href="https://namecheap.com" title="https://namecheap.com (Ctrl or Cmd-click to open)">Namecheap</a> or use the domain registrar of your choice.</p>
</li>
</ol>
<p>While it is not essential, having a domain for your V2Ray server allows you to use TLS (Transport Layer Security) for better security. If you choose to use a domain, ensure sure it is properly configured and points to your server’s IP address.</p>
<ol start="4">
<li><strong>Dns records:</strong> Both of the following DNS records set up for your server. You can follow <a href="https://www.digitalocean.com/community/tutorials/an-introduction-to-digitalocean-dns" title="https://www.digitalocean.com/community/tutorials/an-introduction-to-digitalocean-dns (Ctrl or Cmd-click to open)">this introduction to DigitalOcean DNS</a> for details on how to add them.</li>
</ol>
<ul>
<li>
<p>An A record with <code>your_domain</code> pointing to your server’s public IP address.</p>
</li>
<li>
<p>An A record with <code>www.your_domain</code> pointing to your server’s public IP address.</p>
</li>
</ul>
<p><strong>5. V2Ray Client:</strong> To connect to the V2Ray server, you’ll need a V2Ray client installed on your device. For Windows/ubuntu, you can use clients like nekoray.</p>
<p>Once these conditions are met, you will be able to install V2Ray on Ubuntu 22.04.</p>
<h2 id="step-1----ssh-access-to-your-server"><a href="https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04#step-1-installing-certbot" title="https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04#step-1-installing-certbot (Ctrl or Cmd-click to open)">Step 1 –</a> <strong>SSH Access to Your Server</strong></h2>
<p>SSH (Secure Shell) is a protocol that allows you to securely access and manage your server remotely. Before you can install V2Ray on your Ubuntu 22.04 server, you’ll need to connect to it via SSH.</p>
<ul>
<li>
<p><strong>Linux/Mac Users:</strong> Open the terminal application on your local machine. You can usually find it in your applications menu or by searching for “Terminal.”</p>
</li>
<li>
<p><strong>Windows Users:</strong> Download and install PuTTY, a popular SSH client for Windows. You can download PuTTY from the official website: [PuTTY Download Page](<a href="https://www.putty.org/" title="https://www.putty.org/ (Ctrl or Cmd-click to open)">https://www.putty.org/</a>)</p>
</li>
</ul>
<p>Open PuTTY and enter the IP address of your server in the “Host Name (or IP address)” field. Leave the port as default (22) and click “Open” to start the SSH connection.</p>
<ul>
<li><strong>Linux/Mac Users:</strong> In the terminal, use the following command to connect to your server:</li>
</ul>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">ssh</span> username@server_ip
</code></pre>
<blockquote>
<p>Replace <code>username</code> with your actual username on the server, and</p>
</blockquote>
<blockquote>
<p><code>server_ip</code> with the IP address of your Ubuntu 22.04 server</p>
</blockquote>
<blockquote>
<p>Enter Your Password</p>
</blockquote>
<ul>
<li>
<p>After initiating the SSH connection, you’ll be prompted to enter your password. Type your password carefully (note: no characters will appear on the screen as you type), then press Enter.</p>
</li>
<li>
<p>Once you’ve entered the correct password, you should be logged into your Ubuntu 22.04 server via SSH. You’ll see a command line interface, indicating that you now have remote access to your server.</p>
</li>
</ul>
<p>Congratulations! You’ve successfully connected to your Ubuntu 22.04 server via SSH. You’re now ready to proceed with the installation of V2Ray. If you encounter any issues during the SSH connection process, double-check your server’s IP address, username, and password.</p>
<h2 id="step-2----install-3x-ui-panel">Step 2 – Install 3X-UI Panel</h2>
<p>3X-UI is a user-friendly panel that simplifies server management tasks. To install 3X-UI on your Ubuntu 22.04 server, follow these steps:</p>
<ul>
<li>
<p>Open a terminal window If you’re accessing your server via SSH, you can use the terminal application on your local machine.</p>
</li>
<li>
<p>Run the following command to update the package lists and then upgrade the installed packages to their most recent versions:</p>
</li>
</ul>
<p>This command ensures that your server has the latest software packages and security updates installed.</p>
<pre><code>sudo apt update &amp;&amp; sudo apt upgrade -y
</code></pre>
<ul>
<li>Once the package update and upgrade process is complete, run the following command to download and execute the installation script for 3X-UI:</li>
</ul>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">bash</span> <span class="token operator">&lt;</span><span class="token punctuation">(</span>curl -Ls https://raw.githubusercontent.com/mhsanaei/3x-ui/master/install.sh<span class="token punctuation">)</span>
</code></pre>
<p>This command will retrieve the installation script from the GitHub repository and execute it. During the installation process, you may encounter a purple window. If you see this, simply press <code>ENTER</code>to proceed.</p>
<ul>
<li>
<p>Follow the prompts during the installation process. When prompted, provide the following information:</p>
</li>
<li>
<p><strong>Username:</strong> Choose a username for accessing the 3X-UI panel.</p>
</li>
<li>
<p><strong>Password:</strong> Set a strong password for the chosen username.</p>
</li>
<li>
<p><strong>Port:</strong> Specify a custom port number (e.g., 8443) for accessing the 3X-UI panel. Using a non-standard port enhances security by reducing exposure to common attack vectors.</p>
<pre><code>[secondary_label Output]
Install/update finished! For security it's recommended to modify panel settings
Do you want to continue with the modification [y/n]?:y
Please set up your username:admin
Please set up your password:admin
Please set up the panel port:8443
Initializing, please wait...
set username and password success
Account name and password set successfully!
set port 8443 successPanel port set successfully!
</code></pre>
</li>
</ul>
<p>Once the installation is complete, you will receive a confirmation message indicating that 3X-UI has been successfully installed on your server.</p>
<ul>
<li>
<p>Access 3X-UI by opening a web browser and navigating to the URL of your server followed by the custom port number you specified during installation. For example, if your server’s IP address is “123.456.789.0” and you chose port 8443, you would enter <code>https://123.456.789.0:8443</code> [](<a href="https://123.456.789.0:8443">https://123.456.789.0:8443</a>"** “<a href="https://123.456.789.0:8443">https://123.456.789.0:8443</a>”** (Ctrl or Cmd-click to open)") in the address bar of your browser.</p>
</li>
<li>
<p>Log in to the 3X-UI panel using the username and password you configured during the installation process.</p>
</li>
<li>
<p>Upon successful login, you will be greeted with the 3X-UI dashboard, where you can manage various aspects of your server with ease.</p>
</li>
</ul>
<h2 id="step-3-accessing-3x-ui-panel-options">Step 3: Accessing 3X-UI Panel Options</h2>
<p>After the installation process, when you run the <code>x-ui</code> command, you’ll be presented with a menu in your terminal window displaying various options for managing the 3X-UI panel.</p>
<p>We’ll explain two important configurations: enabling BBR and SSL Certificate Management with Let’s Encrypt.</p>
<p>The menu will look like this:</p>
<pre><code>[secondary_label Output]
1. Install
2. Update
3. Custom Version
4. Uninstall
————————————————
5. Reset Username &amp; Password &amp; Secret Token
6. Reset Settings
7. Change Port
8. View Current Settings
————————————————
9. Start
10. Stop
11. Restart
12. Check Status
13. Check Logs
————————————————
14. Enable Autostart
15. Disable Autostart
————————————————
16. SSL Certificate Management
17. Cloudflare SSL Certificate
18. IP Limit Management
19. WARP Management
20. Firewall Management
————————————————
21. Enable BBR
22. Update Geo Files
23. Speedtest by Ookla

Panel state: Running
Start automatically: Yes
xray state: Running

Please enter your selection [0-23]:

</code></pre>
<h4 id="enabling-bbr-bottleneck-bandwidth-and-round-trip-propagation-time">Enabling BBR (Bottleneck Bandwidth and Round-trip propagation time)</h4>
<p>To enable BBR using the 3X-UI panel, follow these steps:</p>
<ol>
<li>
<p>After running the <code>x-ui</code> command and accessing the menu, type <code>21</code> and press Enter. This corresponds to the “Enable BBR” option in the menu.</p>
</li>
<li>
<p>After selecting option <code>21</code>, you will be prompted to confirm your selection. Type <code>1</code> to confirm and enable BBR on your server.</p>
</li>
</ol>
<p>Enabling BBR can significantly improve network performance by optimizing the flow of data packets, leading to faster download and upload speeds, reduced buffering, and improved network responsiveness.</p>
<h4 id="ssl-certificate-management-with-lets-encrypt">SSL Certificate Management with Let’s Encrypt</h4>
<p>&lt;$&gt;[note]</p>
<p><strong>Note:</strong> If you don’t plan to use a domain name or prefer to handle SSL/TLS certificates manually, you can skip this step.</p>
<p>&lt;$&gt;</p>
<p>If you plan to use your server with a domain name and want to secure connections with SSL/TLS encryption, you can manage SSL certificates with Let’s Encrypt. This process involves obtaining and installing SSL certificates for your domains, ensuring secure communication between your server and clients.</p>
<p>To manage SSL certificates with Let’s Encrypt using the 3X-UI panel, follow these steps:</p>
<ol>
<li>
<p>After running the <code>x-ui</code> command and accessing the menu, select the “SSL Certificate Management” option (typically option <code>16</code>).</p>
</li>
<li>
<p>From the SSL Certificate Management menu, select option <code>1</code> to get SSL certificates for your domains.</p>
</li>
<li>
<p>After selecting option <code>1</code>, you will be prompted to enter your domain name. Type your domain name or subdomain and press Enter.</p>
</li>
<li>
<p>Next, you will be asked to choose which port to use. By default, port <code>80</code> is selected. If port <code>80</code> is already in use, you can choose another available port. Enter the desired port number and press Enter.</p>
</li>
<li>
<p>You need to note that these two addresses are marked in blue. You need them later in the panel to activate SSL/TLS.</p>
</li>
</ol>
<p>&lt;$&gt;[note]</p>
<p><strong>Note:</strong> II have marked the address you need for the panel with a blue color.</p>
<p>&lt;$&gt;</p>
<p><a href="https://github.com/icepolylol/v2ray/blob/3faefc2fe5702565fc47af98eaa5ad592596947c/asset/mark.png?raw=true" title="https://github.com/icepolylol/v2ray/blob/3faefc2fe5702565fc47af98eaa5ad592596947c/asset/mark.png?raw=true (Ctrl or Cmd-click to open)">https://github.com/icepolylol/v2ray/blob/3faefc2fe5702565fc47af98eaa5ad592596947c/asset/mark.png?raw=true</a></p>
<h2 id="step---4--connecting-web-panel-and-setting-up-vpn-without-domain">Step - 4 : Connecting Web Panel and Setting Up VPN Without Domain</h2>
<p><strong>Accessing the Web Panel:</strong></p>
<ul>
<li>
<p>Open a web browser on your local machine.</p>
</li>
<li>
<p>Enter the IP address of your server followed by the appropriate port (e.g., <code>https://your_server_ip:Your_port</code>) to access the 3X-UI web panel.</p>
</li>
<li>
<p><strong>Logging In:</strong></p>
</li>
</ul>
<p>Use the username and password you set during the initial configuration</p>
<ul>
<li>
<p><strong>Navigating to Inbounds:</strong></p>
<ul>
<li>Locate and click on the “Inbounds” section in the sidebar menu.</li>
</ul>
</li>
<li>
<p><strong>Adding a New Inbound:</strong></p>
<ul>
<li>Within the “Inbounds” section, click on the “Add Inbound” button with a green background.</li>
</ul>
</li>
<li>
<p><strong>Configuring Inbound Settings:</strong></p>
<ul>
<li>
<p>Choose the desired combination for the VPN connection. For simplicity, select <code>vless</code> as the protocol and <code>TCP</code> as the transmission protocol.</p>
</li>
<li>
<p>Enter a name for your connection (e.g., <code>MyVPNConnection</code>).</p>
</li>
<li>
<p>Specify a port number for the inbound connection (e.g., <code>8450</code>).</p>
</li>
</ul>
</li>
<li>
<p><strong>Setting Transmission Protocol:</strong></p>
<ul>
<li>Under “Transmission,” select <code>TCP</code> from the dropdown menu.</li>
</ul>
</li>
<li>
<p><strong>Configuring Additional Settings:</strong></p>
<ul>
<li>Optionally, you can set limits for Total Flow to manage bandwidth usage for the VPN connection.</li>
</ul>
</li>
<li>
<p><strong>Creating the VPN Connection:</strong></p>
<ul>
<li>After configuring the settings, click on the “Create” button to finalize the setup of the VPN connection.</li>
</ul>
</li>
</ul>
<h2 id="step---4--connecting-web-panel-and-setting-up-vpn-with-domain">Step - 4 : Connecting Web Panel and Setting Up VPN With Domain</h2>
<ol>
<li>
<p><strong>Accessing Panel Settings:</strong></p>
<ul>
<li>
<p>Log in to the 3X-UI web panel using your credentials.</p>
</li>
<li>
<p>Navigate to the “Panel Settings” section, typically located in the sidebar menu or settings menu.</p>
</li>
</ul>
</li>
<li>
<p><strong>General Settings:</strong></p>
<ul>
<li>Within the “Panel Settings,” locate and click on the “General” tab.</li>
</ul>
</li>
<li>
<p><strong>Configuring Domain and SSL:</strong></p>
<ul>
<li>
<p>In the “General” tab, you will find two fields related to domain and SSL configuration:</p>
<ul>
<li>
<p><strong>Domain Name:</strong> Enter your domain name (e.g., <code>example.com</code>) in the designated field.</p>
</li>
<li>
<p><strong>SSL Certificate:</strong> Upload or specify the path to your SSL certificate files. This typically includes the SSL certificate (<code>fullchain.pem</code>) and private key (<code>privkey.pem</code>) files.</p>
</li>
<li>
<p><a href="https://github.com/icepolylol/v2ray/blob/master/asset/address.png" title="https://github.com/icepolylol/v2ray/blob/master/asset/address.png (Ctrl or Cmd-click to open)">https://github.com/icepolylol/v2ray/blob/master/asset/address.png</a></p>
</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>Saving Changes:</strong></p>
<ul>
<li>After entering the required information, click on the “Save” or “Apply Changes” button to save the configuration.</li>
</ul>
</li>
</ol>
<h3 id="creating-an-inbound-connection-with-tls-and-vless-protocol">Creating an Inbound Connection with TLS and vless Protocol:</h3>
<ul>
<li>
<p><strong>Creating a New Inbound:</strong></p>
</li>
<li>
<p>Click on the “Create Inbound” button to add a new inbound connection.</p>
</li>
<li>
<p>Click on the “Create Inbound” button to add a new inbound connection.</p>
</li>
<li>
<p><strong>Configuring Inbound Settings:</strong></p>
<ul>
<li>
<p><strong>Name:</strong> Enter a name for your inbound connection (e.g., <code>MyTLSvless</code>).</p>
</li>
<li>
<p><strong>Protocol:</strong> Choose <code>vless</code> as the protocol for the VPN connection.</p>
</li>
<li>
<p><strong>Transmission:</strong> Select <code>TCP</code> for transmission. Optionally, you can use <code>WebSocket</code> or <code>gRPC</code> for improved performance.</p>
</li>
<li>
<p><strong>Security:</strong> Choose <code>TLS</code> for secure communication.</p>
</li>
<li>
<p><strong>SNI (Server Name Indication):</strong> Enter your domain name (e.g., <code>example.com</code>) in the SNI field.</p>
</li>
</ul>
</li>
<li>
<p><strong>uTLS Configuration (Optional):</strong></p>
<ul>
<li>Specify the uTls setting based on your preferred browser (e.g., <code>firefox</code> or <code>chrome</code>).</li>
</ul>
</li>
<li>
<p><strong>Setting TLS Certificate for Panel:</strong></p>
<ul>
<li>
<p>Click on the “Set Cert for Panel” button to configure TLS certificate for the panel.</p>
</li>
<li>
<p>Ensure that valid SSL certificate files (<code>fullchain.pem</code> and <code>privkey.pem</code>) are uploaded or specified in the SSL configuration settings.</p>
</li>
</ul>
</li>
<li>
<p><strong>Finalizing the Configuration:</strong></p>
</li>
<li>
<p>After configuring the inbound settings, click on the “Create” button to finalize the setup of the inbound connection.</p>
</li>
<li>
<p><a href="https://github.com/icepolylol/v2ray/blob/master/asset/vlesstls.png" title="https://github.com/icepolylol/v2ray/blob/master/asset/vlesstls.png (Ctrl or Cmd-click to open)">https://github.com/icepolylol/v2ray/blob/master/asset/vlesstls.png</a></p>
<h2 id="step-5---downloading-and-installing-nekoray">Step 5 --Downloading and Installing NekoRay</h2>
</li>
<li>
<p>Downloading and Installing NekoRay</p>
</li>
</ul>
<p><strong>Update Package Lists:</strong></p>
<pre><code>sudo apt update
</code></pre>
<ul>
<li><strong>Install wget (if not already installed):</strong></li>
</ul>
<pre><code>sudo apt install wget
</code></pre>
<ul>
<li><strong>Download NekoRay Debian Package:</strong> Use <code>wget</code> to download the Debian package for NekoRay:</li>
</ul>
<pre><code>wget https://github.com/MatsuriDayo/nekoray/releases/download/3.26/nekoray-3.26-2023-12-09-debian-x64.deb
</code></pre>
<p><strong>Install NekoRay Package:</strong> Use <code>dpkg</code> to install the downloaded Debian package:</p>
<pre><code>sudo dpkg -i nekoray-3.26-2023-12-09-debian-x64.deb
</code></pre>
<ul>
<li>
<p><a href="https://github.com/icepolylol/v2ray/blob/master/asset/INSTALL.png" title="https://github.com/icepolylol/v2ray/blob/master/asset/INSTALL.png (Ctrl or Cmd-click to open)">https://github.com/icepolylol/v2ray/blob/master/asset/INSTALL.png</a></p>
</li>
<li>
<p><strong>GitHub Repository:</strong> Visit the <a href="https://github.com/MatsuriDayo/nekoray" title="https://github.com/MatsuriDayo/nekoray (Ctrl or Cmd-click to open)">NekoRay GitHub repository</a> for more information and updates.</p>
</li>
</ul>
<p>By following these steps, you will successfully download and install NekoRay on your Ubuntu system using the command line. Ensure that you have administrative privileges (<code>sudo</code>) to perform the installation.</p>
<h2 id="configuring-nekoray--firefox">Configuring Nekoray &amp; Firefox</h2>
<ol>
<li>
<p><strong>Access Panel Inbound Settings:</strong></p>
<ul>
<li>
<p>Open the panel interface in your web browser.</p>
</li>
<li>
<p>Navigate to the “Inbounds” tab.</p>
</li>
</ul>
</li>
<li>
<p><strong>Add Inbound Connection:</strong></p>
<ul>
<li>Click on the “+” (plus) button toexpand the list of existing configurations.</li>
</ul>
</li>
<li>
<p><strong>Copy NekoRay Configuration:</strong></p>
<ul>
<li>
<p>Choose the desired configuration within the list.</p>
</li>
<li>
<p>Click twice on the qr-code icon to copy the settings.</p>
</li>
</ul>
</li>
<li>
<p><strong>Paste Configuration in NekoRay:</strong></p>
<ul>
<li>
<p>Switch to your NekoRay client interface (e.g., terminal).</p>
</li>
<li>
<p>Press <code>Ctrl + V</code> (or right-click and select “Paste”) to paste the copied configuration.</p>
</li>
</ul>
</li>
<li>
<p><strong>Connect to Configuration:</strong></p>
<ul>
<li>
<p>Select the pasted configuration within the NekoRay interface.</p>
</li>
<li>
<p>Press <code>ENTER</code> (or follow the appropriate prompt) to establish the connection using the configured settings.</p>
</li>
</ul>
</li>
<li>
<p><strong>Open Firefox:</strong> Launch the Firefox web browser on your computer.</p>
</li>
<li>
<p><strong>Access Proxy Settings:</strong></p>
<ul>
<li>
<p>Click on the menu button (three horizontal lines) in the upper-right corner of the Firefox window.</p>
</li>
<li>
<p>Select “Preferences” (on macOS) or “Options” (on Windows/Linux) from the dropdown menu.</p>
</li>
</ul>
</li>
<li>
<p><strong>Navigate to Network Settings:</strong></p>
<ul>
<li>
<p>In the Preferences or Options window, scroll down and click on “General” on the left-hand sidebar.</p>
</li>
<li>
<p>Scroll down to the “Network Settings” section.</p>
</li>
</ul>
</li>
<li>
<p><strong>Configure Proxy Settings:</strong></p>
<ul>
<li>
<p>Under the “Network Settings” section, click on the “Settings…” button next to “Configure Proxy Access to the Internet.”</p>
</li>
<li>
<p>Choose the option for “Manual proxy configuration.”</p>
</li>
</ul>
</li>
<li>
<p><strong>Enter SOCKS Proxy Details:</strong></p>
<ul>
<li>
<p>In the “SOCKS Host” field, enter <code>localhost</code> or <code>127.0.0.1</code>.</p>
</li>
<li>
<p>Enter <code>2080</code> as the port number for the SOCKS proxy.</p>
</li>
</ul>
</li>
<li>
<p><strong>Apply Proxy Settings:</strong></p>
<ul>
<li>
<p>Check the box for “Proxy DNS when using SOCKS v5” if you want DNS requests to also go through the SOCKS proxy.</p>
</li>
<li>
<p>Click “OK” to save the proxy configuration settings.</p>
</li>
<li>
<p>Close the Preferences or Options window.</p>
</li>
<li>
<p><a href="https://github.com/icepolylol/v2ray/blob/master/asset/firefox.png" title="https://github.com/icepolylol/v2ray/blob/master/asset/firefox.png (Ctrl or Cmd-click to open)">https://github.com/icepolylol/v2ray/blob/master/asset/firefox.png</a></p>
</li>
<li>
<p><a href="https://github.com/icepolylol/v2ray/blob/master/asset/final.png" title="https://github.com/icepolylol/v2ray/blob/master/asset/final.png (Ctrl or Cmd-click to open)">https://github.com/icepolylol/v2ray/blob/master/asset/final.png</a></p>
</li>
</ul>
</li>
</ol>
<h2 id="conclusion">Conclusion</h2>
<p>In this tutorial, you have learned how to set up a powerful VPN solution using V2Ray and NekoRay on Ubuntu. By following the detailed steps provided, you can create secure inbound connections, configure NekoRay as a proxy, and seamlessly integrate your VPN setup with web browsers like Firefox.</p>
<p>Key takeaways from this tutorial include:</p>
<ul>
<li>
<p><strong>Installing V2Ray and NekoRay:</strong> You learned how to install and configure V2Ray and NekoRay on Ubuntu, enabling a robust VPN solution for secure internet browsing.</p>
</li>
<li>
<p><strong>Configuring Inbound Connections:</strong> Through the panel interface, you configured inbound connections and generated configuration settings for NekoRay.</p>
</li>
<li>
<p><strong>Setting up Firefox Proxy:</strong> You configured Firefox to use NekoRay as a SOCKS v5 proxy, ensuring that your browsing activity is routed securely through your VPN.</p>
</li>
</ul>
<p>By leveraging these technologies and configurations, you can enhance your online privacy and security while enjoying unrestricted internet access. Remember to refer to the documentation and community resources for ongoing support and troubleshooting as you explore and expand your VPN setup.</p>
<p>Thank you for following along with this tutorial. We hope you found it informative and empowering for creating your VPN infrastructure with V2Ray and NekoRay on Ubuntu. Happy browsing securely!</p>

