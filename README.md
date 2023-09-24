<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
In this tutorial we’ll outline the prerequisites and installation for osTicket, an open-source help desk and ticketing system.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
  
<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>
  <ul>
    <li>Internet Information Services</li>
  </ul>
  <ul>
    <li>PHP Manager for IIS</li>
  </ul>
  <ul>
    <li>Rewrite Module</li>
  </ul>
  <ul>
    <li>PHP 7.3.8</li>
  </ul>
  <ul>
    <li>Microsoft Visual C++ Redistributable</li>
  </ul>
  <ul>
    <li>MySQL 5.562</li>
  </ul>
  <ul>
    <li>HeidiSQL</li>
  </ul>
  <h2>Installation Steps</h2>
  <h3>1. Create a Windows 10 Virtual Machine in Azure</h3>
  <ul>
    <li>Navigate to the Azure portal and create a new virtual machine (VM) within your current subscription.</li>
  </ul>
  <ul>
    <li>To hold the VM and its assorted components, under “Project Details” create a new resource group named “RG-1.”</li>
  </ul>
  <ul>
    <li>Name your new VM “osTicket-VM.”</li>
  </ul>
  <img src="https://github.com/amaraphi/osticket-prereq/assets/144752187/712ad8d5-5257-4f2b-9d99-85842bfa63bb"/>

  <ul>
    <li>Image and Size Selections
      <ul>
        <li>Image: “Windows 10 Pro.”</li>
      </ul>
      <ul>
        <li>Size: 2-4 vCPUs</li>
      </ul>
    </li>
  </ul>
  <ul>
    <li>Create a username and password.</li>
  </ul>
  <ul>
    <li>Select the Networking tab. Confirm that a new virtual network, or VNet, is being created along with the VM.</li>
  </ul>
