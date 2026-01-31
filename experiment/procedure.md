<h4>Introduction to Covert Channels</h4>

<img src="images/step1intro.png" alt="Introduction to Covert Channels - Initial Screen" style="max-width:80%;">

<ol>
  <li>At the <strong>top section of the screen</strong>, observe the <strong>Introduction to Covert Channels</strong> panel.</li>
  <li>In the <strong>left panel (High-Security Sender Process)</strong>:
    <ul>
      <li>Select a piece of classified information from the list.</li>
      <li>Click <strong>Attempt Data Transfer</strong>.</li>
    </ul>
  </li>
  <li>In the <strong>center panel (Access Control Enforcer)</strong>:
    <ul>
      <li>Observe that the request is evaluated according to the security policy.</li>
      <li>Note that the <strong>No Write Down</strong> rule is enforced and the request is blocked.</li>
    </ul>
  </li>
  <li>In the <strong>right panel (Low-Security Receiver Process)</strong>:
    <ul>
      <li>Observe that the incoming data displays <strong>NULL (WRITE DENIED)</strong>.</li>
    </ul>
  </li>
  <li>At the <strong>bottom of the screen</strong>, review the <strong>System Audit Log</strong>.</li>
  <li>Click <strong>Next: Covert Channel</strong> to proceed.</li>
</ol>

<img src="images/step2next.png" alt="Introduction to Covert Channels - Initial Screen" style="max-width:80%;">

<h4>1. Storage Covert Channel</h4>

<ul>
  <li>In the <strong>top navigation area</strong>, select the <strong>Storage Covert Channel</strong> option.<br>
    <img src="images/step3storage.png" alt="Storage Covert Channel - Main Screen" style="max-width:80%;">
  </li>
</ul>

<p><strong>Step 1: Sender Phase – Prepare and Start Transmission</strong></p>

<ul>
  <li>In the <strong>left panel (Sender – High-Level Process)</strong>:
    <ul>
      <li>Read the displayed sender instructions.</li>
      <li>Select a secret message from the <strong>Select Secret Message</strong> dropdown.</li>
      <li>Observe the <strong>ID to Binary Conversion</strong> displayed directly below the selection.<br>
        <img src="images/step4center.png" alt="Storage Covert Channel - Binary Conversion" style="max-width:80%;">
      </li>
    </ul>
  </li>
  <li>Click <strong>Start Covert Transmission</strong>.</li>
  <li>During transmission, monitor the <strong>Current Sender Action</strong> section in the left panel.
    <ul>
      <li>Note that:
        <ul>
          <li>A database <strong>INSERT</strong> operation represents bit <code>1</code>.</li>
          <li>A database <strong>DELETE</strong> operation represents bit <code>0</code>.</li>
        </ul>
      </li>
    </ul>
    <img src="images/step4Start.png" alt="Storage Covert Channel - Transmission Started" style="max-width:80%;">
  </li>
</ul>

<p><strong>Step 2: Visualization Phase – Observe Shared Storage and Logs</strong></p>

<ul>
  <li>In the <strong>center panel (Shared Storage Covert Channel Visualization)</strong>:
    <ul>
      <li>Observe the <strong>Shared Signal State Resource</strong>.</li>
      <li>The visualization clearly indicates whether a row is present (signaling bit <code>1</code>) or the table is empty (signaling bit <code>0</code>).</li>
    </ul>
  </li>
  <li>Below the visualization, monitor the <strong>Database Action Log</strong>, which records every covert channel operation (INSERT/DELETE) in chronological order.<br>
    <img src="images/stepvisualization.png" alt="Storage Covert Channel - Visualization" style="max-width:80%;">
  </li>
</ul>

<p><strong>Step 3: Receiver Phase – Decode and Recover the Message</strong></p>

<ul>
  <li>In the <strong>right panel (Receiver – Low-Level Process)</strong>:
    <ul>
      <li>Observe the database query result under <strong>Database Observation</strong>.</li>
      <li>Decode each bit by clicking <strong>Decode 1</strong> (when a row is present) or <strong>Decode 0</strong> (when the table is empty).<br>
        <img src="images/stepdecode.png" alt="Storage Covert Channel - Decoding" style="max-width:80%;">
      </li>
    </ul>
  </li>
  <li>Watch the decoded bits appear in the <strong>Decoded Bit Stream</strong> section.</li>
  <li>If a mismatch occurs, click <strong>Resume Decoding from Mismatch</strong> and continue.</li>
  <li>Upon completion, confirm that the system displays <strong>Transmission Complete</strong>, indicating successful recovery of the hidden message.<br>
    <img src="images/step5complete.png" alt="Storage Covert Channel - Transmission Complete" style="max-width:80%;">
  </li>
</ul>

<h4>2. Timing Covert Channel</h4>

<ul>
  <li>In the top navigation, select <strong>Timing Covert Channel</strong>.<br>
    <img src="images/timestep1.png" alt="Timing Covert Channel Interface" style="max-width:80%;">
  </li>
</ul>

<p><strong>Step 1: Sender – Encode and Start Transmission</strong></p>

<ul>
  <li>In the <strong>Sender (High-Level Process)</strong> panel:
    <ul>
      <li>Select a secret message from the dropdown.</li>
      <li>Configure the timing parameters:
        <ul>
          <li>Delay for bit <code>0</code></li>
          <li>Delay for bit <code>1</code></li>
          <li>Optional noise (jitter) to simulate real-world variability</li>
        </ul>
      </li>
      <li>Click <strong>Start Transmission</strong>.</li>
    </ul>
    <img src="images/timestep2.png" alt="Timing Covert Channel Sender Configuration" style="max-width:80%;">
  </li>
</ul>

<p><strong>Step 2: Visualization – Observe Timing Delays</strong></p>

<ul>
  <li>In the <strong>Shared Timing Covert Channel Visualization</strong> panel:
    <ul>
      <li>Observe the response time for each transmitted bit.</li>
      <li>Note how the timing pattern reveals the hidden information (longer or shorter delays correspond to bits <code>0</code> or <code>1</code>).</li>
    </ul>
    <img src="images/timevisualization.png" alt="Timing Covert Channel Visualization" style="max-width:80%;">
  </li>
</ul>

<p><strong>Step 3: Receiver – Decode and Recover the Message</strong></p>

<ul>
  <li>In the <strong>Receiver (Low-Level Process)</strong> panel:
    <ul>
      <li>Compare each observed response time against the expected delay ranges for bits <code>0</code> and <code>1</code>.</li>
      <li>Manually classify each bit by clicking <strong>0</strong> or <strong>1</strong> based on the measured timing.<br>
        <img src="images/timestep3.png" alt="Timing Covert Channel Receiver Decoding" style="max-width:80%;">
      </li>
    </ul>
  </li>
  <li>Monitor the <strong>Decoded Sequence</strong>, which updates in real time as each bit is classified.</li>
  <li>Continue until all bits have been processed.</li>
  <li>Upon completion:
    <ul>
      <li>Observe the final <strong>Decoded Message</strong> displayed.</li>
      <li>Review the <strong>Timing Channel Log</strong> to analyze how timing variations enabled the transmission of hidden data.</li>
    </ul>
    <img src="images/timestep4.png" alt="Timing Covert Channel - Decoded Message" style="max-width:80%;">
  </li>
</ul>