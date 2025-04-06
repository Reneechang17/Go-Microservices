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
![What We Build](https://github.com/Reneechang17/Go-Microservices/blob/main/static/what%20we%20build.jpg)
   - **GraphQL Gateway**: The entry point between the client and the microservices. The client interacts only with the GraphQL Gateway, which then routes the request to the corresponding microservices.
   - **Clients (Account, Catalog, Order)**: These clients communicate with the microservices via gRPC.
   - **Microservices**: Each microservice implements its specific business logic and interacts with its own database.
   - **Catalog uses ElasticSearch** for its database because it needs to support intensive product searches and filtering. ElasticSearch can quickly query and filter large amounts of product data based on multiple attributes (e.g., name, price, description).

---

- Docker compose files
![Docker-compose](https://github.com/Reneechang17/Go-Microservices/blob/main/static/Docker%20yml%20file.jpg)
- GraphQL operations
![GraphQL core ops](https://github.com/Reneechang17/Go-Microservices/blob/main/static/GraphQL-queriesand%20mutations.jpg)
- GraphQL level schema
![GraphQL schema](https://github.com/Reneechang17/Go-Microservices/blob/main/static/GraphQL%20level%20schema.jpg)
![Req & Response](https://github.com/Reneechang17/Go-Microservices/blob/main/static/query-req%20and%20response.jpg)

- Service Structure
![Service structure](https://github.com/Reneechang17/Go-Microservices/blob/main/static/service%20structure.jpg)

- Project Structure--files
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

### About GraphQL used
- `github.com/99designs/gqlgen` library:


### About gRPC used


### Future works?

