This was the phase 1 of my MTech Project where I focused on manually coding optimal maximum flow.
Code generation and the paper that follows was done in phase2.

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



# METIS:
 - header files levaraging METIS to generate partitions for Distributed_Network to read from.
 - The system must have METIS installed and updated in evaluate/runner.sh

# Evaluate:
 - runner.sh runs a control sequential algorithm and the distributed push relabel.
 - It ensures correctness for every run.
 - The METIS directory must be updated in the runner.sh script.

# [Slides]([url](https://docs.google.com/presentation/d/16i2pV6ihZN7LllhNuqymHsNxosuF1KV6/edit?usp=sharing&ouid=111109121071675883151&rtpof=true&sd=true)) [link]([url](https://docs.google.com/presentation/d/16i2pV6ihZN7LllhNuqymHsNxosuF1KV6/edit?usp=sharing&ouid=111109121071675883151&rtpof=true&sd=true))

