# How to Run lab04

This document outlines the steps to compile and run the `lab04` application.

## Setup

1.  **Prepare Terminals:**
    * Open one terminal for the master process.
    * Open *n* terminals for the slave processes, where *n* is the number of inputs specified in your `config.txt` file.  Ensure you have enough terminal windows open to match the number of slaves you need to run.

2.  **Compile the Code:**
    * In any of the terminal windows, navigate to the directory containing `lab04.c`.
    * Compile the code using GCC:
        ```bash
        gcc -o lab04 lab04.c
        ```
        This command creates an executable file named `lab04` in the same directory.

## Running the Application

1.  **Run the Slaves:**
    * In each of the *n* slave terminals, execute the `lab04` program with the appropriate port numbers and slave identifier. The port numbers should correspond to the configuration in your `config.txt` file.  The general command format is:
        ```bash
        ./lab04 <master_port> <slave_port> <slave_id>
        ```
        * `<matrix_size>`: The size of matrix n x n to be divided for slaves.
        * `<slave_port>`: The unique port number for this specific slave process (e.g., 5001, 5002, 5003, ...).
        * `<identifier>`:  1 for slave, 0 for master

    * **Example (assuming `master_port` is 30000):**
        * **Terminal 2:** `./lab04 30000 5001 1`
        * **Terminal 3:** `./lab04 30000 5002 2`
        * **Terminal 4:** `./lab04 30000 5003 3`
        * (And so on, for all *n* slaves)

2.  **Run the Master:**
    * In the master terminal (Terminal 1 in this example), execute the `lab04` program with the master port and a role identifier of 0:
        ```bash
        ./lab04 <master_port> <master_control_port> 0
        ```
        * `<matrix_size>`: The size of matrix n x n to be divided for slaves.
        * `<master_control_port>`: The port number the master uses for its own operations (e.g., 4000).
        * `<identifier>`:  1 for slave, 0 for master

    * **Example:**
        * **Terminal 1:** `./lab04 30000 4000 0`
