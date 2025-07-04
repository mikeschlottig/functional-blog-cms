# 📁 Project Structure

This document outlines the complete file structure for the Functional Blog CMS.

## 🗂️ Directory Layout

```
functional-blog-cms/
├── 📄 README.md                          # Main project documentation
├── 📄 package.json                       # Node.js dependencies and scripts
├── 📄 .env                              # Environment configuration
├── 📄 .gitignore                        # Git ignore rules
├── 📄 index.js                          # Main CMS entry point
│
├── 📁 content/                          # Content storage
│   ├── 📁 drafts/                      # Draft articles
│   ├── 📁 published/                   # Published content
│   ├── 📁 assets/                      # Images, media files
│   └── 📁 imports/                     # PDF imports for conversion
│
├── 📁 services/                         # Core services
│   ├── 📄 file-watcher.js               # File monitoring service
│   ├── 📄 api-manager.js                # Database connection manager
│   ├── 📄 health-monitor.js             # System health monitoring
│   ├── 📄 ghost-integration.js          # Ghost CMS integration
│   ├── 📄 nocodb-integration.js         # NocoDB integration
│   ├── 📄 pdf-converter.js              # PDF to markdown conversion
│   ├── 📄 void-ide-bridge.js            # Void IDE integration
│   └── 📄 backup-providers.js           # Cloudflare, Supabase backups
│
├── 📁 config/                           # Configuration files
│   ├── 📄 appwrite-setup.js             # Appwrite configuration
│   └── 📄 database-config.js            # Database configurations
│
├── 📁 scripts/                          # Utility scripts
│   ├── 📄 setup-environment.js          # Environment setup
│   ├── 📄 local-validator.js            # Local testing validator
│   ├── 📄 quick-test.js                 # Quick system test
│   ├── 📄 database-migration.js         # Database migrations
│   └── 📄 local-dev-start.js            # Development environment starter
│
├── 📁 data/                             # Database storage
│   ├── 📄 functional-cms.db             # SQLite database
│   └── 📁 backups/                     # Database backups
│
├── 📁 logs/                             # System logs
│   └── 📄 cms.log                       # Main log file
│
├── 📁 docs/                             # Documentation
│   ├── 📄 ubuntu-setup.md               # Ubuntu/WSL setup guide
│   ├── 📄 chatbot-training.md           # Chatbot configuration guide
│   ├── 📄 void-ide-integration.md       # Void IDE setup
│   ├── 📄 api-documentation.md          # API reference
│   ├── 📄 cloud-migration.md            # VPS deployment guide
│   └── 📄 project-structure.md          # This file
│
├── 📁 void-ide-extensions/              # Void IDE extensions
│   ├── 📄 cms-integration.js            # CMS integration extension
│   └── 📄 project-layout.js             # Project layout configuration
│
└── 📁 models/                           # AI models (future)
    ├── 📁 llama/                       # Llama4 Scout/Maverick
    ├── 📁 deepseek/                    # DeepSeek Coder
    └── 📁 image-gen/                   # Image generation models
```

## 🔧 Core Files Description

### Main Application Files

| File | Purpose | Status |
|------|---------|---------|
| `index.js` | Main CMS entry point, Express server, API routes | ⭐ Critical |
| `package.json` | Dependencies, scripts, project metadata | ⭐ Critical |
| `.env` | Environment variables, API keys, configuration | ⭐ Critical |

### Service Files

| File | Purpose | Status |
|------|---------|---------|
| `services/file-watcher.js` | Monitors content files for changes | ⭐ Critical |
| `services/api-manager.js` | Manages all database connections | ⭐ Critical |
| `services/health-monitor.js` | System health and monitoring | ⭐ Critical |
| `services/ghost-integration.js` | Ghost CMS publishing | 🔄 Integration |
| `services/nocodb-integration.js` | NocoDB database interface | 🔄 Integration |
| `services/pdf-converter.js` | PDF to markdown conversion | 🔄 Integration |
| `services/void-ide-bridge.js` | Void IDE development bridge | 🔄 Integration |
| `services/backup-providers.js` | Cloudflare, Supabase backups | 🔄 Integration |

### Configuration Files

| File | Purpose | Status |
|------|---------|---------|
| `config/appwrite-setup.js` | Appwrite backend configuration | 🔄 Integration |
| `config/database-config.js` | Database connection settings | 🔄 Integration |

