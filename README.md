# dpfsp_tool_transfer
Distributed Permutation Flow Shop Scheduling Problem with Eligibility Constraints and Qualification Options

# Instance Generation for Distributed Permutation Flowshop Scheduling Problem (DPFSP)

## Overview
This repository contains required information for generating instances for the Distributed Permutation Flowshop Scheduling Problem (DPFSP) with factory eligibility constrains and qualification options. The DPFSP is an extension of the original Flowshop Scheduling Problem, adapted to distributed manufacturing environments where multiple factories are considered. The original problem is further modified to incorporate factory eligibility constraints and qualification options by tool transfer.

## Problem Description
In the Distributed Permutation Flowshop Scheduling Problem (DPFSP), according to Naderi and Ruiz (2010), there are $\phi$ different factories to which a set of $n$ jobs must be allocated and subssequently sequenced within the factories. Each factory consists of a permutation flowshop with $m$ serial machines. The processing time $p_{ji}$ of a job $j$ on a machine $i$ can be adjusted via speed factors. Factories are heterogeneous regarding process times, setup times, energy consumption, electricity prices, and the emission factors of electricity generation. Idle times are assumed to be negligible. The eligibility constraints limit the processing of a job to a subset of suitable factories. Processing a job in an initially ineligible factory requires a tool transfer, resulting in a release time equal to the transfer time. A transfer after the start of processing is not allowed. The number of tool transfers is limited, with a truck transferring only one tool at a time. Finally, the job is delivered to the customer by truck after manufacturing.

## Instance Generation
The instances are generated based real-world and synthetic data. Instance generation is made as realistic as possible. The focus is on random problem settings in Europe to ensure a diverse set of problem scenarios.

## Repository Structure

data/: Reports and data files as input for the instance generation.
docs/: Documentation and detailed descriptions of the instance generation process.

## Contributions
Contributions to improve the instance procedure are welcome. Please fork the repository, make your changes, and submit a pull request.

## Contact
For any questions or suggestions, please open an issue on this repository or contact [martin.schoenheit@tu-dresden.de].
