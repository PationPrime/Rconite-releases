# Rconite

<p align="center">
  <img src="docs/readme-assets/logo/rconite_raccoon_app_icon.png" alt="Rconite logo" width="180">
</p>

<p align="center">
  A desktop admin tool for Rust servers with RCON connectivity, live map support, player management, permissions, commands, and a built-in FTP/FTPS/SFTP client.
</p>

<p align="center">
  <img src="docs/readme-assets/dashboard.png" alt="Rconite dashboard">
</p>

## What Is Rconite

**Rconite** gives Rust server administrators a full visual control panel instead of relying only on a raw RCON console. It brings together server monitoring, world map tools, player management, permissions, chat, server commands, configuration editing, and remote file access in one place.

It is especially useful for servers where admins need to react quickly to live events: inspect player inventories, teleport to players, moderate chat, monitor the world map, update configuration, and manage files without constantly switching between separate tools.

## Key Features

- Connect to a Rust server over RCON and save connection profiles.
- Support for `RconiteDataPlugin.cs` for player inventory access and enhanced live map data.
- Visual dashboard with core server status information.
- Interactive live map with grid, monuments, and real-time player tracking.
- Player management: inventory, item giving, stats, and moderation.
- Permission group management with members and assigned permissions.
- In-game chat monitoring and direct admin actions from the UI.
- Live RCON server console.
- On-demand and scheduled commands, including outdated command tracking.
- Structured server configuration editing by section.
- Installed plugin viewer with compile error visibility.
- Built-in FTP, FTPS, and SFTP client for server file management.
- App language and theme settings.
- Donation screen for supporting the project.

## Quick Start

### 1. Install RconiteDataPlugin

Copy [`plugins/RconiteDataPlugin.cs`](plugins/RconiteDataPlugin.cs) into the `oxide/plugins` directory on your Rust server.

This plugin is used for:

- reading player inventories;
- getting additional data for the live map;
- tighter integration between the application and in-game server data.

### 2. Create a Server Configuration

On first launch, you can either create a saved server profile or enter server details and connect immediately.

<p align="center">
  <img src="docs/readme-assets/add-server-configuration.png" alt="Add server configuration" width="48%">
  <img src="docs/readme-assets/server-connect.png" alt="Server connect" width="48%">
</p>

The connection uses:

- server IP address;
- RCON port;
- RCON password;
- Steam API key.

### 3. Prepare the Map for Live Map

The main killer feature of the application, the interactive **live map**, requires a rendered world map image from the server.

To add a map:

1. Run the `world.rendermap` command on the server.
2. Obtain the generated map image.
3. Upload it through the Rconite interface.

<p align="center">
  <img src="docs/readme-assets/dashboard-upload-map.png" alt="Dashboard upload map">
</p>

## Main Workflows

### 1. Dashboard

The dashboard gives you a fast operational overview of the server:

- server name;
- online players and player limit;
- queue and joining players;
- network input and output;
- server time;
- entity count;
- memory and system memory usage;
- collections;
- server version;
- quick access to the map and scheduled commands.

<p align="center">
  <img src="docs/readme-assets/dashboard.png" alt="Dashboard overview">
</p>

### 2. Interactive Live Map

The live map displays the server world in an interactive view with the ability to:

- open the full map in a dedicated mode;
- enable or disable the grid;
- adjust grid and label opacity;
- show monuments;
- track a player position on the map;
- use additional data provided through `RconiteDataPlugin`.

<p align="center">
  <img src="docs/readme-assets/realtime-live-map-1.png" alt="Realtime live map full">
</p>

<p align="center">
  <img src="docs/readme-assets/realtime-live-map-2.png" alt="Realtime live map player tracking">
</p>

### 3. Players

The players section brings the most important admin actions together in one screen.

#### Player Information and Inventory

You can open a player card, view their SteamID, connection address, and current inventory across `belt`, `wear`, and `main` containers, and quickly remove items.

<p align="center">
  <img src="docs/readme-assets/player-inventory.png" alt="Player inventory">
</p>

#### Give Items

The built-in item catalog lets you browse Rust items by category, set quantities, and send selected items directly to a player from the app.

<p align="center">
  <img src="docs/readme-assets/player-give-items.png" alt="Player give items">
</p>

#### Player Moderation

Available quick admin actions:

- `Kill`
- `Kick`
- `Ban`
- `Unban`
- `Mute`
- `Unmute`
- teleport to player

<p align="center">
  <img src="docs/readme-assets/player-moderation.png" alt="Player moderation">
</p>

#### Player Statistics

A dedicated tab shows combat and gameplay statistics:

- kills;
- deaths;
- K/D;
- suicides;
- PvP and PvE stats;
- building-related activity;
- full stat reset.

<p align="center">
  <img src="docs/readme-assets/player-stats.png" alt="Player stats">
</p>

### 4. Permission Groups

Rconite provides a visual way to manage the server permission system:

