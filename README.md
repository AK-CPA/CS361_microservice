MicroService Readme

How to send a request to the microservice?

The microservice uses ZeroMQ. No data is required (the microservice will read from the GeneralLedger.txt file directly). See below example of how to send ZeroMQ request.

def client():
    # Create a ZeroMQ context
    context = zmq.Context()
    
    # Create a request socket (client)
    socket = context.socket(zmq.REQ)
    
    # Connect to the ZeroMQ server
    socket.connect("tcp://localhost:5555")
    
    # Send a request message to the server
    request_message = "Please trigger summary microservice"
    print(f"Sending request: {request_message}")
    socket.send_string(request_message)
    
    # Wait for the response from the server
    response_message = socket.recv_string()
    print(f"Received response: {response_message}

How to receive data?
The microservice will create summary charts directly in the main folder of the project. No specific data will be received by the program.

<img width="843" alt="image" src="https://github.com/user-attachments/assets/9bca17d0-ae8a-4cae-aa36-72d8a2fa08c4">
