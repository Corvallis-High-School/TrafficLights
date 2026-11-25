# Modernization Plan: TrafficLights Container and Java Runtime Modernization

**Project**: processing-starter (TrafficLights)

---

## Technical Framework

- **Language**: Java 25 minimum (previously Java 21)
- **Framework**: Processing Core (4.5.7)
- **Build Tool**: Maven 3.9+
- **Key Dependencies**: Processing Core 4.5.7, JUnit Jupiter 5.11.0
- **Compatibility Strategy**: Target Java 25; validate Java 25 and 27 separately.

---

## Overview

This plan modernizes the TrafficLights Processing application. The project previously targeted Java 21 and lacks a Dockerfile. The team uses Java 21, 25, and 27, and has selected Java 25 as the minimum:

- Target **Java 25** to allow Java 25 language features and APIs.
- Provide containerization for portability while preserving desktop use.
- Scan and remediate identified dependency vulnerabilities.

Team members on Java 21 need a separate JDK 25 or the rebuilt development container. Java 27 compatibility must be verified, not assumed.

The migration follows a phased approach:
1. **Upgrade Phase**: Target Java 25 and validate on Java 25 and 27.
2. **Security Phase**: Scan and remediate any vulnerable dependencies
3. **Containerization Phase**: Create production-ready Dockerfile for portability

---

## Migration Impact Summary

| Application | Original Service | New Azure Service | Authentication | Comments |
|-------------|------------------|-------------------|---|---|
| processing-starter | Java 21 | None requested | N/A | Target Java 25 |

---

## Modernization Approach

### Phase 1: Java Compatibility Upgrade
- Target Java 25 in Maven and in the development container.
- Validate builds and tests on Java 25 and Java 27.
- Keep features and APIs within Java 25 unless the minimum changes again.

### Phase 2: Security & Dependency Management
- Scan Maven dependencies for CVEs and security vulnerabilities
- Remediate vulnerable packages to ensure a secure codebase

### Phase 3: Containerization
- Generate a production-ready Dockerfile for portability
- Enable the ability to run in containers when needed (future Azure deployment, CI/CD pipelines, etc.)
- Configure multi-stage build to optimize image size

---

## Success Criteria

- **Build**: Project compiles successfully with Maven on Java 25 and 27.
- **Testing**: Existing tests pass on Java 25 and 27.
- **Compatibility**: Java 25 is the minimum; Java 21 is not supported.
- **Security**: No critical or high-severity CVEs in dependencies
- **Dockerfile**: Containerization produces a usable Docker image without removing local desktop support.

---

## Open Questions & Questionnaire

- [x] Minimum Java version: 25, selected by the user.
- [x] Primary environment: local desktop; containerization is required.