<img src="https://github.com/amaraphi/osticket-prereq/assets/144752187/7d67ba6d-083a-4095-8795-9330d46acbcb"/>


  <ul>
    <li>Click “Confirm and Create.”*</li>
  </ul>
  <ul>
    <li>Return the main portal and navigate to Resource Groups. Select the RG-1 resource group you have just created, confirming that your virtual machine, virtual network and their assorted components are within this group.</li>
  </ul>
  <h3>2. Install and Enable Internet Information Services (IIS)</h3>
  <ul>
    <li>While in your resource group, click on your VM-osTicket virtual machine and copy the public IP address displayed.</li>
  </ul>
 <img src="https://github.com/amaraphi/osticket-prereq/assets/144752187/b169b202-c96f-4967-81f2-0417a153b535"/>

  <ul>
    <li>In your computer’s task bar, search for and open Windows Remote Desktop</li>
  </ul>
  <ul>
    <li>Log into your VM using its public IP address and the username and password you created.</li>
  </ul>
  <ul>
    <li>Once you’ve logged in to your VM, use the task bar to search for the Control Panel.</li>
  </ul>
  <ul>
    <li>Click on Programs —&gt; Turn Windows Features on or Off</li>
  </ul>
  <ul>
    <li>Scroll down to Internet Information Services and check/enable the following:
      <ul>
        <li>World Wide Wide Web Services —&gt; Application Development Features —&gt;
          <ul>
            <li>CGI</li>
          </ul>
          <ul>
            <li>Common HTTP Features</li>
          </ul>
        </li>
      </ul>
      <ul>
        <li>Web Management Tools
          <ul>
            <li>IIS Management Console</li>
          </ul>
        </li>
      </ul>
    </li>
  </ul>
  <ul>
    <li>
      <strong>To check to confirm that the IIS server has been enabled:</strong>
      <ul>
        <li>Open Microsoft Edge (or any other browser) within your VM.</li>
      </ul>
      <ul>
        <li>In the address bar, enter the loopback address: 127.0.0.1</li>
      </ul>
      <ul>
        <li>You should see the IIS homepage.</li>
      </ul>
    </li>
  </ul>
  <h3>3. Install <a href="https://www.bing.com/ck/a?!&amp;&amp;p=b9535742e0beff47JmltdHM9MTY5NTQyNzIwMCZpZ3VpZD0wNGQ0ODZiMC03MTM3LTZiOTQtMTM3Ni05NDE2NzA4MDZhNGImaW5zaWQ9NTIwOQ&amp;ptn=3&amp;hsh=3&amp;fclid=04d486b0-7137-6b94-1376-941670806a4b&amp;psq=php+manager+for+iis&amp;u=a1aHR0cHM6Ly93d3cuaWlzLm5ldC9kb3dubG9hZHMvY29tbXVuaXR5LzIwMTgvMDUvcGhwLW1hbmFnZXItMTUwLWZvci1paXMtMTA&amp;ntb=1">PHP Manager for IIS</a></h3>
  <h3>4. Install the <a href="https://www.bing.com/ck/a?!&amp;&amp;p=4bea11af739c82f3JmltdHM9MTY5NTQyNzIwMCZpZ3VpZD0wNGQ0ODZiMC03MTM3LTZiOTQtMTM3Ni05NDE2NzA4MDZhNGImaW5zaWQ9NTIwNw&amp;ptn=3&amp;hsh=3&amp;fclid=04d486b0-7137-6b94-1376-941670806a4b&amp;psq=rewrite+module+download&amp;u=a1aHR0cHM6Ly93d3cuaWlzLm5ldC9kb3dubG9hZHMvbWljcm9zb2Z0L3VybC1yZXdyaXRl&amp;ntb=1">URL Rewrite Module</a></h3>
  <h3>5. Create a PHP directory in your VM’s C: drive</h3>
  <ul>
    <li>Navigate to your VM’s C: drive and create a new folder named “PHP.”</li>
  </ul>
  <h3>6. Install <a href="https://prototype.php.net/versions/7.3.8/">PHP 7.3.8</a> and unzip the contents into C:\PHP</h3>
  <ul>
    <li>After installing PHP, copy or extract all of the file contents into your new PHP directory.</li>
  </ul>
  <h3>7. Install <a href="https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170">Microsoft Visual C+ Redistributable</a></h3>
  <ul>
    <li>Step 1</li>
  </ul>
  <h3>8. Install <a href="https://www.bing.com/ck/a?!&amp;&amp;p=b2ea82429d6c43a1JmltdHM9MTY5NTQyNzIwMCZpZ3VpZD0wNGQ0ODZiMC03MTM3LTZiOTQtMTM3Ni05NDE2NzA4MDZhNGImaW5zaWQ9NTE5Mw&amp;ptn=3&amp;hsh=3&amp;fclid=04d486b0-7137-6b94-1376-941670806a4b&amp;psq=download+mysql&amp;u=a1aHR0cHM6Ly93d3cubXlzcWwuY29tL2Rvd25sb2Fkcy8&amp;ntb=1">mySQL</a></h3>
  <ul>
    <li>During installation select the following options:
      <ul>
        <li>Standard Setup</li>
      </ul>
      <ul>
        <li>Launch Configuration Wizard after install</li>
      </ul>
      <ul>
        <li>Standard Configuration</li>
      </ul>
    </li>
  </ul>
  <ul>
    <li>Important: create a password for the root directory that will be used to access our database.</li>
  </ul>
  <h3>9. Register PHP in IIS</h3>
  <ul>
    <li>Use your VM’s taskbar to search for IIS. Right click and select “Run as administrator.”</li>
  </ul>
  <ul>
    <li>Click on the PHP manager and select “Register new PHP version.”</li>
  </ul>
  <ul>
    <li>Navigate to your VM’s C:\PHP directory and select &lt;code&gt;php-cgi.exe&lt;/code&gt;. Click “OK.”</li>
  </ul>
  <ul>
    <li>After PHP has been registered, reload IIS within the management console.</li>
  </ul>
  <h3>10. Install osTicket</h3>
  <ul>
    <li>Install osTicket v1.15.8</li>
  </ul>
  <ul>
    <li>Copy or extract the “upload” folder to c:\inetpub\wwwroot</li>
  </ul>
  <ul>
    <li>While in the wwwroot folder, rename “upload” to “osTicket.”</li>
  </ul>
  <ul>
    <li>Return to the IIS management console and reload IIS.</li>
  </ul>
  <ul>
    <li>
      <strong>Test osTicket Installation</strong>
      <ul>
        <li>In the IIS management console, navigate to sites—&gt;Default—&gt; osTicket</li>
      </ul>
      <ul>
        <li>Click “Browse *.80.” This should open the osTicket installer in your browser.</li>
      </ul>
    </li>
  </ul>
  <h3>11. Enable PHP extensions</h3>
  <ul>
    <li>On the osTicket installer homepage, note that we still need to enable a few extensions.</li>
  </ul>
  <ul>
    <li>Go back to the IIS management console and navigate to sites—&gt;Default—&gt;osTicket.</li>
  </ul>
  <ul>
    <li>Click on PHP Manager —&gt; Enable or disable an extension.</li>
  </ul>
  <ul>
    <li>Enable the following extensions:
      <ul>
        <li>php_imap.dll</li>
      </ul>
      <ul>
        <li>php_intl.dll</li>
      </ul>
      <ul>
        <li>php_opache.dll</li>
      </ul>
    </li>
  </ul>
  <ul>
    <li>Back in your browser, refresh the osTicket installer page.</li>
  </ul>
  <h3>12. Rename ost-sampleconfig and assign new permissions</h3>
  <ul>
    <li>Navigate to the C:\inetpub\wwroot folder in your VM.</li>
  </ul>
  <ul>
    <li>Inside the osTicket folder, open the “include” folder.</li>
  </ul>
  <ul>
    <li>Find the file named “ost-sampleconfig.php.” Rename this file to “ost-config.php.”</li>
  </ul>
  <ul>
    <li>Next, we need to modify this configuration file so that any user can make changes:
      <ul>
        <li>Right click on ost-config.php.</li>
      </ul>
      <ul>
        <li>Click on Security —&gt; Advanced.</li>
      </ul>
      <ul>
        <li>Click Disable inheritance —&gt; Remove All</li>
      </ul>
      <ul>
        <li>When prompted, select “Remove all inherited permissions from this object.”</li>
      </ul>
      <ul>
        <li>Select a principal, then enter “Everyone” under “object name.” Click OK.</li>
      </ul>
      <ul>
        <li>Under “Basic Permissions,” select the following fields:
          <ul>
            <li>Full Control</li>
          </ul>
          <ul>
            <li>Modify</li>
          </ul>
          <ul>
            <li>Read & execute</li>
          </ul>
          <ul>
            <li>Read</li>
          </ul>
          <ul>
            <li>Write</li>
          </ul>
        </li>
      </ul>
      <ul>
        <li>Click OK.</li>
      </ul>
    </li>
  </ul>
  <h3>13. Use osTicket installer to create admin accounts</h3>
  <ul>
    <li>Back in your browser, your osTicket installer page should still be open.
      <ul>
        <li>If not, you can navigate back to that page by returning to the IIS management console and “Browse *:80” under sites —&gt; Default —&gt; osTicket.</li>
      </ul>
    </li>
  </ul>
  <ul>
    <li>Click Continue. Create a name, password and default email address for your help desk. This email address will receive all end-user tickets.</li>
  </ul>
  <ul>
    <li>Repeat these steps to create a username and password for your default admin account. Note: your admin email address should not be the same as your default Help Desk email address!</li>
  </ul>
  <h3>14. Install <a href="https://www.heidisql.com/">HeidiSQL</a> and initiate a new session</h3>
  <ul>
    <li>To finalize our osTicket installation, we need to connect to our mySQL database. To do this we’ll use Heidi, a []. Important: keep the browser with the osTicket installer open during these next steps!</li>
  </ul>
  <ul>
    <li>Download and open HeidiSQL.</li>
  </ul>
  <ul>
    <li>Click New —&gt; Session in root folder</li>
  </ul>
  <ul>
    <li>Enter the password you created during your mySQL setup.</li>
  </ul>
  <ul>
    <li>Once a session has been initiated, create a new database named “osTicket.”</li>
  </ul>
  <h3>15. Set up database</h3>
  <ul>
    <li>Back in the osTicket installer, scroll down to Database Settings.</li>
  </ul>
  <ul>
    <li>Enter the database name, which should be osTicket</li>
  </ul>
  <ul>
    <li>Enter the username and password for your mySQL database.</li>
  </ul>
  <ul>
    <li>Click “Install Now.”</li>
  </ul>
  <h3>16. Check admin and end users log in pages</h3>
  <ul>
    <li>To check to see if osTicket has been installed correctly, navigate to the following pages:
      <ul>
        <li>Admin and Agent Panel:</li>
      </ul>
      <ul>
        <li>End User Ticket Portal:</li>
      </ul>
    </li>
  </ul>
  <h3>17. Clean up: delete setup folder and set ost-config permissions to Read Only</h3>
  <ul>
    <li>For this final step, we need to do a bit of cleanup before we can use osTicket.</li>
  </ul>
  <ul>
    <li>Navigate to C:\inetpub\wwwroot\osTicket
      <ul>
        <li>Delete “setup”</li>
      </ul>
      <ul>
        <li>Navigate to the “include” folder and find the ost-config.php file
          <ul>
            <li>Under Security—&gt;Advanced, change basic permissions for “Everyone” to the following:
              <ul>
                <li>Read & execute</li>
              </ul>
              <ul>
                <li>Read</li>
              </ul>
            </li>
          </ul>
        </li>
      </ul>
    </li>
  </ul>
