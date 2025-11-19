# Digital Menu Studio – Export Kits

This folder contains **generated menu bundles** ready for deployment.  
Each subfolder or file was created by the Editor’s “Export” button.

## How to Use

### Single-File Export (e.g., `menu-player.html`)
- **What**: One HTML file with everything (menu data, images, styles) embedded.
- **Use case**: Air-gapped TVs, USB sticks, or simple hosting.
- **Deploy**:
  1. Copy the `.html` file to a USB or web server.
  2. Open in a browser (e.g., Chrome on a smart TV).
- **Updates**: Re-export from Editor and replace the file.

### Folder Bundle (e.g., `downtown-location/`)
- **What**: `index.html` + `menu.json` + optional `assets/` with images.
- **Use case**: Live remote menus or when you want smaller files.
- **Deploy**:
  1. Upload the entire folder to a web server or CDN.
  2. Point the Player to `index.html` or a config URL like `https://yourcdn.com/downtown-location/menu.json`.
- **Updates**: Replace only `menu.json` for quick changes.

## Need Help?
See `/docs/deployment-guide.md` or ping us at support@yourchain.com.

© 2025 Accel Analysis, LLC