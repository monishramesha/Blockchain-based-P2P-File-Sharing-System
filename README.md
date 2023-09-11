<h1>Blockchain-based-P2P-File-Sharing-System</h1>

This project leverages blockchain technology to provide a secure, decentralized, and transparent way for users to share files directly with one another. Our platform ensures data privacy, access control, and incentivizes participation in the network. Secure file sharing or exploring the potential of blockchain in decentralized applications.
In the context of our platform, an individual unit within a blockchain possesses the following composition:

Each Block encompasses the following components:

<ul>Block Identifier - This is a simple numeric representation denoting the sequential order of the block. Block 0 signifies the inception point, often referred to as the genesis block.</ul>

<ul>Timestamp - This field signifies the exact moment when the block was created and subsequently appended to the blockchain.</ul>

<ul>Proof (Nonce) - Referred to as a nonce, it stands for "number used only once." The nonce is a numerical value incorporated into an encrypted block within the blockchain. When this block is rehashed, it must satisfy specific difficulty level criteria. Altering the nonce allows for variation in the generated hash, enabling the creation of a new block.</ul>

<ul>Previous Block's Hash - This field encapsulates the hash value of the preceding block, in this case, Block Index 2. The SHA-256 hashing algorithm is employed to generate the hash of the entire block. This element establishes the chain of interconnected blocks, forming the bedrock of security within the blockchain architecture.</ul>

<ul>Sender - The individual who uploads a file is required to provide their identity verification or name during the file upload process.</ul>

<ul>Receiver - This field indicates the intended recipient of the shared information or file.</ul>

<ul>Hash of the Shared File - Prior to upload, the provided file undergoes encryption using the file key supplied by the uploader, employing the AES encryption mechanism. Subsequently, the file is subjected to the SHA-256 hashing algorithm upon upload to IPFS (InterPlanetary File System). The hash value obtained from IPFS post-encryption is considered the hash of the shared file, which is then included within the respective block.</ul>


To establish a peer-to-peer network (P2P) for the proper functioning of the blockchain, it's essential to ensure that all connected nodes operate within the same network. Access to the blockchain's data should be limited to users connected to the blockchain's P2P network exclusively. The creation of this P2P network relies on Socket Programming. We are currently developing a permissioned blockchain, which mandates that access be granted to become a part of the blockchain network. Users can obtain this access by clicking on the 'Connect to the blockchain' option displayed on the home screen.

Using socket programming, the list of connected nodes undergoes real-time updates whenever a new user joins or leaves the network. These updates are then broadcasted to the entire P2P network. Once all connected nodes receive the updated list of network participants, the consensus protocol operates seamlessly whenever a new block is added or the blockchain experiences an update. Consequently, the peer-to-peer network functions efficiently and effectively.

<h2>1.1 File Encryption Key</h2>

The file encryption key, also known as the shared key or password, plays a crucial role in enhancing the security of files within the blockchain network. It serves as a confidential communication channel between the sender and the receiver of shared files.

On the upload page, the uploader initiates the process of sharing a file. The file key entered at this stage is instrumental in encrypting the file using the AES encryption method, prior to uploading it to the IPFS network. Importantly, the uploader is responsible for sharing this key exclusively with the intended receiver(s), allowing them to successfully download and decrypt the file. Supported file formats for upload include .pdf, .png, .jpeg, and .txt. Currently, the network imposes a file size limit of 16 megabytes.

On the download page, the receiver, armed with the valid file key provided by the sender, can access and retrieve the shared file from the blockchain onto their local computer. This file key serves as the decryption mechanism, enabling the receiver to interpret the AES-encrypted file downloaded from the IPFS network. Precision in entering the correct file key and hash is essential to ensure a smooth and successful download process.

<h2>1.2 Integration with IPFS</h2>

Our blockchain system is intricately connected with IPFS (InterPlanetary File System) to achieve a lightweight and scalable architecture. This symbiotic relationship between IPFS and blockchain optimizes efficiency and security.

Storing files directly within the blockchain would lead to excessive weight and inefficiency. By integrating IPFS with the blockchain, we harness the decentralized storage capabilities of IPFS, augmenting the blockchain's security and accessibility. Instead of burdening the blockchain with file storage, we leverage IPFS as the primary storage medium, while the blockchain stores only the unique hash associated with each file. IPFS employs the robust SHA-256 hashing algorithm, ensuring that each file is allocated a secure and distinct hash.

This approach guarantees that files are securely stored within a decentralized network provided by IPFS, maintaining accessibility through the blockchain. Retrieving a file is simplified by utilizing its unique generated hash. Consequently, IPFS effectively eliminates the bottleneck of accommodating entire files within the blockchain, streamlining the system's performance and resource utilization.

<h2>1.3 Using Cryptographic Encryption</h2>

<h3>1.3.1 SHA-256 Hashing Algorithm</h3>

Our blockchain system relies on the SHA-256 algorithm to generate a unique hash for each block, which is essential for chaining together blocks in a secure manner through their previous hashes. This same algorithm is employed by IPFS to generate the hash of shared files. We opt for the SHA-256 hashing algorithm due to its numerous advantages:

1. **One-way**: Once a hash is generated, it is impossible to reverse-engineer the original data from the hash, ensuring data integrity and security.

2. **Deterministic**: For a given input, the hash generated remains constant, ensuring consistency and reliability. The same input will consistently produce the same hash.

3. **Fast Computation**: The SHA-256 algorithm is computationally efficient, allowing for quick hash generation.

4. **Avalanche Effect**: Even a minor alteration in the input data results in a substantially different final hash, making it practically impossible to trace the original data from the hash alone.

5. **Collision Resistance**: The likelihood of two different inputs producing the same hash is exceedingly rare, similar to the uniqueness of human fingerprints.

In essence, the SHA-256 hashing algorithm provides a robust foundation for ensuring the security and integrity of blockchain data.

<h3>1.3.2 AES Encryption</h3>

AES (Advanced Encryption Standard) Encryption is employed as a symmetric cryptographic encryption technique within our system. It relies on a shared key between the sender and receiver for accessing files, specifically the file key in this context. Without the implementation of AES Encryption, any user connected to the blockchain could access the file hash, and consequently, the shared file directly from IPFS.

Through the use of AES Encryption, we encrypt files using the uploader's file key. Consequently, if any user attempts to download a file directly from IPFS, they will receive an unreadable file. Only users possessing a valid file key can decrypt the file and access its contents, thereby significantly enhancing both the blockchain and file content security.

In summary, AES Encryption serves as a vital security measure, ensuring that only authorized users can access and interpret the contents of shared files, contributing to the overall security of our blockchain system.
