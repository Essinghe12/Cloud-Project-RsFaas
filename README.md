# Cloud-Project-RsFaas

## 1. Description du projet


![problem overview](https://github.com/Essinghe12/Cloud-Project-RsFaas/assets/74486234/7b6fc024-8693-43f1-a85b-3770812d57b6)

## 1. Architecture 
For our project, we chose the OpenFaas framework for its ease of installation and use.
Adding a function to OpenFaas takes just a few simple steps:
* faas-cli new pydict --lang python3-flask-debian
* faas-cli build -f pydict.yml
* faas-cli push -f pydict.yml
* faas-cli deploy -f pydict.yml -g http://127.0.0.1:8080
This series of instructions creates a particular architecture, as can be seen in the following example for a Python project:
<img width="576" alt="image" src="https://github.com/fils07/RsFaasDescription/assets/59063893/2dec67b5-2e1d-41ab-b1a0-6bf7c3a935f9">
* The **requirements.txt** file contains the libraries required to execute the function.
* The **handler.py** file contains the function itself.
  <img width="960" alt="image" src="https://github.com/fils07/RsFaasDescription/assets/59063893/9e6300c2-a130-44c4-a762-796c4c8f8089">
 * The event here refers to a simple HTTP request. 
<img width="960" alt="image" src="https://github.com/fils07/RsFaasDescription/assets/59063893/12aba1a1-96ed-42ee-953e-522f1e670f15">

## 2. Solution Design
Our solution is a script written in Python that runs continuously on the server and intercepts HTTP requests containing the decryption key. Once the request has been intercepted, the script uses the key to decrypt the previous **handler.py** file, then re-executes the previous commands. 
The request is then routed, so the function is executed and the script encrypts the **handler.py** file.
![script](https://github.com/fils07/RsFaasDescription/assets/59063893/b0d18c65-d4b9-4413-8ec4-7388e875eff8)

## 3. Solution Implementation
<img width="960" alt="image" src="https://github.com/fils07/RsFaasDescription/assets/59063893/a30d35f9-7cbd-4013-861f-38c3257a33e8">
Once the request has been intercepted, the secret key is extracted and the function decrypted before being executed and the result returned to the user.

## 4. Video Demonstration
[](url)


