# tauri-vite-react-template

![Preview](https://github.com/user-attachments/assets/6eed8cce-c69c-43a1-87b0-8d297067dbaa)

A starter template for building cross-platform desktop apps with Tauri, Vite, and React.

---

This template includes:

- React 19
- Vite
- Tauri 2
- Tailwind CSS
- React Router
- Example starter page and greet flow

## Prerequisites

Before running the app, make sure you have:

- Node.js 18+ or newer
- npm
- Rust and Cargo
- Tauri prerequisites for your platform

For most setups, install the required Tauri dependencies from the official [Tauri documentation](https://tauri.app/start) for your OS.

## Quick start

Install dependencies:

```bash
npm install
```

Start the app in development mode:

```bash
npm run tauri dev
```

Alternatively, run the frontend only:

```bash
npm run dev
```

Build the desktop app for production:

```bash
npm run tauri build
```

## Project structure

```text
.
├── public/                 # Static assets
├── src/                   # React application
│   ├── assets/            # Images / static frontend assets
│   ├── pages/             # Page components
│   ├── App.jsx            # App router setup
│   ├── main.jsx           # React entry point
│   └── index.css          # Global styles
├── src-tauri/             # Tauri application
│   ├── icons/             # App icons
│   ├── src/               # Rust backend
│   ├── Cargo.toml         # Rust package metadata
│   ├── tauri.conf.json    # Tauri app configuration
│   └── ...                # Generated files and build config
├── index.html             # Vite HTML entry
├── package.json           # Node package metadata and scripts
├── vite.config.js         # Vite config with Tauri settings
├── .gitignore
├── LICENSE
└── README.md
```

## Template customization checklist

This template still contains several placeholder values that should be changed before using it as your own app.

### 1. Update package metadata

Edit `package.json` and change:

- `"name"` to your app name
- `"version"` to your app version
- any package metadata you want to keep

Example:

```json
{
  "name": "my-desktop-app",
  "version": "0.1.0"
}
```

### 2. Update the Rust package name

Edit `src-tauri/Cargo.toml` and change:

- `name = "appname"` to your app name
- `description = "App Description"` to your app description
- `authors = ["Developer Name"]` to your name or team
- `version = "0.1.0"` if needed

Example:

```toml
[package]
name = "my-desktop-app"
version = "0.1.0"
description = "My desktop application"
authors = ["Jane Doe"]
edition = "2021"
```

Also update the library name if needed:

```toml
[lib]
name = "my_desktop_app_lib"
crate-type = ["staticlib", "cdylib", "rlib"]
```

### 3. Update the Rust entry point

Edit `src-tauri/src/main.rs` and replace the placeholder library name:

```rust
fn main() {
    appname_lib::run()
}
```

with:

```rust
fn main() {
    my_desktop_app_lib::run()
}
```

Make sure the Rust library name matches the one in `Cargo.toml`.

### 4. Update Tauri app metadata

Edit `src-tauri/tauri.conf.json` and change the values below:

- `"productName"`: app name shown to the user
- `"identifier"`: reverse-DNS bundle identifier, for example `com.company.appname`
- `"title"`: window title
- `"publisher"`: your name or publisher
- `"copyright"`: copyright string
- `"homepage"`: GitHub or website link
- `"longDescription"` / `"shortDescription"`: app summary
- `"category"`: app category
- `"icon"` paths if you replace icons

Example:

```json
{
  "productName": "My Desktop App",
  "identifier": "com.company.mydesktopapp",
  "app": {
    "windows": [
      {
        "title": "My Desktop App"
      }
    ]
  },
  "bundle": {
    "publisher": "Jane Doe",
    "copyright": "2026 © Jane Doe",
    "homepage": "https://github.com/janedoe/my-desktop-app",
    "longDescription": "My Desktop App",
    "shortDescription": "A cross-platform desktop app"
  }
}
```

### 5. Update the app UI

The starter UI is in:

- `src/App.jsx`
- `src/pages/Home.jsx`

Replace the example welcome page and route configuration with your app’s own navigation and screens.

### 6. Replace default branding and assets

Update or replace:

- `public/` static files
- `src/assets/`
- `src-tauri/icons/`

These assets are used for logos, icons, and app branding.

### 7. Update the app name in the frontend if needed

The template uses placeholder strings such as:

- `"App Name"`
- `"appname"`
- `"Developer Name"`
- `"App Description"`

Search the project for these values and update them to match your app.

## Common search values to replace

Use a project-wide search for:

- `appname`
- `App Name`
- `Developer Name`
- `App Description`
- `com.developer.appname`

This will help you identify all the places that still use template-specific values.

## Running the app

For development:

```bash
npm run tauri dev
```

For production build:

```bash
npm run tauri build
```

To preview the frontend only:

```bash
npm run dev
```

## License

This template is provided under the project license in this repository. Please check the `LICENSE` file for details.

## Notes

This template is intentionally minimal so you can customize it for your own Tauri app. The main places to edit are:

- `package.json`
- `src-tauri/Cargo.toml`
- `src-tauri/src/main.rs`
- `src-tauri/tauri.conf.json`
- `src/App.jsx`
- `src/pages/Home.jsx`

Once those are updated, the app is ready for your own project structure, custom screens, and desktop app logic.