### Scripts

| File | Purpose | Status |
|------|---------|---------|
| `scripts/setup-environment.js` | Initial environment setup | ⭐ Critical |
| `scripts/local-validator.js` | Comprehensive system testing | ⭐ Critical |
| `scripts/quick-test.js` | Fast system validation | ⭐ Critical |
| `scripts/database-migration.js` | Database schema migrations | 🔄 Integration |
| `scripts/local-dev-start.js` | Development environment launcher | 🔄 Integration |

## 📝 Content Structure

### Markdown Front Matter Format

```yaml
---
title: \"Article Title\"
status: draft|review|published|archived
sites: [\"leverage-ai\", \"daley-organics\", \"voip-sales\"]
tags: \"tag1, tag2, tag3\"
meta_description: \"SEO description\"
image: \"path/to/featured/image.jpg\"
created: 2025-07-04T10:00:00Z
updated: 2025-07-04T15:30:00Z
---
```

### Content Types

| Type | Directory | Purpose |
|------|-----------|---------|
| Drafts | `content/drafts/` | Work-in-progress articles |
| Published | `content/published/` | Ready for publication |
| Assets | `content/assets/` | Images, videos, documents |
| Imports | `content/imports/` | PDFs for conversion |

## 🗄️ Database Schema

### SQLite Tables

```sql
-- Content metadata
CREATE TABLE content_metadata (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    title TEXT NOT NULL,
    file_path TEXT UNIQUE NOT NULL,
    content_type TEXT NOT NULL,
    status TEXT DEFAULT 'draft',
    tags TEXT,
    ghost_id TEXT,
    appwrite_id TEXT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP
);

-- Site configurations
CREATE TABLE site_configs (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    site_name TEXT UNIQUE NOT NULL,
    ghost_url TEXT NOT NULL,
    ghost_key TEXT NOT NULL,
    enabled BOOLEAN DEFAULT 1
);

-- Publishing queue
CREATE TABLE publishing_queue (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    content_id INTEGER,
    site_name TEXT,
    status TEXT DEFAULT 'pending',
    scheduled_at DATETIME,
    published_at DATETIME,
    error_message TEXT,
    FOREIGN KEY (content_id) REFERENCES content_metadata (id)
);

-- Backup providers
CREATE TABLE backup_providers (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    provider_name TEXT UNIQUE NOT NULL,
    provider_type TEXT NOT NULL,
    configuration TEXT,
    enabled BOOLEAN DEFAULT 0,
    last_sync DATETIME
);
```

## 🌐 API Endpoints

### Health & Status
- `GET /health` - System health check
- `GET /api/status` - Detailed system status
- `GET /api/test` - Basic connectivity test

### Content Management
- `GET /api/content` - List all content
- `GET /api/content/:status` - Filter content by status
- `POST /api/content` - Create new content
- `PUT /api/content/:id` - Update content
- `DELETE /api/content/:id` - Delete content

### Publishing
- `POST /api/publish` - Publish content to sites
- `POST /api/publish/:site` - Publish to specific site
- `GET /api/publish/queue` - View publishing queue

### Utilities
- `POST /api/convert-pdf` - Convert PDF to markdown
- `POST /api/sync-all` - Sync all content
- `GET /api/backup-status` - Check backup provider status

## 🔄 Development Workflow

### 1. Initial Setup
```bash
npm run setup     # Environment setup
npm run test      # Validation tests
```

### 2. Development
```bash
npm run dev       # Start development environment
npm start         # Start production mode
```

### 3. Content Creation
1. Create markdown file in `content/drafts/`
2. File watcher automatically detects changes
3. Metadata extracted and stored
4. Change status to \"published\" to publish

### 4. Testing
```bash
npm run test      # Full system test
npm run health    # Health check
```

## 🚀 Deployment Structure

### Local Development
- SQLite database
- File system storage
- Local API endpoints

### Production (VPS)
- PostgreSQL/MySQL database
- Cloud storage (Cloudflare R2)
- Load balancers
- AI model integration

## 📋 Status Legend

- ⭐ **Critical**: Essential for basic functionality
- 🔄 **Integration**: Connects external services
- 🤖 **AI**: AI model integration
- 📊 **Analytics**: Monitoring and metrics
- 🔒 **Security**: Authentication and authorization

This structure provides a complete, scalable foundation for the Functional Blog CMS!
