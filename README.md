# 🚀 Functional Blog CMS

**Modular Content Creation Powerhouse**

A revolutionary content management system that combines the best open-source tools into a unified, AI-ready platform.

## 🌟 Features

### Core System
- **Real-time File Watching** - Automatic content sync with MarkText integration
- **Multi-Site Publishing** - One content source → multiple branded websites
- **Metadata Extraction** - Intelligent front matter parsing
- **API-First Architecture** - RESTful endpoints for all operations

### AI Integration Ready
- **Llama4 Scout & Maverick** support
- **DeepSeek Coder** integration
- **Code Llama** compatibility  
- **Image Generation** pipeline

### Backup & Resilience
- **Cloudflare D1/R2** backup database and storage
- **Supabase** alternative backend
- **Retool** admin dashboard integration
- **SQLite** primary local storage

### Development Tools
- **Void IDE** integration for development environment
- **PDF to Markdown** converter
- **Health monitoring** and status dashboards
- **WSL/Ubuntu** optimized for Linux deployment

## 🏗️ Architecture

```
Content Creation Layer
├── MarkText (Editor)
├── PDF→Markdown (Converter) 
├── Void IDE (Development)
└── Video Upload (Media)

Integration Layer  
├── File Watcher (Auto-sync)
├── API Gateway (Routing)
├── Webhooks (Events)
└── Sync Scripts (Automation)

Data Management Layer
├── NocoDB (Database UI)
├── Appwrite (Backend API) 
├── Ghost CMS (Publishing)
└── SQLite (Storage)
```

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- WSL/Ubuntu (recommended)
- MarkText editor

### Installation
```bash
# Clone the repository
git clone https://github.com/mikeschlottig/functional-blog-cms.git
cd functional-blog-cms

# Install dependencies
npm install

# Setup environment
npm run setup

# Run tests
npm run test

# Start the CMS
npm start
```

## 📚 Documentation

- [**Setup Guide**](./docs/setup-guide.md) - Complete local setup and testing
- [**API Documentation**](./docs/api-documentation.md) - All endpoints and integrations
- [**Chatbot Training**](./docs/chatbot-training.md) - Website chatbot configuration
- [**Void IDE Integration**](./docs/void-ide-integration.md) - Development environment setup
- [**Cloud Migration**](./docs/cloud-migration.md) - VPS deployment guide

## 🎯 Use Cases

### LEVERAGE AI
- Technology blog content
- AI research articles
- Technical documentation
- Company announcements

### Daley Organics
- Agricultural content
- Organic farming guides
- Local SEO articles
- Community resources

### VoIP Sales
- Product documentation
- Feature comparisons
- ROI calculators
- Customer success stories

## 🛠️ Tech Stack

- **Backend**: Node.js, Express, SQLite
- **CMS**: Ghost CMS (multi-instance)
- **Database**: NocoDB, Appwrite
- **File Processing**: Chokidar, PDF converters
- **Backup**: Cloudflare D1/R2, Supabase
- **Development**: Void IDE, WSL/Ubuntu
- **Deployment**: VPS, Docker ready

## 🔮 Future Roadmap

### Phase 1: Local Development ✅
- [x] File watching system
- [x] API endpoints
- [x] Database integration
- [x] Health monitoring

### Phase 2: AI Integration (In Progress)
- [ ] Llama4 Scout integration
- [ ] DeepSeek Coder setup
- [ ] Image generation pipeline
- [ ] Content AI assistance

### Phase 3: Cloud Deployment
- [ ] VPS deployment scripts
- [ ] Container orchestration
- [ ] Production monitoring
- [ ] Scaling automation

### Phase 4: Advanced Features
- [ ] Real-time collaboration
- [ ] Advanced analytics
- [ ] Multi-language support
- [ ] Plugin ecosystem

## 🤝 Contributing

This is a LEVERAGE AI project. Built for innovation, scalability, and AI-first content management.

## 📄 License

MIT License - Built with love for the open source community

---

**Built by LEVERAGE AI** - Empowering businesses through innovative AI solutions
