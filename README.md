# Tp1
##BEAUCOTE

###UDPClient.py

```python
from socket import *
serverName = ‘localhost’
serverPort = 12000
clientSocket = socket(AF_INET, SOCK_DGRAM)
message = raw_input(’Input lowercase sentence:’)
clientSocket.sendto(message,(serverName, serverPort))
modifiedMessage, serverAddress = clientSocket.recvfrom(2048)
print modifiedMessage
clientSocket.close()
```
###UDPServer.py

```python
from socket import *
serverPort = 12000
serverSocket = socket(AF_INET, SOCK_DGRAM)
serverSocket.bind(('', serverPort))
print "The server is ready to receive"
while 1:
	message, clientAddress = serverSocket.recvfrom(2048)
	modifiedMessage = message.upper()
	serverSocket.sendto(modifiedMessage, clientAddress)
  ```
  
###TCPClient.py
  
  ```python
  from socket import *
serverName = ’servername’
serverPort = 12000
clientSocket = socket(AF_INET, SOCK_STREAM)
clientSocket.connect((serverName,serverPort))
sentence = raw_input(‘Input lowercase sentence:’)
clientSocket.send(sentence)
modifiedSentence = clientSocket.recv(1024)
print ‘From Server:’, modifiedSentence
clientSocket.close()
```

###TCPServer.py

```python
from socket import *
serverPort = 12000
serverSocket = socket(AF_INET,SOCK_STREAM)
serverSocket.bind((‘’,serverPort))
serverSocket.listen(1)
print ‘The server is ready to receive’
while 1:
	connectionSocket, addr = serverSocket.accept()
	sentence = connectionSocket.recv(1024)
	capitalizedSentence = sentence.upper()
	connectionSocket.send(capitalizedSentence)
	connectionSocket.close()
  ```
##4)Client/Server TCP en Netcat: #TCPclient: Pour créer un server netcat on tape: nc -t 12000 
-t : sert à dire que l'on travaille en TCP localhost est l'ip sur lequel on veut envoyer le msg 12000 est le port sur lequel le server se trouve et avec lequel on veut communiquer on écrit ensuite le message que l'on veut envoyer.

#TCPserver: Pour créer un server netcat on tape: nc -t -l -p 12000
-l : sert à dire au server d'écouter
-t : sert à dire que l'on travaille en TCP
-p : sert à spécifier le port 12000 est le port sur lequel le serveur va travailler et communiquer avec le client.
