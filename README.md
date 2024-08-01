# 0x05. AirBnB clone - RESTful API
REST API is a software architectural style for Backend.

REST = “REpresentational State Transfer”. API = Application Programming Interface

Its purpose is to induce performance, scalability, simplicity, modifiability, visibility, portability, and reliability.

REST API is Resource-based, a resource is an object and can be access by a URI. An object is “displayed”/transferred via a representation (typically JSON). HTTP methods will be actions on a resource.

Example:

Resource: Person (John)
Service: contact information (GET)
Representation:
first_name, last_name, date_of_birth
JSON format

There are 6 constraints:
1. Uniform Interface
Define the interface between client-server
Simple and can be split in small parts
HTTP verbs
GET:
Read representation of a resource or a list of resources
POST:
Create a new resource
PUT:
Update an existing resource
DELETE:
Remove an existing resource
URIs - resource name
A resource representation is accessible by a URI:

GET /users: path for listing all user resources
GET /users/12: path for the user id = 12
GET /users/12/addresses: path for listing all addresses of the user id = 12
POST /users: path for creating a user resource
PUT /users/12: path for updating the user id = 12
DELETE /users/12/addresses/2: path for deleting the address id = 2 of the user id = 12
HTTP Response
In the HTTP Response, the client should verify the information of two things:

status code: result of the action
body: JSON or XML representation of resources
Some important status code:

200: OK
201: created => after a POST request
204: no content => can be return after a DELETE request
400: bad request => the server doesn’t understand the request
401: unauthorized => client user can’t be identified
403: forbidden => client user is identified but not allowed to access a resource
404: not found => resource doesn’t exist
500: internal server error
2. Stateless
The server is independent of the client. The server doesn’t store user client information/state. Each request contains enough context to process it (HTTP Headers, etc.)

Some authentication systems like OAuth have to store information on the server side but they do it with REST API design.

3. Cacheable
All server responses (resource representation) are cacheable:

Explicit
Implicit
Negotiated
Caches are here to improve performances. In a REST API, clients don’t care about the caching strategy, if the resource representation comes from a cache or from a database…

4. Client-Server
REST API is designed to separate Client from the Server. The server doesn’t know who is talking to it. Clients are not concerned with data storage => the portability of client code is improved. Servers are not concerned with the user interface or user state so that servers can be simpler and more scalable

5. Layered System
Client can’t assume direct connection to server. Intermediary servers may improve system scalability by enabling load-balancing and by providing shared caches. Layers may also enforce security policies.

6. Code on Demand (optional)
Server can temporarily:

Transfer logic to client
Allow client to execute logic
Example: JavaScript
#### Functionalities of this command interpreter:
* Create a new object (ex: a new User or a new Place)
* Retrieve an object from a file, a database etc...
* Do operations on objects (count, compute stats, etc...)
* Update attributes of an object
* Destroy an object

## Table of Content
* [Environment](#environment)
* [Installation](#installation)
* [File Descriptions](#file-descriptions)
* [Usage](#usage)
* [Examples of use](#examples-of-use)
* [Bugs](#bugs)
* [Authors](#authors)
* [License](#license)

## Environment
This project is interpreted/tested on Ubuntu 20.04 LTS using python3 (version 3.4.3)

## File Descriptions
[console.py](console.py) - the console contains the entry point of the command interpreter. 
List of commands this console current supports:
* `EOF` - exits console 
* `quit` - exits console
* `<emptyline>` - overwrites default emptyline method and does nothing
* `create` - Creates a new instance of`BaseModel`, saves it (to the JSON file) and prints the id
* `destroy` - Deletes an instance based on the class name and id (save the change into the JSON file). 
* `show` - Prints the string representation of an instance based on the class name and id.
* `all` - Prints all string representation of all instances based or not on the class name. 
* `update` - Updates an instance based on the class name and id by adding or updating attribute (save the change into the JSON file). 

#### `models/` directory contains classes used for this project:
[base_model.py](/models/base_model.py) - The BaseModel class from which future classes will be derived
* `def __init__(self, *args, **kwargs)` - Initialization of the base model
* `def __str__(self)` - String representation of the BaseModel class
* `def save(self)` - Updates the attribute `updated_at` with the current datetime
* `def to_dict(self)` - returns a dictionary containing all keys/values of the instance

Classes inherited from Base Model:
* [amenity.py](/models/amenity.py)
* [city.py](/models/city.py)
* [place.py](/models/place.py)
* [review.py](/models/review.py)
* [state.py](/models/state.py)
* [user.py](/models/user.py)

#### `/models/engine` directory contains File Storage class that handles JASON serialization and deserialization :
[file_storage.py](/models/engine/file_storage.py) - serializes instances to a JSON file & deserializes back to instances
* `def all(self)` - returns the dictionary __objects
* `def new(self, obj)` - sets in __objects the obj with key <obj class name>.id
* `def save(self)` - serializes __objects to the JSON file (path: __file_path)
* ` def reload(self)` -  deserializes the JSON file to __objects

## Author
Evans Mukonyole - [Github] (https://github.com/Mukonyole)
