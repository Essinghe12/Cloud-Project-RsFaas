# Cloud-Project-RsFaas

## 1. Description du projet
Le FaaS, ou « Function-as-a-Service », est un service de cloud computing qui permet aux clients d’exécuter du code en réponse à des événements, sans avoir à gérer l’infrastructure complexe généralement associée au développement et au lancement d’applications de microservices. Le processus se déroule comme suit :
+ Le fournisseur de services initie la mise à disposition de la fonction.
+ L’auteur crée le code de la fonction.
+ L’utilisateur invoque la fonction.
+ Le code de la fonction est acheminé vers l’infrastructure FaaS via la passerelle FaaS.
+ Le code de la fonction est stocké dans le stockage de code de fonction.
+ Lorsque la fonction est invoquée par l’utilisateur, elle est exécutée par le moteur JavaScript.

![Faas implementation ](https://github.com/Essinghe12/Cloud-Project-RsFaas/assets/74486234/bb8c1a79-2b18-4ed4-8a26-02ed883cae95)


Le problème d'exécution anonyme concerne la nécessité de permettre l'exécution de fonctions serverless de manière sécurisée sans divulguer les informations sensibles sur les opérations effectuées. Il s'agit de pouvoir continuer à se reposer sur les services de Faas offert par les CSP (Cloud Service Provider), tout en garantissant la confidentialité du code uploadé. 
Cela implique de garantir la confidentialité et l'intégrité des processus d'exécution. 
La préocupation principale etant de renforcer les domaines suivants :
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


