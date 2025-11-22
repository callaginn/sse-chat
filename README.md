# SSE Real-time Messenger
A real-time chat application using Server-Sent Events (SSE) for instant message delivery.

## 🎯 Quick Start

1. **Setup**: Follow [SETUP.md](SETUP.md) to configure DDEV
2. **Access**: http://sse.ddev.site

## 📁 Project Structure

```
sse-chat/
├── public/
│   ├── index.php           # Main chat interface
│   ├── sse-server.php      # SSE event stream
│   ├── receiver.php        # Message receiver endpoint
│   ├── assets/             # CSS and JavaScript
│   └── data/
│       └── messages.json   # Message storage
├── .ddev/                  # DDEV configuration
└── SETUP.md                # Setup and testing guide
```

## 🚀 How It Works

This real-time chat application uses Server-Sent Events (SSE) for instant message delivery between multiple users or browser tabs.

### Architecture

1. **Client connects** to `sse-server.php` via JavaScript `EventSource` API
2. **Server streams events** using `text/event-stream` format
3. **Messages are stored** in `messages.json` for persistence across sessions
4. **Each tab has unique identity** (via sessionStorage) for multi-user support
5. **Heartbeat signal** (every 2.5 seconds) keeps connections alive and detects disconnections
6. **New messages broadcast** instantly to all connected clients

### Event Types

- `connected` - Initial connection established
- `message` - New message received (triggers display)
- `heartbeat` - Keep-alive signal (prevents timeouts, confirms server responsiveness)

### Key Features

- ✅ Real-time updates (< 100ms latency)
- ✅ Persistent message history
- ✅ Multiple users/tabs support
- ✅ Automatic reconnection on disconnect
- ✅ Modern, responsive UI

## 🎨 Customization

### Message History Limit

Edit `public/sse-server.php`:
```php
$maxMessages = 100; // Change this value
```

### Polling Interval

Edit `public/sse-server.php`:
```php
usleep(500000); // 0.5 seconds (500ms)
```

### Styling

Customize the appearance in `public/assets/styles.css`.
