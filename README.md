<p align="center">
  <img width="300" height="168" alt="68747470733a2f2f692e696d6775722e636f6d2f705535413538532e706e67"  src="https://github.com/user-attachments/assets/a80f144b-2015-408e-bcc8-c8e08c18cedf" />


</p>

<div align="center">
<hr>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>

<p>
In this project, we use Wireshark to examine traffic between Azure Virtual Machines, focusing on different protocols such as ICMP, SSH, DHCP, DNS, and RDP. We also experiment with Network Security Groups (NSGs) to control inbound and outbound traffic. This allows us to gain insight into how network traffic flows between virtual machines and how security rules can be used to restrict or permit specific types of traffic.
</p>

</div>

<hr>

<h2>Evan H. Yearwood - Portfolio Project</h2>

<h2>Environments and Technologies Used</h2>

<ul>
  <li>Microsoft Azure (Virtual Machines/Compute)</li>
  <li>Remote Desktop</li>
  <li>Command-Line Tools</li>
  <li>Network Protocols (SSH, RDP, DNS, DHCP, ICMP)</li>
  <li>Wireshark (Protocol Analyzer)</li>
</ul>

<h2>Operating Systems Used</h2>

<ul>
  <li>Windows 11 (25H2)</li>
  <li>Ubuntu Server 20.04</li>
</ul>

<hr>

<h2>Part 1: Create Resources</h2>

<ol>
  <li>Create a Resource Group.</li>

  <li>Create a Windows 11 Virtual Machine (VM).
    <ol type="a">
      <li>While creating the VM, select the Resource Group created earlier.</li>
      <li>Allow the creation of a new Virtual Network (Vnet) and Subnet for the VM.</li>
    </ol>
  </li>

  <li>Create a Linux (Ubuntu) Virtual Machine (VM).
    <ol type="a">
      <li>Select the previously created Resource Group and Vnet for this VM.</li>
    </ol>
  </li>

  <li>Observe the topology and details of your Virtual Network using Azure Network Watcher.</li>
</ol>

<hr>

<h2>Part 2: Observe ICMP Traffic</h2>

<ol>
  <li>Connect to the Windows 11 VM using Remote Desktop.</li>

  <li>Install Wireshark within the Windows 11 VM.</li>

  <li>Open Wireshark and apply a filter to capture only ICMP traffic (used for ping commands).</li>

  <li>Retrieve the private IP address of the Ubuntu VM and attempt to ping it from the Windows 11 VM.
    <ul>
      <li>Observe the ping requests and replies in Wireshark.</li>
    </ul>
  </li>

  <li>From the Windows 11ping www.google.com VM, open Command Prompt or PowerShell and ping a public website (such as www.google.com).
    <ul>
      <li>Observe the public ping traffic in Wireshark.</li>
    </ul>
  </li>

  <li>Initiate a continuous ping from the Windows 10 VM to the Ubuntu VM.</li>

  <li>In the Azure portal, access the Network Security Group (NSG) assigned to the Ubuntu VM and disable inbound ICMP traffic.
    <ul>
      <li>Observe how the ICMP traffic stops in Wireshark and the command line due to the blocked traffic.</li>
    </ul>
  </li>

  <li>Re-enable ICMP traffic in the NSG for the Ubuntu VM.
    <ul>
      <li>Observe the ICMP traffic start working again in Wireshark and on the command line.</li>
    </ul>
  </li>

  <li>Stop the continuous ping activity from the Windows 10 VM.</li>
</ol>

<hr>

<h2>Part 3: Observe SSH Traffic</h2>

<ol>
  <li>In Wireshark, apply a filter to capture SSH traffic.</li>

  <li>From the Windows 10 VM, establish an SSH connection to the Ubuntu VM using its private IP address.
    <ul>
      <li>Type commands (e.g., username, password) into the SSH session and observe the SSH traffic in Wireshark.</li>
      <li>Exit the SSH session by typing exit and pressing Enter.</li>
    </ul>
  </li>
</ol>

<hr>

<h2>Part 4: Observe DHCP Traffic</h2>

<ol>
  <li>In Wireshark, apply a filter to capture DHCP traffic.</li>

  <li>From the Windows 10 VM, attempt to request a new IP address using the command <code>ipconfig /renew</code>.
    <ul>
      <li>Observe the DHCP traffic in Wireshark as the VM communicates with the DHCP server to renew its IP address.</li>
    </ul>
  </li>
</ol>

<hr>

<h2>Part 5: Observe DNS Traffic</h2>

<ol>
  <li>In Wireshark, apply a filter to capture DNS traffic.</li>

  <li>From the Windows 10 VM, use the <code>nslookup</code> command to resolve the IP addresses of websites like google.com and disney.com.
    <ul>
      <li>Observe the DNS query and response traffic in Wireshark.</li>
    </ul>
  </li>
</ol>

<hr>

<h2>Part 6: Observe RDP Traffic</h2>

<ol>
  <li>In Wireshark, apply a filter to capture RDP traffic (using the filter <code>tcp.port == 3389</code>).</li>

  <li>Observe the continuous stream of RDP traffic between your local machine and the Windows 10 VM.
    <ul>
      <li>This constant stream is because RDP continuously transmits data to keep the live remote session active.</li>
      <li>The protocol constantly sends data, even when there is no specific user activity, to maintain the connection and update the screen in real time.</li>
    </ul>
  </li>
</ol>

<hr>

<h2>Conclusion</h2>

<p>
In this lab, we explored different types of network traffic between two Azure Virtual Machines, using Wireshark to analyze protocols such as ICMP, SSH, DHCP, DNS, and RDP. We also experimented with Network Security Groups to control the flow of ICMP traffic and observed how security settings can affect network behavior. By completing these exercises, we gained insight into how network traffic flows between virtual machines in Azure and how network security controls can be implemented to manage this traffic effectively.
</p>
