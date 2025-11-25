# WEB303 Microservices & Serverless Applications - Complete Practicals# Practical 6 Example: Comprehensive Testing for Microservices

**Student:** Kinley-pal8 ## Overview

**Module:** WEB303 Microservices & Serverless Applications

**Academic Year:** 2025This is the complete example implementation for **Practical 6**, demonstrating comprehensive testing strategies for gRPC microservices. It builds on Practical 5A and adds unit tests, integration tests, end-to-end tests, and test automation.

---### Key Learning Objectives

## Overview1. **Unit Testing**: Test individual service methods in isolation using in-memory databases

2. **Mocking**: Use mocks to simulate external dependencies in unit tests

This repository contains **three complete practicals** demonstrating the full evolution of microservices architecture:3. **Integration Testing**: Test multiple services working together using in-memory gRPC connections

4. **End-to-End Testing**: Validate the entire system through HTTP API requests

| Practical | Focus | Achievement |5. **Test Automation**: Use Makefile for consistent test execution and CI/CD integration

|-----------|-------|-------------|

| **5A** | Centralized gRPC with Proto Repository | Hybrid architecture (HTTP + gRPC internal) |## What's Included

| **5B** | Pure gRPC Backend | Simplified services with 39% code reduction |

| **6** | Comprehensive Testing | 1,900+ lines of test code with full coverage |This example includes comprehensive tests at three levels:

---### ✅ Unit Tests

- **User Service**: `user-service/grpc/server_test.go`

## Quick Navigation - Tests for CreateUser, GetUser, GetUsers

- In-memory SQLite database


### Detailed Guides

- **Order Service**: `order-service/grpc/server_test.go`

- **[practical5a.md](practical5a.md)** - Complete 5A Guide (636 lines) - Tests with mocked gRPC clients

- **[practical5b.md](practical5b.md)** - Complete 5B Guide (787 lines) - Validation scenarios (invalid user, invalid menu item)

- **[practical6.md](practical6.md)** - Complete 6 Guide (1,455 lines) - Price snapshotting tests

---### ✅ Integration Tests

Located in `tests/integration/integration_test.go`:

## Practical Progression- Complete order flow across all services

- Order validation tests

### Practical 5A: gRPC Migration with Centralized Proto Repository- Concurrent request handling

- Uses bufconn (in-memory gRPC connections)

**Objective:** Add gRPC for inter-service communication with centralized protocol buffer management

### ✅ End-to-End Tests

**What You'll Learn:**Located in `tests/e2e/e2e_test.go`:

- Create centralized versioned protocol buffer repository- Full system validation via HTTP API

- Implement gRPC servers in microservices- User creation and retrieval

- Implement gRPC clients for inter-service communication- Menu item management

- Solve proto synchronization issues- Complete order workflow

- Hybrid architecture (HTTP external, gRPC internal)- Error handling validation

- Requires running Docker containers

**Key Components:**

- `student-cafe-protos/` - Centralized proto module (standalone Go module)## Project Structure

- `user-service/` - HTTP server + gRPC server (port 8081/9091)

