# Flutter Web — Deploy to GitHub Pages

**Repo:** `SharlanAndy/cuddly-waddle`  
**Live URL:** `https://sharlanandy.github.io/cuddly-waddle/`  
**Backend API:** `https://api.iotareward.com/api`

## Build & Deploy

```bash
# 1. Go to Flutter project
cd /Users/khoo/Documents/GitHub/project17/apps/mobile

# 2. Build for web (GitHub Pages base-href + API URL)
flutter build web --release \
  --base-href /cuddly-waddle/ \
  --dart-define=API_BASE_URL=https://api.iotareward.com/api \
  --dart-define=WS_BASE_URL=https://api.iotareward.com

# 3. Copy build output to GitHub Pages repo
cp -r build/web/* /Users/khoo/Documents/GitHub/cuddly-waddle/

# 4. Commit and push
cd /Users/khoo/Documents/GitHub/cuddly-waddle
git add -A
git commit -m "Deploy: <describe changes>"
git push origin main
```

## Notes

- `--base-href /cuddly-waddle/` is required for GitHub Pages sub-path routing
- `API_BASE_URL` must end with `/api` (the NestJS global prefix)
- `WS_BASE_URL` must NOT end with `/api` (Socket.IO connects at root)
- `404.html` = copy of `index.html` for SPA deep-link refresh support
- GitHub Pages takes ~1 min to propagate after push
