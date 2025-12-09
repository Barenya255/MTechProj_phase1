# distributedv2.0

## Distributed_Network.hpp:
 - Distributed P2P Network data structure.
 - Each process has a portion of the structure and reads from a tmp file appended by its rank using partitioned_file_read.
 - Communicatory phase between processes creates a global View of the graph.
 - The number of vertices is deduced by max({V}) - min({V})
 - <img width="633" height="715" alt="image" src="https://github.com/user-attachments/assets/ffab1a6c-dd91-42ad-ba0e-b029bd2efb96" />


## distributed_bfs:
 - BFS support to reset heights for Distributed maximum flow.
 - We found the overhead of the BFS kills performance.
 - Gap relabeling after 1000 pulses gave best results.

## synchronize_p2p.hpp:
 - communication substrate for propagating updates to buffers of recipient processes.
 - All processes in world must participate in it.
 - <img width="1015" height="573" alt="image" src="https://github.com/user-attachments/assets/8dd5b840-3dbb-4bf5-8b89-fe2e14305c63" />

## perform_updates.hpp:
 - Responsible for reading udpates from the synchronization buffers into appropriate vectors.

## init_maxflow.cpp:
 - implementes and utilizes the framework this described to perform push relabel.
 - The maximum flow is done in pulses as defined in A.Goldberg and Tarjan's original paper.
 - <img width="999" height="900" alt="image" src="https://github.com/user-attachments/assets/1b9e6c0d-8a4f-4318-a79a-bb29c1cebcbc" />
### Distributed Discharge:
 - <img width="999" height="783" alt="image" src="https://github.com/user-attachments/assets/04a99edc-c493-48fa-84b0-26d9ec6cdb3d" />
### Distributed Push: 
 - <img width="1108" height="488" alt="image" src="https://github.com/user-attachments/assets/add6b27e-2c83-4949-83cf-8eaed58448a8" />
### Distributed Relabel:
 - <img width="981" height="349" alt="image" src="https://github.com/user-attachments/assets/4cee5786-082e-4a2f-b6c4-700cd81d0b69" />



# METIS:
 - header files levaraging METIS to generate partitions for Distributed_Network to read from.
 - The system must have METIS installed and updated in evaluate/runner.sh

# Gap relabeling:
## Low cost consensus Gap Relabeling:
 - You don't necessarily need all the heights to be exactly consistent.
 - <img width="996" height="816" alt="image" src="https://github.com/user-attachments/assets/42d51457-99ab-4f9b-bebd-35a47aae4a68" />
## High cost consensus Gap Relabeling: 
 - <img width="887" height="362" alt="image" src="https://github.com/user-attachments/assets/cd8cda3b-be74-4ba7-b9a9-938c0ee4abed" />


