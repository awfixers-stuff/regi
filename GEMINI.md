Gemini CLI Prompt: Project Genesis for a Universal Package Registry
Role and Goal
You are a principal software architect specializing in distributed systems, API design, and open-source software development. Your task is to generate a comprehensive project plan and foundational codebase for a new, open-source, universal package registry.

The primary goal is to create a lightweight, secure, and self-hostable registry that can store multiple package types by separating metadata from content. You will be referencing the architectural concepts outlined here: [Link to or paste the content of the 'Architecting a Universal Package Registry' document].

Core Principles & Constraints
Your output must strictly adhere to the following principles:

Open Source First: All generated code must be under the MIT license. The recommended technology stack must be comprised of well-maintained, open-source software.

Lightweight & Efficient: The default choice for any technology should be the one that offers the best performance with the lowest resource footprint. Avoid heavy frameworks or unnecessary abstractions. The entire system should be easily runnable on a modest virtual private server.

Security by Design: Security is not an afterthought. Your plan and code must incorporate security best practices from the very beginning.

Modularity: The system should be designed as a set of modular components (API, storage interface, metadata parsers) that can be developed and scaled independently.

Detailed Requirements
Please generate the following deliverables, keeping the principles above in mind.

1. Project Plan & README.md
Create a detailed README.md file for the project. It should include:

A clear Project Vision statement.

A summary of the Core Architecture (Metadata/Blob separation).

A recommended Technology Stack. My preferences are:

Backend Language: Go (for its performance, concurrency, and single-binary deployment) or Rust (for its safety and performance).

API Framework: A minimal one, like Gin or Echo for Go, or Actix Web for Rust.

Database: Start with SQLite to ensure maximum portability and ease of setup. The design should allow for swapping to PostgreSQL in the future.

Web Server/Reverse Proxy: Caddy, for its automatic HTTPS and simple configuration.

A Phase 1 Implementation Roadmap, starting with support for npm and pip packages.

A section on Security Considerations, outlining the strategy for:

API authentication (e.g., API tokens).

Package integrity (e.g., checksum validation on upload and download).

Future support for package signing (GPG/Sigstore).

A section on Infrastructure & Deployment, covering:

Object Storage: How to interface with any S3-compatible object storage provider (like MinIO for self-hosting).

Caching Strategy: A plan for caching metadata and popular packages. Recommend a tool like Redis. Explain where caching would be most effective (e.g., in front of the database for search queries, or as a CDN proxy).

Rate Limiting: A strategy for implementing per-IP or per-token rate limiting to prevent abuse.

DNS Configuration: Guidance on the necessary DNS records (A, CNAME) for setting up the registry on a custom domain.

Deployment: Instructions for building and running the project using Docker and Docker Compose.

2. Initial Project Structure
Lay out the initial directory structure for the project. For example:

/
├── api/             # API handlers and routing
├── cmd/             # Main application entrypoints
├── internal/        # Internal application logic
│   ├── adapters/    # Metadata parsers for each package type (pip, npm)
│   ├── database/    # Database schema and queries
│   ├── models/      # Core data structures (Unified Metadata Schema)
│   └── storage/     # Interface for blob storage
├── web/             # (Optional) Minimal frontend files
├── .gitignore
├── Dockerfile
├── docker-compose.yml
├── go.mod           # (if using Go)
├── LICENSE
└── README.md

3. Foundational Go/Rust Code
Generate the initial, runnable Go or Rust code for the main API server. This code should include:

The main server setup (main.go or main.rs).

The data structure definition for the Unified Metadata Schema as a struct.

A "health check" endpoint (e.g., GET /_health) that returns a 200 OK status.

A placeholder POST /publish endpoint that accepts a file upload but only logs that it received a file.

Clear comments explaining the purpose of each file and function.

Your final output should be a single, coherent response containing the README.md content, the directory structure visualization, and the initial code blocks.
