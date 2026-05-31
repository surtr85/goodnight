### **GoodNight** — Intelligent Sleep + Wake Scheduler for Linux

**GoodNight** lets you put your Linux machine into **hybrid-sleep** (suspend-to-RAM + hibernate) while setting a reliable hardware wake-up alarm via the RTC. Perfect for:

- Waking up your PC in the morning like a real alarm clock
- Scheduled downloads, backups, or renders while you sleep
- Energy-efficient overnight tasks with automatic wake-up
- Turning your desktop into a smart sleep device

---

### ✨ Features

- **Flexible time formats** — relative (`+3600`), absolute epoch, `08:30`, full datetime, or natural language (`"tomorrow 7:30"`)
- **Smart time handling** — automatically moves past times to tomorrow
- **Hybrid-sleep** with optional delay (great for logging out cleanly)
- **Hardware-level wake alarm** — survives power loss better than software timers
- **Safe & robust** — root checks, validation, clear error messages
- **Zero dependencies** — just bash and systemd

---

### 📥 Installation

```bash
# Clone the repo
git clone https://github.com/yourusername/goodnight.git
cd goodnight

# Make it executable and install system-wide
chmod +x good-night
sudo cp good-night /usr/local/bin/good-night

# Optional: Create a convenient alias
echo "alias goodnight='sudo good-night'" >> ~/.bashrc
source ~/.bashrc
```

---

### 🚀 Usage

```bash
# Basic usage
sudo good-night 08:30

# Sleep in 45 minutes
sudo good-night +2700

# Wake at a specific time tomorrow
sudo good-night "tomorrow 07:15"

# Full datetime
sudo good-night "2026-05-20 06:45:00"

# Wait 10 seconds before sleeping (e.g. for logout)
sudo good-night --delay 10 07:00
```

**Pro tip:** Add it to your shutdown/logout workflow!

---

### 📖 Examples

```bash
# Wake up in 8 hours
goodnight +28800

# Classic morning alarm
goodnight 07:00

# Natural language
goodnight "next monday 9am"

# For automated overnight tasks
goodnight "4:00" && systemctl hybrid-sleep
```

---

### 🔧 How It Works

1. Parses your desired wake time using `date -d`
2. Writes the Unix epoch timestamp to `/sys/class/rtc/rtc0/wakealarm`
3. Calls `systemctl hybrid-sleep` (suspend + hibernate)
4. The RTC hardware wakes the system at the exact time

---

### 📋 Requirements

- Linux with RTC wakealarm support (`/sys/class/rtc/rtc0/wakealarm`)
- Systemd
- Root/sudo privileges (required for writing to RTC)

Tested on Ubuntu, Fedora, Arch, and other modern distributions.

---

### 🛠️ Contributing

Contributions are welcome! Feel free to open issues or PRs for:
- Desktop integration (GUI, systemd service, etc.)
- Better error handling
- Support for `suspend-then-hibernate`

---

### 📜 License

MIT License — feel free to use, modify, and share.

---

### ❤️ Acknowledgments

Thank you for using **GoodNight**!  
May your computer rest well and wake up refreshed.

---

**Made with ❤️ for Linux power users who love elegant automation.**

---

### Ready to use?

```bash
git clone https://github.com/yourusername/goodnight.git
```

Would you like me to also generate:
- A cool ASCII logo / banner for the README?
- A `README.md` file with better markdown formatting?
- Desktop entry / systemd service suggestions?

Just say the word and I’ll refine it further! 🌙
