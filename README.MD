# Module 8 - Reflection

---

### 1. Unary vs Server Streaming vs Bi-Directional Streaming
- **Unary**: One request, one response.  
  *Use when you only need a simple reply (e.g., fetch user info).*
- **Server Streaming**: One request, many responses.  
  *Good for sending a list or updates (e.g., live logs).*
- **Bi-Directional Streaming**: Multiple requests/responses at the same time.  
  *Great for real-time apps like chat or games.*

### 2. Security Considerations in Rust gRPC
- **Authentication**: Use TLS with client/server certs or tokens.
- **Authorization**: Check user roles before handling requests.
- **Encryption**: Enable TLS to protect data in transit.

### 3. Challenges with Bi-Directional Streaming
- Handling multiple users and connections at once.
- Managing shared state safely (e.g., chat room messages).
- Backpressure or slow clients can affect performance.

### 4. Pros and Cons of `ReceiverStream`
**Advantages:**
- Simple way to stream from a `tokio::mpsc` channel.
- Fits async Rust pattern well.

**Disadvantages:**
- Buffer size must be managed.
- Error handling and shutdown logic can get complex.

### 5. Structuring Code for Modularity
- Use modules (`mod`) for services, models, and utils.
- Traits for service logic to allow swapping/mock implementations.
- Keep proto logic separate from business logic.

### 6. Improving MyPaymentService
- Add checks to ensure input data (like card number and amount) is valid.

- Integrate with external payment systems and handle potential failures from those systems.

- Include transaction logging, retry strategies, and rollback functionality to ensure data consistency.

- Implement fraud prevention measures and support a variety of payment methods or currencies.


### 7. gRPC's Architectural Impact
gRPC enables efficient binary communication and strong typing with Protobuf, boosting performance and developer confidence. It supports multiple languages but might need adapters for systems using REST/JSON. Its schema-first design promotes clear API contracts and ensures consistent evolution.









### 8. HTTP/2 vs HTTP/1.1 (and WebSockets)
**HTTP/2 (used by gRPC):**
- Multiplexed streams (faster, no head-of-line blocking).
- Built-in support for streaming.

**HTTP/1.1/WebSocket:**
- Simpler but less efficient for many small messages.
- WebSocket adds complexity for real-time features.

### 9. REST vs gRPC Streaming
- REST: Request-response only, needs polling for updates.
- gRPC: Real-time communication via streaming.

### 10. Protobuf vs JSON
- **Protobuf**: Smaller, faster, strict schema (better for backend/backend).
- **JSON**: Human-readable, more flexible (better for frontend/backend).