- browse existing groups;
- create and delete groups;
- view group members;
- add and remove members;
- assign permissions to groups;
- edit allowed permissions through a visual dialog.

<p align="center">
  <img src="docs/readme-assets/permissions.png" alt="Permissions management">
</p>

### 5. In-Game Chat

The chat section shows the real in-game server chat and lets admins interact with players without switching to another tool. You can respond quickly and apply moderation actions directly from the context menu.

Supported actions:

- `Kill`
- `Mute text chat`
- `Unmute text chat`
- `Kick`
- `Ban`
- `Unban`

<p align="center">
  <img src="docs/readme-assets/chat-moderation.png" alt="Chat moderation">
</p>

### 6. Live RCON Console

When you need full low-level control, the app includes a proper live RCON console. It is useful for reading logs, checking command responses, reviewing plugin output, and investigating server-side issues.

<p align="center">
  <img src="docs/readme-assets/console.png" alt="RCON console">
</p>

### 7. Commands

Rconite splits server commands into two main workflows:

- **On demand**: commands executed manually by the admin.
- **Scheduled**: commands planned to run at a specific time.

The scheduled tab also shows outdated entries, so admins can clearly see overdue tasks and avoid missing important actions.

<p align="center">
  <img src="docs/readme-assets/commands-on-demand.png" alt="On demand commands" width="48%">
  <img src="docs/readme-assets/commands-scheduled-outdated.png" alt="Scheduled and outdated commands" width="48%">
</p>

### 8. Server Configuration

Rconite includes a dedicated configuration module divided into clear sections.

#### Common Info

Edit the server cover image, name, description, URL, tags, and player limits.

<p align="center">
  <img src="docs/readme-assets/server-configuration-common-info.png" alt="Server configuration common info">
</p>

#### Map

View and manage the current world seed, size, and map-related configuration.

<p align="center">
  <img src="docs/readme-assets/server-configuration-map.png" alt="Server configuration map">
</p>

#### Security

Configure security-related and system-level values such as `VAC secure`, save interval, and other server settings.

<p align="center">
  <img src="docs/readme-assets/server-configuration-security.png" alt="Server configuration security">
</p>

#### Gameplay

Manage core gameplay rules such as:

- chat;
- PVE;
- radiation;
- instant craft;
- building stability;
- animal behavior;
- AFK kick settings;
- and other important gameplay values.

<p align="center">
  <img src="docs/readme-assets/server-configuration-gameplay.png" alt="Server configuration gameplay">
</p>

#### Entity Population

Visually manage the amount of different world entities by category:

- animals;
- vehicles;
- special and event-related entities.

<p align="center">
  <img src="docs/readme-assets/server-configuration-population-animals.png" alt="Population animals" width="32%">
  <img src="docs/readme-assets/server-configuration-population-vehicles.png" alt="Population vehicles" width="32%">
  <img src="docs/readme-assets/server-configuration-population-special.png" alt="Population special" width="32%">
</p>

Unsaved changes are clearly indicated, and the application lets you either apply them or discard them.

### 9. Server Plugins

The plugins tab shows:

- installed Oxide plugins;
- versions;
- authors;
- file sizes;
- response times;
- compile errors and problematic plugins.

This makes it easy to inspect the health of the plugin setup without manually browsing the server plugin directory.

<p align="center">
  <img src="docs/readme-assets/server-plugins.png" alt="Server plugins">
</p>

### 10. FTP, FTPS, and SFTP Client

Rconite can connect to the server file system over `FTP`, `FTPS`, and `SFTP`. That makes the app a single administration hub instead of forcing you to switch to a separate file client for simple tasks.

Supported operations:

- browse files and folders;
- navigate the remote file system;
- upload files to the server;
- download files;
- delete files;
- create folders;
- delete folders.

<p align="center">
  <img src="docs/readme-assets/server-ftp.png" alt="Server FTP" width="48%">
  <img src="docs/readme-assets/server-sftp.png" alt="Server SFTP" width="48%">
</p>

### 11. Settings

The settings screen currently includes the main user-facing options:

- interface language selection;
- app theme selection.

<p align="center">
  <img src="docs/readme-assets/settings-theme.png" alt="Settings theme">
</p>

### 12. Support the Project

The app includes a dedicated donations screen so users can support the continued development of the project.

<p align="center">
  <img src="docs/readme-assets/donations.png" alt="Donations">
</p>

## Who Rconite Is For

Rconite is a good fit if you want:

- a visual control center for your Rust server;
- fast control over players and chat;
- convenient world and map monitoring;
- one place to manage both configuration and server files;
- a tool that covers daily admin workflows without constant manual console work.

## Tech Stack

- Dart & Flutter
- WebSocket RCON
- Drift / SQLite
- FTP / FTPS / SFTP

## Important Note

For the full inventory-related and enhanced live map feature set, it is strongly recommended to use `plugins/RconiteDataPlugin.cs` on the Rust server inside the `oxide/plugins` directory.
