Encrypted Messaging Social Media App
====================================

Byte Dynamics - Full-Stack Development Week 11 deliverable
----------------------------------------------

System Overview
---------------

The Encrypted Messaging Social Media App is a secure real-time messaging platform that provides end-to-end encryption for all communications. Messages are encrypted before they leave the sender's device and can only be decrypted by the intended recipient. The server never sees plaintext messages, ensuring complete privacy and security.

### Key Features

*   End-to-End Encryption: Hybrid RSA-2048 + AES-256-GCM encryption for all messages
    
*   Real-Time Messaging: Instant message delivery using Socket.I WebSockets
    
*   Secure Authentication: JWT tokens with bcrypt password hashing
    
*   Zero-Knowledge Architecture: Server stores only encrypted messages, never plaintext
    
*   User Management: Registration, login, and user list functionality
    
*   Responsive UI: Modern chat interface with message bubbles and timestamps
    

### System Architecture

The application follows a three-tier architecture:

**Client Layer (Browser):**

*   HTML/CSS for user interface
    
*   Vanilla JavaScript for client-side logic
    
*   Web Crypto API for RSA and AES encryption
    
*   Socket.IO client for real-time communication
    

**Server Layer (Backend):**

*   Node.js runtime environment
    
*   Express.js for REST API endpoints
    
*   Socket.IO for WebSocket connections
    
*   JWT for authentication
    
*   bcrypt for password hashing
    

**Database Layer:**

*   SQLite for lightweight data persistence
    
*   Users table stores account information and encryption keys
    
*   Messages table stores encrypted message content in JSON format
    

### Encryption Flow

1.  Sender types message
    
2.  System generates random AES-256 key unique to that message
    
3.  Message is encrypted with AES-GCM
    
4.  AES key is encrypted with recipient's RSA public key
    
5.  Encrypted package is sent to server
    
6.  Server stores encrypted data (cannot decrypt without private key)
    
7.  Server forwards encrypted package to recipient via Socket.IO
    
8.  Recipient decrypts AES key using their RSA private key
    
9.  Recipient decrypts message with AES key
    
10.  Original message is displayed to recipient
    

Key Point: The server NEVER sees plaintext messages at any point in this process.

### Installation Steps

**1\. Install Backend**

bash

` 
cd backend  npm install  node server.js   
`

**2\. Install Frontend** (in a new terminal)

bash

`   
cd frontend  npm install  npx serve public   
`

**3\. Open Browser**

text

`   
http://localhost:3000   
`

### Quick Test

1.  Create two accounts (use two different browsers)
    
2.  Log in with both accounts
    
3.  Select a user from the sidebar
    
4.  Start sending encrypted messages
    
