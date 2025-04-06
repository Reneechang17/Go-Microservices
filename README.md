# Go Microservices Project

### Project Introduction
- 

### Tech Used
- **Golang**: The core programming language used to build the microservices.
- **Microservice**: Decomposes the application into smaller, independent services for better scalability, maintainability, and fault tolerance.
- **GraphQL**: Query language for APIs, enabling clients to request exactly data they need, simplifying API calls by aggregating multiple microservice calls.
- **gRPC**: A high-performance RPC framework that uses HTTP/2 for low-latency communication between services.
- **Docker**: Used for containerizing services, ensuring each service runs in its own isolated environment.
- **ElasticSearch**: A distributed search and analytics engine used by the Catalog service for fast product searches and filtering.

### Project Design and Structures
1. **What we build**
    - **GraphQL Gateway**: The entry point between the client and the microservices. The client interacts only with GraphQL Gateway, then routes the request to the corresponding microservices.
    - **Clients (Account, Catalog, Order)**: These clients communicate with the microservices via gRPC.
    - **Microservices**: Each microservice implements its specific business logic and interacts with its own database.
    - Catalog uses ElasticSearch as database for intensive product searches and filtering. ElasticSearch can quickly query and filter large amounts of product data based on multiple attributes (e.g., name, price, description and more).
![What We Build](https://github.com/Reneechang17/Go-Microservices/blob/main/static/what%20we%20build.jpg)

2. **Docker compose yaml**
    - Where defines the services' configuration, including image builds, dependencies, environment variables, and port mappings. 

3. **GraphQL, schema and Request & Response**
    - **Core operations**:
        - **Queries**: For retrieving data. The client sends a query to GraphQL, which is mapped to the appropriate microservice. The response is sent back to the client with requested data.
        - **Mutations**: For modifying data, i.e. create, update, or delete data in the database and trigger backend logic.
![GraphQL core ops](https://github.com/Reneechang17/Go-Microservices/blob/main/static/GraphQL-queriesand%20mutations.jpg)
    - **GraphQL level Schema**: Where defines the structure of data as exposed by the GraphQL server. 
        - **Types** represent the data that can be queried by the client, including fields.
        - **Inputs** define the data the client needs to send when performing mutations.
![GraphQL schema](https://github.com/Reneechang17/Go-Microservices/blob/main/static/GraphQL%20level%20schema.jpg)
   - **Request & Response**:
![Req & Response](https://github.com/Reneechang17/Go-Microservices/blob/main/static/query-req%20and%20response.jpg)

4. **Service Structure**
![Service structure](https://github.com/Reneechang17/Go-Microservices/blob/main/static/service%20structure.jpg)

5. **Project Structure--files**
   - **cmd**: Contains the `main.go` file for each service, responsible for initializing and configuring the service.
   - **pb**: Contains the auto-generated gRPC client and server interfaces from the `proto` files, enabling service-to-service communication.
   - **dockerfile**: Builds Docker images for each service, specifying the base image, dependencies, and how to run the service.
   - **client.go**: Encapsulates the logic to interact with other microservices via gRPC, sending requests and receiving responses.
   - **repository.go**: Defines the data access layer, handling storage and retrieval of data in the database.
   - **server.go**: Handles incoming requests, calls the corresponding service methods, and returns the response.
   - **service.go**: Implements core business logic, using `repository.go` to interact with the database.
![Proj structure](https://github.com/Reneechang17/Go-Microservices/blob/main/static/proj%20structure-files.jpg)

- Services running at(local):

| Service            | PORT    |
| ------------------ | ------- |
| `Account service`  | `:8081` |
| `Catalog service`  | `:8082` |
| `Order service`    | `:8083` |
| `GraphQL Gateway`  | `:8080` |
| `Postgres`         | `:5432` |
| `ElasticSearch`    | `:9200` |
