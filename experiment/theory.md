


Covert channels are unintended communication mechanisms through which information can leak in a computer system without using authorized data transfer paths. Such channels do not rely on direct message passing; instead, they exploit shared system resources or observable system behavior to convey information indirectly. Covert channels are an important concern in information leakage analysis and security modeling, as they demonstrate how sensitive data may be exposed even when access control policies are correctly enforced.

Based on the method used to transmit hidden information, covert channels are broadly classified into two categories:

* **Storage Covert Channels**
* **Timing Covert Channels**



#### Storage Covert Channels

Storage covert channels enable information leakage by modifying the state of a shared storage resource, also referred to as a **Shared Signal State Resource**, that is accessible or observable by multiple processes. In this type of channel, a sender process encodes information by changing the state of the shared resource, while a receiver process decodes the information by observing those state changes.

Typical shared storage resources include files, database entries, memory locations, or permission flags. Information is not explicitly transmitted; instead, it is inferred from the presence, absence, or value of the shared resource.

In this experiment, the storage covert channel is simulated using a **shared database table**. The sender encodes binary information by altering the state of the table (for example, creating or removing a record), and the receiver decodes the information by observing whether the record exists. This simulation demonstrates how unintended information leakage can occur through shared storage resources without direct communication.



#### Timing Covert Channels

Timing covert channels enable information leakage by modulating the time taken to perform system operations. In this approach, the sender encodes information by introducing deliberate delays or variations in execution time, while the receiver decodes the information by measuring and analyzing these timing differences.

Timing covert channels exploit normal system behaviors such as processing delays, scheduling effects, or response times. Since such variations can occur naturally in real systems, timing-based channels are often difficult to detect and analyze.

In this experiment, the timing covert channel is simulated by introducing controlled delays during system operations. Different delay durations represent different binary values. The receiver infers the transmitted information by measuring execution time and comparing it against predefined thresholds. System operations are logged to support the inference of hidden data transmission and to analyze the characteristics of timing-based leakage.


