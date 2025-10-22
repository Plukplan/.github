<div align="center">

# Plukplan

**Modern web application development with hybrid human-AI engineering**

[![Next.js](https://img.shields.io/badge/Next.js-15.5.4-black?style=flat&logo=next.js&logoColor=white)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Infrastructure](https://img.shields.io/badge/IaC-OpenTofu-844FBA?style=flat&logo=terraform&logoColor=white)](https://opentofu.org)
[![Hetzner Cloud](https://img.shields.io/badge/Cloud-Hetzner-D50C2D?style=flat&logo=hetzner&logoColor=white)](https://www.hetzner.com)

[Architecture](../webapp/docs/architecture/README.md) • [Infrastructure](../infrastructure/README.md) • [Team](../webapp/README.md#-our-team)

</div>

---

## About Plukplan

Plukplan is a modern web application project demonstrating how **hybrid human-AI engineering** can deliver production-grade software rapidly while maintaining quality and best practices.

### Philosophy

> **Human creativity + AI capabilities = rapid development with consistent quality**

We blend human strategic thinking with AI-powered development, where every architectural decision is human-approved but AI-assisted. This approach enables us to:

- 🚀 Ship features faster without sacrificing quality
- 📚 Maintain comprehensive documentation as we build
- 🔍 Ensure consistent code reviews and best practices
- 🎯 Focus human expertise on strategy and AI on implementation

---

## Project Structure

This organization consists of three main repositories:

### [📱 webapp](../webapp)

Full-stack Next.js web application with modern architecture:

- **Framework**: Next.js 15.5 with App Router and React 19
- **Language**: TypeScript with strict typing
- **Database**: PostgreSQL 16 with Prisma ORM
- **Authentication**: NextAuth.js v5 with role-based authorization
- **Styling**: Tailwind CSS 4.x with shadcn/ui components
- **API**: tRPC v11 for type-safe API layer
- **Email**: Resend for transactional emails with React Email
- **Storage**: S3-compatible object storage (Hetzner)
- **Testing**: Playwright for E2E testing
- **CI/CD**: GitHub Actions with automated releases

**Key Features:**
- Role-based access control (Admin, User)
- User activity monitoring and analytics
- Email verification system
- S3 file upload functionality
- Admin dashboard with user management
- Comprehensive documentation with ADRs and requirements

[→ View webapp documentation](../webapp/README.md)

### [🏗️ infrastructure](../infrastructure)

Infrastructure as Code for cloud resources and deployment:

- **IaC Tool**: OpenTofu (Terraform-compatible)
- **Cloud Provider**: Hetzner Cloud (Nuremberg datacenter)
- **Deployment**: Self-hosted Coolify PaaS
- **Architecture**: Three-tier setup (Management, Application, Database)
- **Network**: Private network with floating IPs
- **Security**: Multi-layer firewall with database lockdown
- **Cost**: ~€42/month (~€50 with VAT)

**Infrastructure Highlights:**
- Coolify server for deployment management
- Dedicated application server (CX32: 4 vCPU, 8GB RAM)
- Dedicated database server (CX32: 4 vCPU, 8GB RAM)
- Private network for secure inter-server communication
- Automated daily backups
- Production-ready with high availability

[→ View infrastructure documentation](../infrastructure/README.md)

### [👥 team](../team)

Team management application (Python-based, in development)

---

## Technology Stack

<table>
<tr>
<td valign="top" width="50%">

### Frontend & Framework
- Next.js 15.5 (App Router)
- React 19
- TypeScript 5.x
- Tailwind CSS 4.x
- shadcn/ui components
- Radix UI primitives

### API & Data
- tRPC v11 (type-safe APIs)
- Tanstack Query (React Query)
- Prisma ORM
- PostgreSQL 16
- Zod validation

</td>
<td valign="top" width="50%">

### Authentication & Email
- NextAuth.js v5
- Role-based authorization
- Resend email service
- React Email templates
- Email verification

### Infrastructure & DevOps
- OpenTofu (IaC)
- Hetzner Cloud
- Coolify (self-hosted PaaS)
- Docker & Docker Compose
- GitHub Actions

</td>
</tr>
</table>

---

## Our Team

**Hybrid human-AI engineering:** Where Bobbie leads the strategy, AI agents write the code, and everyone reviews together.

<div align="center">

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| 👨‍💼<br/>**Bobbie**<br/>🎯 Lead Engineer<br/><sub>Strategy & oversight</sub> | <img src="https://www.anthropic.com/images/icons/safari-pinned-tab.svg" width="60" height="60" alt="Claude"/><br/>**Claude**<br/>💻 Senior Dev<br/><sub>Full-stack development</sub> | <img src="https://www.cursor.com/brand/icon.svg" width="60" height="60" alt="Cursor"/><br/>**Cursor**<br/>🤖 Developer<br/><sub>IDE-native coding</sub> | <img src="https://openai.com/favicon.ico" width="60" height="60" alt="Codex"/><br/>**Codex**<br/>🔧 Developer<br/><sub>Experimental features</sub> | <img src="https://coderabbit.ai/favicon.ico" width="60" height="60" alt="CodeRabbit"/><br/>**CodeRabbit**<br/>🔍 Reviewer<br/><sub>Automated PR reviews</sub> | <img src="https://github.githubassets.com/images/modules/site/copilot/copilot.png" width="60" height="60" alt="Copilot"/><br/>**Copilot**<br/>👁️ Reviewer<br/><sub>Code suggestions</sub> |

</div>

**How we work:**
- Human defines requirements and architecture
- AI agents implement features with documentation
- Automated code reviews (CodeRabbit)
- Human approves all decisions and merges
- Every line of code is human-approved but AI-assisted

---

## Production Infrastructure

**Live on Hetzner Cloud** with self-hosted Coolify deployment platform

### Architecture Overview

```
┌─────────────────────────────────────────────────────────┐
│              Hetzner Cloud (Nuremberg)                  │
│                                                         │
│  ┌──────────────────────────────────────────────────┐  │
│  │         Private Network (10.0.0.0/16)            │  │
│  │                                                  │  │
│  │  ┌─────────────┐  ┌──────────────┐  ┌─────────┐ │  │
│  │  │   Coolify   │  │ Application  │  │Database │ │  │
│  │  │   Server    │→│   Server     │→│ Server  │ │  │
│  │  │  CX22 2/4GB │  │  CX32 4/8GB  │  │CX32 4/8│ │  │
│  │  │  + 50GB Vol │  │  Traefik     │  │+100GB  │ │  │
│  │  └─────────────┘  └──────────────┘  └─────────┘ │  │
│  │  Floating IP      Floating IP       Floating IP  │  │
│  │  49.13.33.134     49.13.39.243      116.203.11.8│  │
│  └──────────────────────────────────────────────────┘  │
│                                                         │
│  Security: Multi-tier firewalls • Database SSH-only    │
└─────────────────────────────────────────────────────────┘
```

### Infrastructure Details

- **Management**: Coolify dashboard at `https://dashboard.plukplan.nl`
- **Application**: Next.js app at `https://www.plukplan.nl` (when deployed)
- **Database**: PostgreSQL 16 on isolated server (private network only)
- **Cost**: €42.28/month (~€50 with VAT)
- **Backups**: Automated daily database backups
- **Security**: Three-tier firewall, database completely locked down

[→ Full infrastructure details](../webapp/README.md#-production-environment)

---

## Documentation & Knowledge Base

We maintain comprehensive documentation as we build:

### Architecture Decisions (ADRs)
Documents recording significant technical choices, trade-offs, and rationale:
- [Adopt NextAuth.js v5](../webapp/docs/architecture/adr/ADR-20251009-adopt-nextauth-js-v5-for-authentication.md)
- [Role-based Authorization](../webapp/docs/architecture/adr/ADR-20251010-role-based-authorization-strategy.md)
- [tRPC v11 Adoption](../webapp/docs/architecture/adr/ADR-20251014-trpc-v11-adoption.md)
- [Resend for Email](../webapp/docs/architecture/adr/ADR-20251016-adopt-resend-for-email-service.md)
- [Hetzner S3 Storage](../webapp/docs/architecture/adr/ADR-20251021-hetzner-s3-storage.md)

### Feature Requirements
Specifications defining what features should do and why:
- [User Authentication System](../webapp/docs/architecture/requirements/REQ-20251009-user-authentication-system.md)
- [Monitor User Activity](../webapp/docs/architecture/requirements/REQ-20251015-monitor-user-activity.md)
- [Book Upload System](../webapp/docs/architecture/requirements/REQ-20251021-book-upload-system.md)

### Vibe Sessions
Real-time implementation logs documenting the development journey:
- [Database & CI Configuration](../webapp/docs/vibe/sessions/VIBE-SESSION-20251009-1245-database-mount-configuration-and-ci-work.md)
- [GitHub Actions Rebuild](../webapp/docs/vibe/sessions/VIBE-SESSION-20251009-1626-github-actions-build-from-ground-up.md)
- [S3 Book Upload](../webapp/docs/vibe/sessions/VIBE-SESSION-20251021-1200-s3-book-upload.md)

[→ Browse all documentation](../webapp/docs/)

---

## Development Workflow

### Quick Start

```bash
# Navigate to webapp
cd webapp

# One-command setup
cp .env.example .env.local && \
docker-compose --profile dev up postgres -d && \
npm run db:migrate && \
npm run dev
```

**Done!** Open http://localhost:3000

[→ Detailed setup guide](../webapp/QUICKSTART.md)

### Development Practices

**Git Workflow:**
- Conventional commits (`feat:`, `fix:`, `docs:`, etc.)
- Automated releases based on branch prefixes
- CodeRabbit AI reviews on all PRs

**AI Agent Workflow:**
- Read session checklist before starting
- Create documentation BEFORE coding
- Track work with todo lists
- Update session logs as progress happens
- Link ADRs ↔ Requirements ↔ PRs ↔ Sessions

**Code Quality:**
- ESLint with Next.js config
- TypeScript strict mode
- Playwright E2E tests
- Automated CI/CD checks

[→ Full development guide](../webapp/DEVELOPMENT.md) • [→ AI agent workflow](../webapp/docs/AI_AGENT_WORKFLOW.md)

---

## Key Features

### Authentication & Authorization
- ✅ Email/password authentication with NextAuth.js v5
- ✅ Email verification system
- ✅ Role-based access control (Admin/User)
- ✅ Protected routes and API endpoints

### User Management
- ✅ Admin dashboard with user overview
- ✅ User activity monitoring and analytics
- ✅ User registration and profile management
- ✅ Activity tracking (logins, page views)

### Infrastructure
- ✅ Production deployment on Hetzner Cloud
- ✅ Automated backups and high availability
- ✅ S3-compatible object storage
- ✅ Email service with Resend
- ✅ Type-safe API layer with tRPC

### Developer Experience
- ✅ Hot reloading with Turbopack
- ✅ Type-safe database with Prisma
- ✅ Component library with shadcn/ui
- ✅ Comprehensive documentation
- ✅ Automated testing with Playwright

---

## Repository Links

- **Web Application**: [../webapp](../webapp)
- **Infrastructure**: [../infrastructure](../infrastructure)
- **Team App**: [../team](../team)

---

## Getting Started

1. **Clone the repositories**
   ```bash
   cd plukplan
   ```

2. **Set up the webapp**
   ```bash
   cd webapp
   cp .env.example .env.local
   docker-compose --profile dev up postgres -d
   npm install
   npm run db:migrate
   npm run dev
   ```

3. **Explore the codebase**
   - Browse [architecture decisions](../webapp/docs/architecture/adr/)
   - Read [feature requirements](../webapp/docs/architecture/requirements/)
   - Check [session logs](../webapp/docs/vibe/sessions/)

4. **Deploy to production** (optional)
   ```bash
   cd infrastructure
   # Follow infrastructure README for deployment
   ```

---

## Project Stats

- **Tech Stack**: 20+ modern technologies
- **Documentation**: 30+ ADRs, requirements, and session logs
- **Infrastructure**: 3 servers, private network, automated backups
- **Cost**: ~€50/month for production infrastructure
- **Development Model**: Hybrid human-AI engineering
- **Code Quality**: Automated reviews, strict TypeScript, E2E tests

---

## License

Private project

---

<div align="center">

**Built with ❤️ using hybrid human-AI engineering**

Bobbie + Claude + Cursor + CodeRabbit + Copilot

</div>