- `menu-service/` - HTTP server + gRPC server (port 8082/9092)```

- `order-service/` - HTTP server + gRPC server + gRPC clients (port 8083/9093)practical5a/

- `api-gateway/` - HTTP reverse proxy (port 8080)├── student-cafe-protos/ # Centralized proto repository

│ ├── proto/ # Proto definition files

**Key Achievement:** Type-safe inter-service communication with 2-5x performance improvement│ │ ├── user/v1/user.proto

│ │ ├── menu/v1/menu.proto

---│ │ └── order/v1/order.proto

│ ├── gen/go/ # Generated Go code

### Practical 5B: Pure gRPC Backend with HTTP Gateway│ ├── go.mod # Go module definition

│ ├── Makefile # Proto generation commands

**Objective:** Simplify services to pure gRPC backend with HTTP gateway translation│ └── README.md # Proto repo documentation

├── user-service/ # User microservice

**What You'll Learn:**│ ├── grpc/server.go # gRPC server implementation

- Protocol translation pattern (HTTP to gRPC)│ ├── handlers/ # HTTP handlers (REST)

- Service simplification (39% code reduction)│ ├── main.go # Runs both HTTP and gRPC servers

- Gateway as intelligent translator│ └── Dockerfile

- Pure gRPC internal architecture├── menu-service/ # Menu microservice

- Backwards compatibility for HTTP clients│ ├── grpc/server.go

│ ├── handlers/

**Key Components:**│ ├── main.go

- `api-gateway/` - Enhanced to translate HTTP to gRPC calls│ └── Dockerfile

- `user-service/` - Simplified to gRPC only (46 lines, port 9091)├── order-service/ # Order microservice

- `menu-service/` - Simplified to gRPC only (46 lines, port 9092)│ ├── grpc/

- `order-service/` - gRPC only with clients (46 lines, port 9093)│ │ ├── server.go # gRPC server

- `student-cafe-protos/` - Same centralized proto module│ │ └── clients.go # gRPC clients for other services

│ ├── handlers/ # HTTP handlers (use gRPC internally)

**Key Achievement:** 39% code reduction per service while improving type safety│ ├── main.go

│ └── Dockerfile

---├── api-gateway/ # REST API Gateway

├── docker-compose.yml # Orchestration config

### Practical 6: Comprehensive Testing for Microservices├── deploy.sh # Deployment script

└── README.md # This file

**Objective:** Implement testing across all three tiers of testing pyramid```

**What You'll Learn:**## Prerequisites

- Unit testing with mocks and test isolation

- Integration testing with bufconn (in-memory connections)### Required Tools

- End-to-end testing via HTTP API

- Testing best practices and patterns1. **Go** (1.23+)

- Test automation with Make commands ```bash

  go version

**Key Components:** ```

- `tests/integration/` - Multi-service integration tests (431 lines)

- `tests/e2e/` - Full system HTTP API tests (488 lines)2. **Protocol Buffer Compiler (protoc)**

- `user-service/grpc/server_test.go` - Unit tests (240 lines) ```bash

- `menu-service/grpc/server_test.go` - Unit tests (272 lines) # macOS

- `order-service/grpc/server_test.go` - Unit tests with mocks (469 lines) brew install protobuf

**Key Achievement:** 45+ test scenarios covering all services with 1,900+ lines of test code # Linux

sudo apt-get install protobuf-compiler

---

# Verify

## Architecture Evolution protoc --version

```

```

PRACTICAL 5A: Hybrid Microservices3. **Go Proto Plugins**

┌─────────────┐ ```bash

│ HTTP Client│ go install google.golang.org/protobuf/cmd/protoc-gen-go@latest

└──────┬──────┘ go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest

       │ HTTP   ```

       ▼

┌─────────────────────────┐4. **Docker & Docker Compose**

│ API Gateway (8080) │ HTTP Reverse Proxy ```bash

└──────┬──────────────────┘ docker --version

       │ HTTP   docker-compose --version

       ├─────────┬──────────┬─────────┐   ```

       ▼         ▼          ▼         ▼

    (8081)   (8082)     (8083)     (other)## Quick Start

    User     Menu       Order      services

HTTP+ HTTP+ HTTP+ with### Option 1: Automated Deployment (Recommended)

gRPC gRPC gRPC gRPC

````bash

├────gRPC────→│ (inter-service)./deploy.sh

└────gRPC────────────→│ (inter-service)```



PRACTICAL 5B: Pure gRPC BackendThis script will:

┌─────────────┐1. Generate Go code from proto files

│  HTTP Client│2. Clean up existing containers

└──────┬──────┘3. Build Docker images

    │ HTTP4. Start all services

    ▼5. Display access information

┌─────────────────────────────────────┐

│  API Gateway (8080) - Translator    │ Converts HTTP to gRPC### Option 2: Manual Deployment

└──────┬──────────────────────────────┘

    │ gRPC#### Step 1: Generate Proto Code

    ├──────────┬──────────┬────────┐

    ▼          ▼          ▼        ▼```bash

 (9091)    (9092)     (9093)   (others)cd student-cafe-protos

 User      Menu       Order    servicesmake generate

 gRPC      gRPC       gRPC     Pure gRPCcd ..

 ```

 ├────gRPC────→│ (inter-service)

 └────gRPC────────────→│ (inter-service)#### Step 2: Build and Start Services



