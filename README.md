# Peer-to-Peer (P2P) Network Simulation

This project simulates a peer-to-peer (P2P) network where peers join the network, download pieces of a file from other peers, and leave the network after a certain session time. 
The simulation includes features like **Local Rarest First** piece selection, **Tit-for-Tat** peer selection, and **Optimistic Unchoke** for peer discovery.

## Table of Contents
1. [Overview]
2. [Features]
3. [Prerequisites]
4. [Running the Simulation in Google Colab]
5. [Code Structure]
6. [Output Explanation]
7. [Customization]
    
## Overview
This project simulates a P2P file-sharing network. Peers join the network, request pieces of a file from other peers, and leave after a random session time.
The simulation uses strategies like Local Rarest First, Tit-for-Tat, and Optimistic Unchoke to mimic real-world P2P behavior.

## Features
- **Event-Driven Simulation**: Uses a priority queue to manage and process events.
- **Peer Behavior**:
  - Seeds start with all pieces of the file.
  - Leechers download pieces using the Local Rarest First strategy.
- **Peer Selection**:
  - Tit-for-Tat for rewarding cooperative peers.
  - Optimistic Unchoke for discovering new peers.
- **Configurable Parameters**:
  - Number of peers (`N`).
  - Number of seeds (`S`).
  - Simulation time (`T`).

## Prerequisites
- **Python 3.8+** (if running locally).
- A **Google account** (if running in Google Colab).

## Running the Simulation in Google Colab
1. **Open Google Colab**:
   - Go to [Google Colab](https://colab.research.google.com/).
   - Sign in with your Google account.
2. **Copy the Code**:
   - Create a new notebook in Google Colab.
   - Copy and paste the provided Python code into a code cell.
3. **Run the Simulation**:
   - Execute the code cell by clicking the `Play` button or pressing `Shift + Enter`.
   - The simulation will run, and you will see output logs in the notebook.

4. **Example Output**:
   [Time 0] Loaded config with N=20, S=1, T=1
   [Time 0] [Step 1] Peer 0 joined the network.
   [Time 0] [Step 1] Peer 1 joined the network.
   ...
   [Time 10] [Step 2] Peer 1 is requesting piece 0 from Peer 0.
   [Time 12] [Step 2 Outcome] Peer 1 downloaded piece 0 from Peer 0.
   [Time 12] Peer 0 uploaded piece 0 to Peer 1.
   
## Code Structure
The simulation consists of the following key components:
- **EventQueue**: Manages a priority queue of events.
- **Config**: Holds simulation configuration parameters.
- **Event**: Base class for all events.
- **Piece**: Represents a piece of the file.
- **Peer**: Represents a peer in the network.
- **Tracker**: Manages the list of peers.
- **Simulator**: Drives the simulation by processing events.
- 
## Output Explanation
The simulation outputs logs in the following format:
- `[Time X]`: The current simulation time.
- `[Step Y]`: The step in the simulation process.
- `Peer A`: The peer performing the action.
- `Piece Z`: The piece being downloaded or uploaded.
Example:
[Time 10] [Step 2] Peer 1 is requesting piece 0 from Peer 0.
[Time 12] [Step 2 Outcome] Peer 1 downloaded piece 0 from Peer 0.
[Time 12] Peer 0 uploaded piece 0 to Peer 1.

## Customization
You can customize the simulation by modifying the following parameters in the `Simulator` class:
- `num_peers`: Number of peers in the network.
- `is_seed`: Whether a peer is a seed (has all pieces).
- `session_time`: How long a peer stays in the network.
Example:
```python
sim = Simulator(num_peers=20)  # Change the number of peers
sim.run()
