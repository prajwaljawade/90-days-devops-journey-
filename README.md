# 90-days-devops-journey-


# 🌐 Networking Fundamentals — What I Learned

IN first week I learned some important networking concepts that are useful for my DevOps journey.

## 1. 🧩 OSI Model

The **OSI (Open Systems Interconnection) Model** is a 7-layer model that helps us understand how data travels from one computer to another over a network.

### The 7 Layers

 Layer   Name          What I Understood                            
 
 7      Application  | Where applications interact with the network 
 6      Presentation | Data formatting, encryption, compression     
 5      Session      | Manages communication sessions               
 4      Transport    | Reliable data delivery using TCP/UDP         
 3      Network      | Handles IP addresses and routing             
 2      Data Link    | Handles MAC addresses and frames             
 1      Physical     | Transfers raw bits through cables/signals    

### 🧠 My Understanding

I think of the OSI model as a **step-by-step journey of data**.



The data goes down through the layers on the sender side and comes back up through the layers on the receiver side.

📖 Resource: [OSI Model — GeeksforGeeks](https://www.geeksforgeeks.org/layers-of-osi-model/)

---

## 2. 🔌 Common Networking Protocols

A **protocol** is basically a set of rules that devices follow to communicate with each other.

Some protocols I learned about:

* **HTTP** → Used for communication between web browsers and web servers.
* **HTTPS** → Secure version of HTTP.
* **FTP** → Used for transferring files.
* **SSH** → Used to securely connect to remote machines.
* **DNS** → Converts domain names into IP addresses.
* **TCP** → Reliable and connection-oriented communication.
* **UDP** → Faster but does not guarantee delivery.
* **ICMP** → Used for network diagnostics, such as `ping`.



📖 Resource: [List of Network Protocols — Wikipedia](https://en.wikipedia.org/wiki/List_of_network_protocols)

---

## 3. ☁️ AWS Free Tier

I also explored the **AWS Free Tier**.

AWS provides cloud services that can be used to learn and practice cloud technologies, with free usage available for eligible services and accounts under their applicable terms.

For my DevOps journey, AWS is important because many DevOps tools and workflows are used with cloud infrastructure.



📖 Resource: [AWS Free Tier](https://aws.amazon.com/free/)

---

## 4. 🌍 DNS — Domain Name System

DNS is one of the most important networking concepts I learned.

### What does DNS do?

DNS converts a **domain name** into an **IP address**.

For example:

```text
www.example.com
       ↓
     DNS
       ↓
  IP Address
```

Humans prefer remembering names like:

```text
google.com
```

while computers communicate using IP addresses.




### 🧠 My Understanding

I think of DNS like a **phonebook of the internet**.

Instead of remembering someone's phone number, we remember their name.

Similarly, instead of remembering a server's IP address, we use a domain name.

📖 Resource: [DNS Basics — Cloudflare](https://www.cloudflare.com/learning/dns/what-is-dns/)

---

## 5. 🐳 Docker Networking

Docker networking allows **containers to communicate with each other and with the outside world**.

Containers are isolated by default, so Docker provides networking mechanisms to connect them.

### Common Docker Network Types

* **Bridge** → Commonly used for containers on the same Docker host.
* **Host** → Container shares the host's network stack.
* **None** → Container has no network connectivity.
* **Overlay** → Used for communication across multiple Docker hosts, commonly with Docker Swarm.


This is very useful when building applications with multiple services.

📖 Resource: [Docker Networking Documentation](https://docs.docker.com/network/)

---

# 🧠 My Key Takeaways

After studying these concepts, I understood that networking is a **fundamental part of DevOps**.

The main things I learned today:

✅ OSI model explains how network communication works.

✅ Protocols define how devices communicate.

✅ DNS translates domain names into IP addresses.

✅ AWS provides cloud infrastructure that I can practice with.

✅ Docker networking allows containers to communicate.

---