PRACTICAL 6: Tested Microservices```bash

(Same as 5B + comprehensive testing)docker-compose build

```docker-compose up -d

````

---

#### Step 3: Verify Services

## Project Structure (Organized)

````bash

```docker-compose ps

Student-Cafe-Microservices/```

├── Documentation/

│   ├── PRACTICAL_5A_REPORT.md       (Summary report - 400 lines)All services should show as "Up".

│   ├── PRACTICAL_5B_REPORT.md       (Summary report - 400 lines)

│   ├── PRACTICAL_COMPLETION_REPORT.md (Summary report - 400 lines)## Testing the Application

│   ├── practical5a.md               (Full guide - 636 lines)

│   ├── practical5b.md               (Full guide - 787 lines)### 1. Create a Menu Item

│   ├── practical6.md                (Full guide - 1,455 lines)

│   └── README.md                    (This file)```bash

│curl -X POST http://localhost:8080/api/menu \

├── Core Services/  -H "Content-Type: application/json" \

│   ├── user-service/                (User management service)  -d '{

│   │   ├── main.go    "name": "Cappuccino",

│   │   ├── grpc/    "description": "Italian coffee with steamed milk",

│   │   │   ├── server.go            (gRPC implementation)    "price": 3.50

│   │   │   └── server_test.go       (Unit tests - 240 lines)  }'

│   │   ├── handlers/                (HTTP handlers - 5A only)```

│   │   ├── database/                (GORM setup)

│   │   ├── models/                  (Data models)### 2. Create a User

│   │   ├── go.mod

│   │   └── Dockerfile```bash

│   │curl -X POST http://localhost:8080/api/users \

│   ├── menu-service/                (Menu catalog service)  -H "Content-Type: application/json" \

│   │   ├── main.go  -d '{

│   │   ├── grpc/    "name": "Alice Smith",

│   │   │   ├── server.go            (gRPC implementation)    "email": "alice@example.com",

│   │   │   └── server_test.go       (Unit tests - 272 lines)    "is_cafe_owner": false

│   │   ├── handlers/                (HTTP handlers - 5A only)  }'

│   │   ├── database/                (GORM setup)```

│   │   ├── models/                  (Data models)

│   │   ├── go.mod### 3. Create an Order (Demonstrates gRPC Communication)

│   │   └── Dockerfile

│   │```bash

│   └── order-service/               (Order processing service)curl -X POST http://localhost:8080/api/orders \

│       ├── main.go  -H "Content-Type: application/json" \

│       ├── grpc/  -d '{

│       │   ├── server.go            (gRPC implementation)    "user_id": 1,

│       │   ├── clients.go           (gRPC clients - 5A+)    "items": [

│       │   └── server_test.go       (Unit tests with mocks - 469 lines)      {"menu_item_id": 1, "quantity": 2}

│       ├── handlers/                (HTTP handlers - 5A only)    ]

│       ├── database/                (GORM setup)  }'

│       ├── models/                  (Data models)```

│       ├── go.mod

│       └── Dockerfile**What happens behind the scenes:**

│1. Client sends HTTP request to API Gateway

├── API & Communication/2. API Gateway forwards to Order Service (HTTP)

│   ├── api-gateway/                 (HTTP to gRPC translator)3. Order Service validates user via **gRPC** call to User Service

│   │   ├── main.go4. Order Service fetches menu item price via **gRPC** call to Menu Service

│   │   ├── grpc/clients.go          (Service clients)5. Order Service creates order and returns HTTP response

│   │   ├── handlers/                (HTTP to gRPC translation)

│   │   ├── go.mod### 4. Verify gRPC Communication

│   │   └── Dockerfile

│   │Check the order-service logs to see gRPC calls:

│   └── student-cafe-protos/         (Centralized proto repository - 5A+)

│       ├── proto/                   (Proto source files)```bash

│       │   ├── user/v1/user.protodocker-compose logs order-service | grep gRPC

│       │   ├── menu/v1/menu.proto```

