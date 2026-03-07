

Covert channels are unintended communication mechanisms through which information can leak in a computer system without using authorized data transfer paths. Unlike normal communication channels that follow defined system policies and access controls, covert channels exploit shared system resources or observable system behaviors to transmit information indirectly.

Such channels do not rely on authorized message passing mechanisms. Instead, they enable a sender process and a receiver process to exchange information through indirect signals such as changes in system state or variations in execution time.

Covert channels are an important concern in **information leakage analysis and security modeling**, as they demonstrate how sensitive data may be exposed even when access control mechanisms and security policies are correctly enforced.

Based on the method used to transmit hidden information, covert channels are broadly classified into two categories:

- **Storage Covert Channels**
- **Timing Covert Channels**


#### Storage Covert Channels

Storage covert channels enable information leakage by modifying the state of a shared storage resource that is accessible or observable by multiple processes. This shared resource is often referred to as a **Shared Signal State Resource**.

In this type of channel:

- The **sender process** encodes information by changing the state of a shared resource.
- The **receiver process** decodes the information by observing those state changes.

Information is not explicitly transmitted through standard communication mechanisms. Instead, it is inferred from changes in the **presence, absence, or value** of the shared resource.

Typical shared storage resources include:

- Files
- Database entries
- Memory locations
- Permission flags
- System variables

In this experiment, the storage covert channel is simulated using a **shared database table**. The sender encodes binary information by modifying the state of the table, for example by **creating or deleting a record**. The receiver process decodes the transmitted information by checking whether the record exists or not.

This simulation demonstrates how unintended information leakage can occur through shared storage resources without direct communication between processes.



#### Timing Covert Channels

Timing covert channels enable information leakage by manipulating the **time taken to perform system operations**. In this method, the sender process encodes information by introducing deliberate delays or variations in execution time, while the receiver process decodes the information by measuring and analyzing these timing differences.

Timing covert channels exploit normal system behaviors such as:

- Processing delays
- CPU scheduling effects
- Response times
- Resource contention

Since such timing variations can naturally occur in real systems, timing-based covert channels are often difficult to detect and analyze.

In this experiment, the timing covert channel is simulated by introducing **controlled delays during system operations**. Different delay durations represent different binary values.

For example:

| Delay Duration | Binary Value |
|---------------|--------------|
| Short delay   | 0 |
| Long delay    | 1 |

The receiver process measures the execution time of system operations and compares it with predefined thresholds to infer the transmitted information.

System operations are also **logged during the experiment** to support the inference of hidden data transmission and to analyze the characteristics of timing-based information leakage.


