# 🚀 Ubuntu/WSL Setup Guide

## Perfect Setup for Functional Blog CMS

Now that you have WSL Ubuntu set up, here are the **perfect commands** for getting started:

### 1. Navigate to Your Project
```bash
# From Ubuntu terminal, navigate to your Windows project folder
cd /mnt/c/Users/mikes/functional-blog-cms
```

### 2. Create Directory Structure
```bash
# Create all directories (this works perfectly in Ubuntu!)
mkdir -p content/{drafts,published,assets,imports}
mkdir -p services config scripts data logs backups models void-ide-extensions
```

### 3. Initialize Project
```bash
# Initialize npm project
npm init -y

# Install core dependencies
npm install appwrite @tryghost/admin-api axios chokidar express form-data sqlite3 ws dotenv cors helmet

# Install backup provider dependencies
npm install @supabase/supabase-js @aws-sdk/client-s3

# Install development dependencies
npm install -D nodemon jest @types/node
```

### 4. Create Environment File
```bash
cat > .env << 'EOF'
# ========================================
# DATABASE CONFIGURATION
# ========================================
DATABASE_TYPE=sqlite
SQLITE_FILE=./data/functional-cms.db
SQLITE_WAL_MODE=true

# ========================================
# CMS API CONFIGURATION
# ========================================
CMS_API_PORT=3001
CMS_API_HOST=localhost
CMS_API_SECRET=will-be-generated
VOID_IDE_BRIDGE_PORT=3002

# ========================================
# FILE SYSTEM CONFIGURATION
# ========================================
CONTENT_ROOT_DIR=./content
CONTENT_DRAFTS_DIR=./content/drafts
CONTENT_PUBLISHED_DIR=./content/published
CONTENT_ASSETS_DIR=./content/assets

# ========================================
# PDF CONVERSION (Your existing service)
# ========================================
PDF_CONVERTER_HOST=localhost
PDF_CONVERTER_PORT=3000
PDF_CONVERTER_ENDPOINT=/api/convert

# ========================================
# DEVELOPMENT FLAGS
# ========================================
NODE_ENV=development
LOG_LEVEL=info
WATCH_ENABLED=true

# Backup providers (optional for testing)
CLOUDFLARE_D1_TOKEN=
SUPABASE_URL=
SUPABASE_ANON_KEY=
RETOOL_API_KEY=
EOF
```

### 5. Create Package.json
```bash
cat > package.json << 'EOF'
{
  "name": "functional-blog-cms",
  "version": "1.0.0",
  "description": "Modular content creation powerhouse",
  "main": "index.js",
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js",
    "setup": "node scripts/setup-environment.js",
    "test": "node scripts/quick-test.js",
    "health": "curl -s http://localhost:3001/health | json_pp"
  },
  "dependencies": {
    "appwrite": "^13.0.0",
    "@tryghost/admin-api": "^1.13.0",
    "@supabase/supabase-js": "^2.38.0",
    "@aws-sdk/client-s3": "^3.450.0",
    "axios": "^1.6.0",
    "chokidar": "^3.5.3",
    "express": "^4.18.2",
    "form-data": "^4.0.0",
    "sqlite3": "^5.1.6",
    "ws": "^8.14.2",
    "dotenv": "^16.3.1",
    "cors": "^2.8.5",
    "helmet": "^7.1.0"
  },
  "devDependencies": {
    "nodemon": "^3.0.1",
    "jest": "^29.7.0",
    "@types/node": "^20.8.0"
  }
}
EOF
```

### 6. Next Steps

After creating the basic structure:

1. **Copy the core files** from the repository
2. **Run setup script**: `npm run setup`
3. **Test everything**: `npm run test`
4. **Start the CMS**: `npm start`

## What This Gives You

✅ **Perfect Linux environment** for AI model integration  
✅ **All original bash commands work** - no more syntax issues  
✅ **Production-ready setup** - identical to your future VPS  
✅ **AI model compatibility** - Ready for Llama4, DeepSeek, etc.  
✅ **Docker support** - When we containerize everything  
✅ **Professional workflow** - Industry standard development environment  

## Ready to Build!

Now you have the **perfect foundation** for:
- Building the complete CMS locally
- Testing all integrations
- Adding AI models seamlessly
- Deploying to production VPS

**Let's get this incredible system running!** 🔥
