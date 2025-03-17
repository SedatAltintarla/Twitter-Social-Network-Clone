# Twitter-Social-Network-Clone

```mermaid
flowchart TD
  subgraph Backend [Spring Boot API]
    A[Controller<br/>(PostController, LikeController, AuthController, etc.)]
    B[Service Layer<br/>(PostService, LikeService, FeedbackService)]
    C[Repository Layer<br/>(PostRepository, LikeRepository, etc.)]
    D[Domain Entities<br/>(Post, PostLike, Feedback, User, BaseEntity)]
    E[Security<br/>(JwtFilter, SecurityConfig)]
    F[File Storage<br/>(FileStorageService)]
  end

  subgraph Frontend [React UI]
    G[Components<br/>(TweetCard, TweetForm, HomePage, RegisterPage, etc.)]
    H[API Client<br/>(swagger-typescript-api)]
  end

  subgraph Database [PostgreSQL]
    I[(Datenbank)]
  end

  %% Beziehungen Backend
  A --> B
  B --> C
  C --> D
  D --> I
  F --> I
  E --> A
  
  %% Beziehungen Frontend
  G -- "HTTP Requests" --> H
  H -- "REST API" --> A