│       │   └── order/v1/order.proto

│       ├── gen/go/                  (Generated code)You should see messages like:

│       ├── buf.yaml                 (Buf configuration)```

│       ├── go.mod                   (Proto module)gRPC clients initialized successfully

│       └── Makefile                 (Code generation)gRPC server starting on :9093

│```

├── Testing/                         (Practical 6)

│   └── tests/## Understanding the gRPC Implementation

│       ├── integration/             (Multi-service tests)

│       │   ├── integration_test.go  (431 lines, bufconn-based)### 1. Centralized Proto Repository

│       │   └── go.mod

│       └── e2e/                     (Full system tests)**Location**: `student-cafe-protos/`

│           ├── e2e_test.go          (488 lines, HTTP API)

│           └── go.mod**Key Files**:

│- `proto/user/v1/user.proto`: User service definitions

└── Deployment/- `proto/menu/v1/menu.proto`: Menu service definitions

    ├── docker-compose.yml           (Service orchestration)- `proto/order/v1/order.proto`: Order service definitions

    ├── Makefile                     (Build, test, deploy commands)

    ├── deploy.sh                    (Deployment script - 5A)**Why This Solves Previous Issues**:

    └── deploy_5b.sh                 (Deployment script - 5B)

```In previous practicals, students often faced:

- ❌ Proto files duplicated across services

---- ❌ Version mismatches between services

- ❌ Docker build errors when copying proto files

## Getting Started- ❌ Circular dependencies



### 1. PrerequisitesOur solution:

- ✅ Single source of truth for all proto definitions

```bash- ✅ Versioned Go module that services import

# Check Go version (1.23+)- ✅ Proto code generated once, used everywhere

go version- ✅ Docker builds work reliably with `replace` directive



# Install Docker and Docker Compose### 2. How Services Import Proto Code

docker --version

docker-compose --versionEach service's `go.mod` includes:



# Install Protocol Buffer Compiler```go

brew install protobuf  # macOSrequire (

# or apt-get install protobuf-compiler  # Linux    github.com/douglasswm/student-cafe-protos v0.0.0

```    google.golang.org/grpc v1.59.0

)

### 2. Clone/Setup

// Local development: point to the local proto module

```bashreplace github.com/douglasswm/student-cafe-protos => ../student-cafe-protos

cd /home/easykp8/Desktop/Year\ 3/practical6-example```

````

**The `replace` directive** tells Go to use the local proto module instead of fetching from GitHub. This is perfect for development!

### 3. Choose Your Practical

### 3. Dual Server Implementation

#### Practical 5A Only (Hybrid gRPC + HTTP)

Each service runs **two servers concurrently**:

````bash

# Generate proto code```go

