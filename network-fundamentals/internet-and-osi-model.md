# Internet and the OSI Model

- A network is officially defined as a group or system of interconnected people or items.
- There are two main purposes of computer networks: Communication using computers and sharing of resources.
- (internet vs. Internet) An internet with a lowercase “i” is any interconnection of computer networks.
  Whereas the global Internet is always spelled with a capital I.
- Computer Network is like a "posting a letter or a package".
- In network each layer at the sending end has a parallel in the receiving end.
- Two most common model are: Open Systems Interconnections(OSI) and Transmission Control Protocol/Internet Protocol(TCP/IP)
  model.
- **OSI model layers**:
  - Please Do Not Throw Sausage Pizza Away (Mnemonic)
  - Application Layer:
    - Always implemented in software.
    - End-user interact with this layer.
    - From this layer outgoing message starts its journey so it provides data for the layer below.
  - Presentation Layer:
    - Presents data in a way that it can be easily understood and displayed by the application layer.
    - This layer assumes that a user session is being maintained by the lower layers and transforms content presentation to suit the application.
    - ```Encryption``` is also usually done at this layer.
  - Session Layer:
    - Session layer's responsibility is to take the services of the transport layer and build a service on top of it that manages user sessions.
    - A session is an exchange of information between local applications and remote services on other end systems.
  - Transport Layer:
    - Since the application, presentation and session layers may be handling off large chunks of data, the transport layer
      segments it into smaller chunks. These chunks are called datagrams or segments depending on the protocol used.
    - Sometimes some additional information is required to transmit the segment/datagram reliably. The transport layer
      adds this information to the segment/datagram.
      - An example of this would be the ```checksum```, which helps ensure that the message is correctly delivered to the destination, 
        i.e. that it’s not corrupted and changed to something else on the way.
      - When additional information is added to the start of a segment/datagram, it’s called a ```header```.
      - When additional information is appended to the end it’s called a ```trailer```.
  - Network Layer:
    - Network layer messages are termed as packets.
    - They facilitate the transportation of packets from one end system to another and help to determine the best routes 
      that messages should take from one end system to another.
    - Routing protocols are applications that run on the network layer and exchange messages with each other to develop 
      information that helps them route transport layer messages.
  - Data Link Layer:
    - Allows directly connected hosts to communicate. 
    - Encapsulates packets for transmission across a single link.
    - Resolves transmission conflicts.
    - Handles addressing, If the data link is a broadcast medium, addressing is another link layer problem.
    - Multiplexing and Demultiplexing.
  - Physical Layer:
    - Consists largely of hardware.
    - Provides a solid electrical and mechanical medium to transmit the data.
    - Transmits bits. Not logical packets, datagrams, or segments.
    - Also has to deal with mechanical specifications about the makeup of the cables and the design of the connectors.
- The TCP/IP Model:
  - This model also known as the Internet Protocol Suite.
  - Layers of the TCP/IP stack:
    - Application
    - Transportation
    - Network
    - Data Link
    - Physical
  - TCP/IP is ```used practically```. The OSI model is conceptual and is ```not practically used``` for communication.
  - Application + Presentation + Session = Application layer in TCP/IP.
  - The TCP/IP protocol suite is heavily influenced by the following design choice, also known as the ```end-to-end argument```.
