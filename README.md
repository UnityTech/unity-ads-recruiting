We're excited you are applying to Unity! As a part of the recruitment process, we would like to validate your technical skills through a small assignment. Return your answer as a zip file containing all relevant files _with tests_ (including `.git`, so that we can see your commit history), do not fork this repository.

# Assignment

Design and implement (with proper tests) a _message delivery system_ using [Go](http://golang.org/), C/C++/C#, or Java. You are free to use any external libraries if needed, but make sure your deliverable either contains these or allows us to automatically download any dependencies.

In this simplified scenario the message delivery system includes the following parts:

### Hub

The Hub relays incoming message bodies to receivers based on user ID(s) defined in the message. You don't need to implement authentication, the hub can for example assign arbitrary (unique) user id to the clients as they connect.

- user_id - unsigned 64 bit integer
- Connection to hub must be done using pure TCP. Protocol doesnt require multiplexing.

### Clients

Clients are users who are connected to the hub. Client may send three types of messages which are described below.

### Identity message

A Client can send an identity message which the hub will respond with the user_id of the _connected user_.

![Identity](https://raw.githubusercontent.com/Everyplay/developer-assignment-backend/master/identity.seq.png)

### List message

Client can send a command to list messages, which cause the hub to answer with the list of all connected client user_id:s (excluding the requesting client).

![List](https://raw.githubusercontent.com/Everyplay/developer-assignment-backend/master/list.seq.png)

### Relay message

Clients can send relay messages where the body of the message is relayed to the receivers marked in the message. Design the optimal data format for the message delivery system, so that it consumes minimal amount resources (memory, cpu, etc.). The message body can be relayed to one or multiple receivers.

- max 255 receivers (user_id:s) per message
- message body - byte array (text, JSON, binary, or anything), max length 1024 kilobytes

![Relay](https://raw.githubusercontent.com/Everyplay/developer-assignment-backend/master/relay.seq.png)

*Relay example: receivers: 2 and 3, body: foobar*
