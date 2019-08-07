************************************
RSA algorithm with Cipher Block Chaining
************************************

Both Certification authority keys and server keys were hardcoded into the programs right in the beginning. d_server was found using extended Euclidean Algorithm (find_d() in the server code), d_ca was “known” to the server, but could have been found using the same function. All the p and q values are prime, z and e are coprime- that can be tested using euclidean() function in the server code. 

Using standard functions, client initiates connection with the server, the server then sends his e and n encrypted with d_ca. Once received, client sends an ACK and then an encrypted nonce, generated with rand(). Upon receiving nonce, server sends a final ACK and then awaits messages from the client until disconnected. 

All subsequent messages from client to server are using RSA_CBC technique for encryption and decryption, (encrypt() and decrypt() functions). Each character is XORed separately and then encrypted with client’s key, the whole text is then concatenated and sent to server, where it is firstly decrypted character by character and then XORed back using the nonce received earlier, then message is assembled back into full text and displayed on the screen. 

![Alt text](screenshot.png?raw=true)
