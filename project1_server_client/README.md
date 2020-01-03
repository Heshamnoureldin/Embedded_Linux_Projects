
This project simulate 2 ECUs:

ECU-1 
•It is used to receive packets from user.
•Add the received time to the packet.
•Send the packet to ECU-2 via Ethernet Socket communication (server). 
•Server has two threads ,first one to receive data from user and the second one to send data to the client side.
•Mutual exclusion is handleld using coidition mutex.
•If ECU-1 terminates:
  - It closes socket connections.
  - It closes serial connections.
  - IT sends termination message to the client side.

ECU-2 
•It is used to receive packets from ECU-1 via Ethernet Socket communication (client). 
•Add the received time to the packet.
•Dump the received packet into file in ECU-2’s system files.
•Client has two threads ,first one to receive data from server side and the second one to dump data to log file.
•Mutual exclusion is handleld using coidition mutex.
•If ECU-2 terminates:
  – It closes socket connection.
  – It creates a child process to show the dumped file to the user.