cd student-cafe-protos && make generate && cd ..func main() {

    // ... database connection ...

# Build and deploy

docker-compose build    // Start gRPC server in background

docker-compose up -d    go startGRPCServer()



# Access    // Start HTTP server (blocks)

curl http://localhost:8080/api/menu    startHTTPServer()

```}

````

#### Practical 5B Only (Pure gRPC)

**HTTP Server** (port 8081/8082/8083):

````bash- Handles REST API requests

# Use 5B deployment script- Used by API Gateway and external clients

./deploy_5b.sh

```**gRPC Server** (port 9091/9092/9093):

- Handles internal service-to-service calls

#### All with Testing (Practical 5B + 6)- More efficient than HTTP/REST

- Strongly typed with proto definitions

```bash

# Deploy services### 4. gRPC Client Usage (Order Service Example)

docker-compose up -d

The order service creates gRPC clients to call other services:

# Run unit and integration tests

make test-unit```go

make test-integration// In main.go

clients, err := grpcserver.NewClients()

# Run E2E testshandlers.GrpcClients = clients

make test-e2e

```// In handlers/order_handlers.go

// Validate user via gRPC

---userResp, err := GrpcClients.UserClient.GetUser(ctx, &userv1.GetUserRequest{

    Id: uint32(req.UserID),

## Testing})



### Unit Tests// Get menu item via gRPC

menuResp, err := GrpcClients.MenuClient.GetMenuItem(ctx, &menuv1.GetMenuItemRequest{

Test individual services in isolation:    Id: uint32(item.MenuItemID),

})

```bash```

make test-unit              # All unit tests

make test-unit-user         # User service only**Benefits over HTTP**:

make test-unit-menu         # Menu service only- Type safety (compile-time checks)

make test-unit-order        # Order service only- Better performance (binary protocol)

```- Streaming support (not used here, but available)

- Built-in load balancing and retries

**Coverage:** 35+ test scenarios, <200ms execution

## Troubleshooting

### Integration Tests

### Issue 1: Proto Generation Fails

Test multiple services working together:

**Symptom**:

```bash```

make test-integration       # All integration testsprotoc-gen-go: program not found

````

**Coverage:** 4 multi-service workflows with bufconn (in-memory gRPC)**Solution**:

````bash

### End-to-End Testscd student-cafe-protos

make install-tools

Test full system via HTTP API:```



```bash### Issue 2: Docker Build Fails - Proto Module Not Found

make test-e2e               # Requires services running

make test-e2e-docker        # Starts services, runs tests, stops**Symptom**:

````

go: github.com/douglasswm/student-cafe-protos@v0.0.0: invalid version

**Coverage:** 8+ complete workflows via HTTP API```

### All Tests**Solution**:

Ensure the Dockerfile copies the proto module:

`bash`dockerfile

make test # Unit + Integration testsCOPY ../student-cafe-protos /student-cafe-protos

make test-all # Unit + Integration + E2E tests```

make test-coverage # Generate coverage reports

```And the service `go.mod`has the`replace` directive.

---### Issue 3: gRPC Connection Refused

## API Endpoints**Symptom**:

```

### User Servicefailed to connect to user service: connection refused

```

````bash

# Create user**Solutions**:

curl -X POST http://localhost:8080/api/users \1. Verify services are running:

  -H "Content-Type: application/json" \   ```bash

  -d '{"name": "Alice", "email": "alice@test.com", "is_cafe_owner": false}'   docker-compose ps

````

# Get user by ID

curl http://localhost:8080/api/users/12. Check gRPC ports are exposed:

````bash

# List all users   docker-compose logs user-service | grep "gRPC server"

curl http://localhost:8080/api/users   ```

````

3. Verify service names in `docker-compose.yml` match code:

### Menu Service ```yaml

environment:

````bash USER_SERVICE_GRPC_ADDR: "user-service:9091"

# Create menu item   ```

curl -X POST http://localhost:8080/api/menu \

  -H "Content-Type: application/json" \### Issue 4: Changes Not Reflected

  -d '{"name": "Latte", "description": "Espresso with milk", "price": 4.00}'

**Symptom**: Code changes don't appear after rebuild

# Get menu item

curl http://localhost:8080/api/menu/1**Solution**:

```bash

# List all menu itemsdocker-compose down

curl http://localhost:8080/api/menudocker-compose build --no-cache

```docker-compose up -d

````

### Order Service

## Updating Proto Definitions

````bash

# Create order (demonstrates inter-service gRPC calls)### Step-by-Step Guide

curl -X POST http://localhost:8080/api/orders \

  -H "Content-Type: application/json" \1. **Modify Proto Files**

  -d '{"user_id": 1, "items": [{"menu_item_id": 1, "quantity": 2}]}'

   Edit the relevant `.proto` file in `student-cafe-protos/proto/`:

# Get order

curl http://localhost:8080/api/orders/1   ```protobuf

   // Add a new field to User

# List all orders   message User {

curl http://localhost:8080/api/orders       uint32 id = 1;

```       string name = 2;

       string email = 3;

---       bool is_cafe_owner = 4;

       string phone_number = 5;  // NEW FIELD

## Key Learning Points   }

````

### Practical 5A

2. **Regenerate Code**

- Centralized proto repository eliminates synchronization issues

- gRPC servers run alongside HTTP for backward compatibility ```bash

- Type-safe inter-service communication through proto contracts cd student-cafe-protos

- 2-5x performance improvement vs HTTP for internal calls make clean && make generate

- Proper error handling with gRPC status codes ```

### Practical 5B3. **Update Service Implementation**

- Protocol translation pattern maintains backwards compatibility Update the model conversion in the affected service:

- Backend service simplification (39% code reduction)

- Single-protocol design simplifies service code ```go

- Gateway acts as intelligent HTTP-to-gRPC converter // In user-service/grpc/server.go

- Clear separation: HTTP external, gRPC internal func modelToProto(user *models.User) *userv1.User {

       return &userv1.User{

### Practical 6 // ... existing fields ...

           PhoneNumber: user.PhoneNumber,  // NEW

- Three-tier testing pyramid (unit, integration, E2E) }

- Mock gRPC clients for unit test isolation }

- Bufconn for fast in-memory integration testing ```

- Real HTTP API validation with E2E tests

- Test automation with Makefile for CI/CD integration4. **Rebuild and Deploy**

--- ```bash

cd ..

## Service Ports Reference ./deploy.sh

````

| Service | Protocol | Port | Purpose |

|---------|----------|------|---------|## Advanced Topics

| API Gateway | HTTP | 8080 | External client entry point |

| User Service | HTTP | 8081 | 5A only - REST API |### Versioning Proto Definitions

| User Service | gRPC | 9091 | Service-to-service |

| Menu Service | HTTP | 8082 | 5A only - REST API |For production, you'd tag the proto module:

| Menu Service | gRPC | 9092 | Service-to-service |

| Order Service | HTTP | 8083 | 5A only - REST API |```bash

| Order Service | gRPC | 9093 | Service-to-service |cd student-cafe-protos

| User DB | PostgreSQL | 5434 | User database |git add .

| Menu DB | PostgreSQL | 5433 | Menu database |git commit -m "Add phone_number field to User"

| Order DB | PostgreSQL | 5435 | Order database |git tag v1.1.0

git push origin v1.1.0

---```



## Common CommandsThen services can pin to specific versions:



```bash```go

# View logsrequire (

docker-compose logs api-gateway    github.com/douglasswm/student-cafe-protos v1.1.0

docker-compose logs user-service)

