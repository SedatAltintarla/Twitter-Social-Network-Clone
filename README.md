# Twitter-Social-Network-Clone

```mermaid
flowchart TD
  subgraph Backend [Spring Boot API]
    A["Controller (PostController, LikeController, AuthController, etc.)"]
    B["Service Layer (PostService, LikeService, FeedbackService)"]
    C["Repository Layer (PostRepository, LikeRepository, etc.)"]
    D["Domain Entities (Post, PostLike, Feedback, User, BaseEntity)"]
    E["Security (JwtFilter, SecurityConfig)"]
    F["File Storage (FileStorageService)"]
  end

  subgraph Frontend [React UI]
    G["Components (TweetCard, TweetForm, HomePage, RegisterPage, etc.)"]
    H["API Client (swagger-typescript-api)"]
  end

  subgraph Database [PostgreSQL]
    I[(Datenbank)]
  end

  %% Beziehungen im Backend
  A --> B
  B --> C
  C --> D
  D --> I
  F --> I
  E --> A

  %% Beziehungen Frontend
  G -- "HTTP Requests" --> H
  H -- "REST API" --> A
