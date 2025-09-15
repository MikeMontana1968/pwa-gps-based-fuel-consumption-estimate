# 🚀 Deployment & Versioning Guide

This project uses automated version injection via GitHub Actions to keep the HTML version synchronized with git tags.

## 📋 How It Works

1. **Version Placeholders**: The HTML contains `{{VERSION}}` and `{{BUILD_DATE}}` placeholders
2. **Git Tags**: Create version tags like `v2.4.2` to trigger deployments
3. **GitHub Actions**: Automatically injects real versions and deploys to GitHub Pages
4. **Synchronized**: Version in footer always matches the git tag

## 🎯 Release Workflow

### For New Releases:

```bash
# 1. Make your changes and commit
git add .
git commit -m "🔧 Fix roll angle sensitivity"

# 2. Create and push a version tag
git tag v2.4.2
git push origin v2.4.2

# 3. GitHub Actions automatically:
#    - Replaces {{VERSION}} with v2.4.2
#    - Replaces {{BUILD_DATE}} with current timestamp
#    - Deploys to GitHub Pages
```

### For Development (Optional):

```bash
# Push to main branch - deploys with dev-{hash} version
git push origin main
```

## 📦 What Gets Deployed

**Version Tags (v\*):**
- Version: `v2.4.2`
- Footer: `v2.4.2 • Cornering Analytics Edition • Built 2024-01-15 14:30 UTC`

**Main Branch:**
- Version: `dev-a1b2c3d`
- Footer: `dev-a1b2c3d • Cornering Analytics Edition • Built 2024-01-15 14:30 UTC`

## 🔧 GitHub Actions Workflow

The workflow (`/.github/workflows/deploy.yml`) triggers on:
- **Tag pushes** matching `v*` pattern (production releases)
- **Main branch pushes** (development builds)

## 📝 Version Placeholders

In `index.html`, these placeholders get replaced:

```html
<!-- Version Footer -->
<div>{{VERSION}} • Cornering Analytics Edition • Built {{BUILD_DATE}}</div>

<!-- Export Metadata -->
appVersion: '{{VERSION}}'
```

## ⚙️ GitHub Pages Configuration

**IMPORTANT**: Ensure GitHub Pages is configured correctly:

1. Go to repository **Settings** → **Pages**
2. Under **Source**, select "Deploy from a branch"
3. Set branch to **gh-pages** (NOT main)
4. Save the configuration

**Why**: The workflow deploys processed files to `gh-pages` branch, but if Pages serves from `main`, you'll see unprocessed `{{VERSION}}` placeholders.

## 🎉 Benefits

✅ **Single Source of Truth**: Git tags control versions
✅ **No Manual Updates**: No more editing version numbers in code
✅ **Build Timestamps**: Know exactly when each version was built
✅ **Development Tracking**: Dev builds get unique identifiers
✅ **Synchronized**: HTML version always matches git history
✅ **Automatic Deployment**: Tag push triggers complete build and deploy