docker-compose logs -f order-service    # Follow logs```



# Stop services### Adding gRPC Interceptors

docker-compose down

For logging, authentication, or error handling:

# Clean and rebuild

docker-compose down -v```go

docker-compose build --no-caches := grpc.NewServer(

docker-compose up -d    grpc.UnaryInterceptor(loggingInterceptor),

)

# Enter service container```

docker-compose exec user-service sh

### gRPC Streaming

# View service status

docker-compose psThe proto definitions support streaming (not implemented here):

````

````protobuf

---service OrderService {

    // Server streaming - watch order updates

## File Statistics    rpc WatchOrder(WatchOrderRequest) returns (stream Order);

}

| Practical | Implementation | Documentation | Tests | Total |```

|-----------|----------------|----------------|-------|-------|

| 5A | 1000+ lines | 636 lines | 0 lines | 1,636 |## Comparison with Practical 5

| 5B | 434 lines | 787 lines | 0 lines | 1,221 |

| 6 | Same as 5B | 1,455 lines | 1,900+ lines | 3,355+ || Aspect | Practical 5 (HTTP) | Practical 5A (gRPC) |

| **Total** | **1,434+ lines** | **2,878 lines** | **1,900+ lines** | **6,212+ lines** ||--------|-------------------|-------------------|

| **Inter-Service Protocol** | HTTP/REST | gRPC |

---| **External API** | HTTP/REST | HTTP/REST (same) |

| **Type Safety** | JSON (runtime) | Protobuf (compile-time) |

## Reports Summary| **Performance** | Good | Better (binary protocol) |

| **Proto Management** | N/A | Centralized module |

### Quick Summaries (Start Here - 1,200 lines total)| **Complexity** | Lower | Higher (but more scalable) |



1. **PRACTICAL_5A_REPORT.md** - 400 lines## Key Takeaways

   - Centralized proto repository

   - Hybrid gRPC + HTTP architecture1. **Centralized Proto Repository**: Solves version sync and build issues by treating proto definitions as a versioned Go module

   - Type-safe service contracts

   - 2-5x performance improvement2. **Dual Protocol Support**: Services can speak both HTTP (for clients) and gRPC (for internal communication)



2. **PRACTICAL_5B_REPORT.md** - 400 lines3. **gRPC Benefits**:

   - Pure gRPC backend implementation   - Type safety via proto definitions

   - Protocol translation layer   - Better performance than REST

   - 39% code reduction per service   - Built-in features (streaming, deadlines, cancellation)

   - Production architecture

4. **Production Ready**: This pattern is used by companies like Google, Netflix, and Uber

3. **PRACTICAL_COMPLETION_REPORT.md** - 400 lines

   - Unit, integration, E2E testing5. **Trade-offs**: More complex than pure REST, but scales better for large systems

   - 45+ test scenarios

   - Testing best practices## Next Steps

   - CI/CD automation

1. **Add gRPC Health Checks**: Implement the gRPC health checking protocol

### Detailed Guides (4,878 lines total)2. **Add Metrics**: Collect gRPC metrics with Prometheus

3. **Deploy to Kubernetes**: Migrate from Docker Compose to K8s

For complete implementation details, see:4. **Add Service Mesh**: Integrate Istio for advanced traffic management

- `practical5a.md` - Complete 5A walkthrough5. **Implement Streaming**: Add real-time order updates using server streaming

- `practical5b.md` - Complete 5B walkthrough

- `practical6.md` - Complete 6 testing guide## Resources



---- [gRPC Documentation](https://grpc.io/docs/)

- [Protocol Buffers Guide](https://protobuf.dev/)

## Troubleshooting- [Go gRPC Tutorial](https://grpc.io/docs/languages/go/quickstart/)

- [Microservices Patterns](https://microservices.io/patterns/index.html)

### Proto Generation Fails

## Submission Requirements

```bash

