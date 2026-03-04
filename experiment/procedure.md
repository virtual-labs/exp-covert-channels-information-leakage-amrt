<h4>Introduction to Covert Channels</h4>

<img src="images/covert1.png" alt="Introduction to Covert Channels - Initial Screen" style="max-width:80%;">

<ol>
  <li>At the <strong>top section of the screen</strong>, observe the <strong>Introduction to Covert Channels</strong> panel.</li>

  <li>In the <strong>left panel (High-Security Process)</strong>:
    <ul>
      <li>Select a piece of classified information from the list.</li>
      <li>Click <strong>Attempt Data Transfer</strong>.</li>
    </ul>
  </li>

  <li>In the <strong>center panel (System Security Engine)</strong>:
    <ul>
      <li>Observe that the request is evaluated according to the security policy.</li>
      <li>Note that the <strong>No Write Down</strong> rule is enforced and the request is blocked.</li>
    </ul>
  </li>

  <li>In the <strong>right panel (Low-Security Process)</strong>:
    <ul>
      <li>Observe that the incoming data displays <strong>NULL (WRITE DENIED)</strong>, indicating that the security policy has blocked the primary transfer mechanism.</li>
    </ul>
  </li>

  <li>At the <strong>bottom section of the screen</strong>, review the <strong>Security System Logs</strong> to observe how the system records the blocked attempt.</li>

  <li>Click <strong>Next: Proceed to Covert Channel Simulation</strong> to start analyzing how to circumvent this policy.</li>
</ol>

<img src="images/covert2.png" alt="Proceed to Covert Channel Simulation" style="max-width:80%;">



<h4>1. Storage Covert Channel</h4>

<ul>
  <li>In the <strong>top navigation area</strong>, select the <strong>Storage Covert Channel</strong>
</ul>

<img src="images/storage1.png" alt="Storage Covert Channel - Main Screen" style="max-width:80%;">

<p><strong>Step 1: Sender Phase – Prepare and Start Transmission</strong></p>

<ul>
  <li>In the <strong>left panel (Data Sender (High Security))</strong>:
    <ul>
      <li>Select a secret message from the dropdown.</li>
      <li>Observe the binary conversion displayed below the selection.</li>
      <li>Click <strong>Start Hidden Message Sending</strong>.</li>
      <li>During transmission, monitor the <strong> Active Signaling</strong> in the sender panel.</li>
    </ul>
  </li>
  <li>Note that:
    <ul>
      <li>Creating a file or record represents bit <code>1</code>.</li>
      <li>Deleting a file or record represents bit <code>0</code>.</li>
    </ul>
  </li>
</ul>

<img src="images/storage2.png" alt="Storage Covert Channel - Transmission Started" style="max-width:60%;">



<p><strong>Step 2: Visualization Phase – Observe Shared Storage</strong></p>

<ul>
  <li>In the <strong>center panel (Storage Simulation Visualization)</strong>:
    <ul>
      <li>Observe the representation of the shared resource over time.</li>
      <li>The visualization updates to show whether the shared file exists (representing bit <code>1</code>) or empty/not present (representing bit <code>0</code>).</li>
    </ul>
  </li>
  <li>Below the visuals, monitor the <strong>System Activity Logs</strong>. Observe how the sender modifies the shared storage state without direct communication with the receiver.</li>
</ul>

<img src="images/storage3.png" alt="Storage Covert Channel Visualization" style="max-width:80%;">



<p><strong>Step 3: Receiver Phase – Decode and Recover the Message</strong></p>

<ul>
  <li>In the <strong>right panel (Data Receiver (Low Security))</strong>:
    <ul>
      <li>Observe the shared storage status under <strong>Current Resource Check</strong>.</li>
      <li>Decode the message by determining if the storage exists in real-time.</li>
      <li>Click <strong>Decode as '1'</strong> when the item exists, or <strong>Decode as '0'</strong> when it is empty.</li>
    </ul>
  </li>
</ul>

<img src="images/storage4.png" alt="Storage Covert Channel - Transmission Complete" style="max-width:80%;">

<ul>
  <li>Observe the decoded bits appearing chronologically and completing the text translation in the <strong>Decoded Message stream</strong>.</li>
  <li>Verify that the final hidden message is recovered based solely on checking the shared resource over interval time ticks.</li>
</ul>



<h4>2. Timing Covert Channel</h4>

<ul>
  <li>In the top navigation bar, select the <strong>Timing Channel</strong> option.</li>
</ul>

<img src="images/timing1.png" alt="Timing Covert Channel Interface" style="max-width:80%;">

<p><strong>Step 1: Sender Phase – Encode and Start Transmission</strong></p>

<ul>
  <li>In the <strong>left panel (Data Sender (High Security))</strong>:
    <ul>
      <li>Select a secret message from the dropdown list.</li>
      <li>Configure the delay times (in milliseconds) used to represent binary bits under <strong>1. Message and Delay Parameters</strong>.</li>
      <li>For instance, set a short delay for <code>0</code> and a long delay for <code>1</code>. You can also specify random jitter under <strong>2. Add Random System Noise</strong>.</li>
      <li>Click <strong>Start Hidden Message Sending</strong>.</li>
    </ul>
  </li>
</ul>

<img src="images/timing2.png" alt="Timing Covert Channel Sender Configuration" style="max-width:60%;">



<p><strong>Step 2: Visualization Phase – Observe Timing Delays</strong></p>

<ul>
  <li>In the <strong>center panel (Timing Visualization and Action Logs)</strong>:
    <ul>
      <li>Observe the visualization showing computing operations taking varying amounts of time according to the bit sent.</li>
      <li>Notice how the HIGH process intentionally executes for a longer or shorter time, creating measurable delays in CPU usage for the current bit.</li>
    </ul>
  </li>
</ul>

<img src="images/timing3.png" alt="Timing Covert Channel Visualization" style="max-width:80%;">



<p><strong>Step 3: Receiver Phase – Decode and Recover the Message</strong></p>

<ul>
  <li>In the <strong>right panel (Data Receiver (Low Security))</strong>:
    <ul>
      <li>Monitor the measured time of operations dynamically recorded in milliseconds under <strong>Latest System Activity</strong>.</li>
      <li>Based on the duration, deduce which bit was sent by the HIGH process.</li>
      <li>Press <strong>Decode as '0'</strong> when a short delay is observed, and <strong>Decode as '1'</strong> when a long delay is observed.</li>
    </ul>
  </li>
</ul>

<img src="images/timing4.png" alt="Timing Covert Channel Receiver Decoding" style="max-width:80%;">

<ul>
  <li>Continue until all bits are successfully captured.</li>
  <li>Monitor the <strong>Decoding Accuracy & Stats</strong> below the panels to track how many bits correctly match the intended message.</li>
  <li>The final secret text and statistics are displayed when the entire sequence is complete.</li>
</ul>