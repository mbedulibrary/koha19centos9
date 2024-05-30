<h1>ANSIBLE PLAYBOOK FOR CENTOS 8 AND KOHA 19.11</h1> 
<h3>(based on https://github.com/nemobis/beic-koha)</h3>

<ol>
  <li>Install Core CentOS 8 – Choose Server software package and select Basic Web in right column, Connect to Network, set time zone, make partitions as needed, set root password and create Admin user (koha) </li>
  <li>Update CentOS – sudo dnf -y update</li>
  <li>Enable EPEL Repo – sudo dnf -y install epel-release</li>
  <li>Enable PowerTools Repo – sudo dnf config-manager --set-enabled PowerTools</li>
  <li>Update Install – sudo dnf -y update</li>
  <li>Create group koha and add koha (user) to koha and apache groups
    <ul>
      <li>sudo usermod -aG koha koha</li>
      <li>sudo usermod -aG apache koha</li>
    </ul>
  </li>
  <li>Install Ansible - sudo dnf -y install ansible</li>
  <li>Clone or Download ansible playbook</li>
  <li>Go to Download Location of ansible playbook</li>
  <li>Run Ansible - sudo ansible-playbook koha.yml –u koha –i inventory.ini --connection local</li>
  <li>Secure MySQL Database - sudo mysql_secure_installation</li>
  <li>Find IP address of install server or localhost on port 8080 (localhost:8080) and begin web installation (username: kohaadmin password:katikoan)</li>
  <li>Go to About Koha and update required Perl modules manually with cpanm (ex:sudo cpanm Module::Name)</li>
  <li>Start and enable memcached at boot:
    <ul>
      <li>sudo systemctl start memcached</li>
      <li>sudo systemctl enable memcached</li>
    </ul>
  </li>
</ol>
<p><strong>NOTE: To rebuild zebra - sudo -u koha ./rebuild_zebra.pl -b -a -r -v</strong> - Won't break permissions which will break regular zebra reindexing.</p>