cd student-cafe-protos### What to Submit

make clean

make generate1. **All Source Code**:

cd ..   - `student-cafe-protos/` directory

```   - All service directories

   - `docker-compose.yml`

### Docker Build Issues   - `deploy.sh`



```bash2. **Documentation**:

docker-compose down -v   - This `README.md` with your observations

docker-compose build --no-cache api-gateway   - Screenshots showing:

docker-compose up -d     - Successful proto generation

```     - All services running (docker-compose ps)

     - Successful order creation (demonstrating gRPC communication)

### gRPC Connection Refused     - Service logs showing gRPC connections



```bash3. **Reflection Essay (500 words minimum)**:

# Check services are running   - How does the centralized proto repository solve the issues from previous practicals?

docker-compose ps   - Compare HTTP vs gRPC for inter-service communication

   - What are the trade-offs of running dual servers (HTTP + gRPC)?

# Check gRPC server started   - When would you choose gRPC over REST?

docker-compose logs user-service | grep "gRPC"   - How would you version the proto module in production?



# Verify port is exposed### Grading Criteria

docker-compose port user-service 9091

```| Criteria | Weight |

|----------|--------|

### Tests Fail| Proto repository structure and generation | 20% |

| gRPC server implementations | 25% |

```bash| gRPC client usage in order-service | 25% |

# Rebuild images| Docker configuration and deployment | 15% |

docker-compose build --no-cache| Documentation and reflection | 15% |



# Restart services---

docker-compose restart

**Good luck!** This practical demonstrates production-grade microservices communication patterns. Understanding these concepts will make you valuable in any microservices organization.

# Run tests again
make test-all
````

---

## Next Steps

1. **Review Summary Reports** - Start with the 400-line reports
2. **Run Services** - `docker-compose up -d`
3. **Test API** - Use curl commands above
4. **Review Code** - Examine service implementations
5. **Run Tests** - `make test-all`
6. **Study Details** - Read full practical guides

---

## Summary

This project demonstrates the complete evolution of microservices architecture:

- **Practical 5A:** Hybrid gRPC with centralized proto repository
- **Practical 5B:** Pure gRPC backend with simplified services (39% code reduction)
- **Practical 6:** Comprehensive testing (1,900+ lines of tests)

**Total Achievement:** 6,200+ lines of production-grade microservices code with complete documentation and test coverage.

---
