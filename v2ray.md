---


---

<h1 id="installing-v2ray-on-ubuntu-22.04">Installing V2Ray on Ubuntu 22.04</h1>
<h3 id="introduction">Introduction</h3>
<p>In the realm of proxy software, V2Ray stands out as a versatile and efficient tool for routing internet traffic securely. With its advanced features and robust performance, V2Ray is a popular choice among users seeking to enhance their privacy and circumvent online restrictions.</p>
<p>This tutorial aims to guide users through the process of installing V2Ray on Ubuntu 22.04, ensuring a seamless setup procedure regardless of the user’s level of experience. By following the steps outlined in this tutorial, readers will gain access to the powerful capabilities of V2Ray, unlocking a plethora of possibilities for secure internet browsing and network management.</p>
<h2 id="prerequisites">Prerequisites</h2>
<p>Before proceeding with the installation of V2Ray on Ubuntu 22.04, ensure that you have the following prerequisites in place:</p>
<ol>
<li>
<p><strong>Ubuntu 22.04:</strong> Ensure that you have a clean installation of Ubuntu 22.04 on your server or virtual machine.</p>
</li>
<li>
<p><strong>Root Access:</strong> You’ll need root access or a user account with sudo privileges to execute commands and install packages on the Ubuntu system.</p>
</li>
<li>
<p><strong>Domain (Optional):</strong> While not mandatory, having a domain for your V2Ray server allows you to utilize TLS (Transport Layer Security) for enhanced security. If you choose to use a domain, ensure that it is properly configured and points to your server’s IP address.</p>
</li>
<li>
<p><strong>Cloudflare Account (Optional):</strong> If you opt to use a domain for your V2Ray server, having a Cloudflare account is recommended. Cloudflare offers additional security features and can help improve the performance and reliability of your server by acting as a CDN (Content Delivery Network) and providing DDoS protection.</p>
</li>
<li>
<p><strong>V2Ray Client:</strong> To connect to the V2Ray server, you’ll need a V2Ray client installed on your device. For Windows, you can use clients like v2rayn or nekoray. For mobile devices, you can use a client like v2rayng.</p>
</li>
</ol>
<p>With these prerequisites fulfilled, you’ll be ready to proceed with the installation of V2Ray on Ubuntu 22.04. If you opt to use a domain and Cloudflare, your V2Ray setup will benefit from enhanced security and performance features.</p>
<h3 id="ssh-access-to-your-server">SSH Access to Your Server</h3>
<p>SSH (Secure Shell) is a protocol that allows you to securely access and manage your server remotely. Before you can install V2Ray on your Ubuntu 22.04 server, you’ll need to connect to it via SSH.</p>
<h4 id="step-1-open-terminal-linuxmac-or-putty-windows">Step 1: Open Terminal (Linux/Mac) or PuTTY (Windows)</h4>
<ul>
<li>
<p><strong>Linux/Mac Users:</strong> Open the terminal application on your local machine. You can usually find it in your applications menu or by searching for “Terminal.”</p>
</li>
<li>
<p><strong>Windows Users:</strong> Download and install PuTTY, a popular SSH client for Windows. You can download PuTTY from the official website: [PuTTY Download Page](<a href="https://www.putty.org/" title="https://www.putty.org/ (Ctrl or Cmd-click to open)">https://www.putty.org/</a>)</p>
</li>
</ul>
<h4 id="step-2-connect-to-your-server">Step 2: Connect to Your Server</h4>
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
<ul>
<li><strong>Windows Users (PuTTY):</strong> Open PuTTY and enter the IP address of your server in the “Host Name (or IP address)” field. Leave the port as default (22) and click “Open” to start the SSH connection.</li>
</ul>
<h4 id="step-3-enter-your-password">Step 3: Enter Your Password</h4>
<ul>
<li>After initiating the SSH connection, you’ll be prompted to enter your password. Type your password carefully (note: no characters will appear on the screen as you type), then press Enter.</li>
</ul>
<h4 id="step-4-verify-connection">Step 4: Verify Connection</h4>
<ul>
<li>Once you’ve entered the correct password, you should be logged into your Ubuntu 22.04 server via SSH. You’ll see a command line interface, indicating that you now have remote access to your server.</li>
</ul>
<p>Congratulations! You’ve successfully connected to your Ubuntu 22.04 server via SSH. You’re now ready to proceed with the installation of V2Ray. If you encounter any issues during the SSH connection process, double-check your server’s IP address, username, and password.</p>
<p>Certainly, let’s modify the installation process to include prompts for username, password, and port, and let’s choose a custom port for added security:</p>
<h3 id="step-5-install-3x-ui-panel">Step 5: Install 3X-UI Panel</h3>
<p>3X-UI is a user-friendly panel that simplifies server management tasks. To install 3X-UI on your Ubuntu 22.04 server, follow these steps:</p>
<ul>
<li>
<p>Open a terminal window on your Ubuntu 22.04 server. If you’re accessing your server via SSH, you can use the terminal application on your local machine.</p>
</li>
<li></li>
<li>
<p>Run the following command to update the package lists for upgrades and new package installations, and then upgrade the installed packages to their latest versions:</p>
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
<h3 id="step-6-accessing-3x-ui-panel">Step 6: Accessing 3X-UI Panel</h3>
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
<p>&lt;$&gt;[note]</p>
<p><strong>Note:</strong> II have marked the address you need for the panel with a blue color.</p>
<p>&lt;$&gt;<br>
<img src="https://github.com/icepolylol/v2ray/blob/3faefc2fe5702565fc47af98eaa5ad592596947c/asset/mark.png" alt="enter image description here"></p>
</li>
</ol>

