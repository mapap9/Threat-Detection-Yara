<h1>Threat Detection with Yara</h1>

<h2>Description</h2>
A walkthrough guide for Yara
<br />

<h2>Environments Used </h2>

- <b>Ubuntu</b>
- <b>VMWare</b>

<h2>Walk-through:</h2>

<p align="center">
<h2>1. Installing and Compiling Yara </h2>
<br/>
<b>Open the browser in the Ubuntu virtual machine, then navigate to the official GitHub releases page for YARA: https://github.com/VirusTotal/yara/releases </b>
<br />
<br />
<img src="images/3.png" height="80%" width="80%" alt=""/>
<b>Download the YARA source archive (e.g., yara-4.5.5.tar.gz or the latest release) into the Downloads directory.</b>
<br />
<br />
<img src="images/4.png" height="80%" width="80%" alt=""/>
<img src="images/5.png" height="80%" width="80%" alt=""/>
<b>Open a terminal and change to the Downloads directory</b>
<br />
<br />
<b>Extract the archive and enter the extracted directory (adjust the filenames to match the version you downloaded):
tar -zxf yara-4.5.5.tar.gz 
cd yara-4.5.5
</b>
<br />
<br />
<b>
You should now be inside the yara-4.5.5 directory.
</b>
<br />
<br />
<b>Install the required build tools:
sudo apt-get install automake libtool make gcc pkg-config
</b>
<br />
<br />
<img src="images/6.png" height="80%" width="80%" alt=""/>
<b>After installation, generate the build system:
./bootstrap.sh
</b>
<br />
<br />
<img src="images/7.png" height="80%" width="80%" alt=""/>
<img src="images/8.png" height="80%" width="80%" alt=""/>
<b>Configure the build (OpenSSL will be detected automatically and crypto features enabled if present): 
./configure
</b>
<br />
<br />
<img src="images/9.png" height="80%" width="80%" alt=""/>
<img src="images/10.png" height="80%" width="80%" alt=""/>
<b>Run the build:
make
</b>
<br />
<br />
<img src="images/11.png" height="80%" width="80%" alt=""/>
<b>Wait for the compilation to complete successfully.
Install YARA system-wide:
Sudo make install
</b>
<br />
<br />
<img src="images/12.png" height="80%" width="80%" alt=""/>
<img src="images/13.png" height="80%" width="80%" alt=""/>
<b>This installs the binaries (yara, yarac) and the shared library (libyara.so), typically under /usr/local.
Verify the installation:
Yara --version
</b>
<br />
<br />
<img src="images/14.png" height="80%" width="80%" alt=""/>
<b>Run the test suite to verify the build and configuration:
Make check
</b>
<br />
<br />
<img src="images/15.png" height="80%" width="80%" alt=""/>
<img src="images/16.png" height="80%" width="80%" alt=""/>
<b>Review the output for successful test results.</b>
<br />
<br />
  
<h2>2. Installing a module in Yara </h2>
<br/>
<b>I will use the Magicmodule in an upcoming experiment. Follow these steps to install the module when prompted in that section.
Install the required dependency:
sudo apt-get update 
sudo apt-get install libmagic-dev
sudo apt-get install libssl-dev
</b>
<br />
<br />
<img src="images/17.png" height="80%" width="80%" alt=""/>
<img src="images/21.png" height="80%" width="80%" alt=""/>
<b>Clean the previous build:
Make clean
</b>
<br />
<br />
<img src="images/18.png" height="80%" width="80%" alt=""/>
<b>Reconfigure with the Magic module enabled:
./configure –enable-magic
</b>
<br />
<br />
<img src="images/19.png" height="80%" width="80%" alt=""/>
<b>(If you also want crypto support:)
./configure --with-crypto --enable-magic
</b>
<br />
<br />
<img src="images/20.png" height="80%" width="80%" alt=""/>
<b>Rebuild and reinstall:
make 
</b>
<br />
<br />
<img src="images/22.png" height="80%" width="80%" alt=""/>
<b>
sudo make install
</b>
<br />
<br />
<img src="images/23.png" height="80%" width="80%" alt=""/>
<b>Verify the Magic module is available:
yara -M
</b>
<br />
<br />
<img src="images/24.png" height="80%" width="80%" alt=""/>
<b>The Magic module is now enabled.
Begin the experiment — follow along with the steps below to proceed.
</b>
<br />
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
