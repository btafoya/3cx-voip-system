# 3CX VoIP System - Project Documentation

## Project Overview

The 3CX VoIP System project provides a comprehensive knowledge base and administrative guide for 3CX IP PBX (Private Branch Exchange) systems. 3CX is a software-based VoIP telephone system that handles voice calls, call routing, queues, multichannel communication including phone, chat, WhatsApp, SMS, and Facebook Messenger, and provides a browser-based Web Client interface for unified communications.

**Project Type:** Documentation & Knowledge Base
**Primary Purpose:** Administrative guide and end-user reference for 3CX PBX configuration, management, and usage
**License:** 3CX Documentation (proprietary vendor documentation + custom skill)

---

## Documentation Statistics

| Component | Lines | Status |
|-----------|-------|--------|
| SKILL.md | 989 | Complete |
| KNOWLEDGE_BASE.md | 818 | Complete |
| README.md | 302 | Complete |
| PROJECT_INDEX.md | 348 | Complete |
| **Total** | **2,457** | - |

---

## Directory Structure

```
3cx-voip-system/
├── .claude/
│   └── plugins/
│       └── 3cx-voip-system/
│           └── SKILL.md                   # Main administrative skill guide (989 lines)
├── 3cx-documentation/                      # Official 3CX HTML documentation
│   ├── ImportExtensionTemplateV20.csv     # Bulk import template
│   ├── Setup Your Team.html               # User creation and roles
│   ├── Call Queues & Ring Groups.html     # Queue configuration
│   ├── Call Routing Office Hours & IVR.html  # Time-based routing
│   ├── Configuring IP Phones.html         # Phone provisioning
│   ├── Configuring a SIP Trunk.html       # Trunk setup
│   ├── Importing Extensions in Bulk.html  # CSV import guide
│   ├── Caller ID Reformatting.html        # Number formatting
│   ├── Busy Lamp Fields.html              # BLF configuration
│   ├── Manage Customer Queries.html       # Multichannel setup
│   ├── PBX Dial Codes.html                # Dial code reference
│   ├── 3CX Phone System Parameters Table.html  # System parameters
│   ├── How to Migrate to 3CX Hosted.html  # Cloud migration guide
│   ├── 3CX Web Client.html                # Web client end-user guide
│   └── *.png                              # Supporting screenshots (60+ images)
├── .git/                                  # Git repository
├── 3cx-voip-system.skill                  # Distribution package (ZIP archive)
├── README.md                              # Project overview and quick start (302 lines)
├── PROJECT_INDEX.md                       # This file (348 lines)
├── KNOWLEDGE_BASE.md                      # Detailed knowledge base by topic (818 lines)
└── memory/
    └── MEMORY.md                          # Quick reference memory file
```

---

## Core Components

### 1. Skill File (`SKILL.md`)

**Location:** `.claude/plugins/3cx-voip-system/SKILL.md` (989 lines)

The primary knowledge base containing comprehensive 3CX administration and end-user guidance:

| Section | Description |
|---------|-------------|
| **Quick Start** | Navigation table mapping user intents to sections |
| Users & Extensions | Creating users with detailed roles, assigning phones, extension types, Groups |
| **3CX Talk & Meet Links** | NEW: WebRTC-based calling links, Meet links for video conferencing |
| Call Queues & Ring Groups | Queue configuration, ring strategies, statistics |
| Call Routing & IVR | Office hours, holidays, digital receptionists |
| IP Phone Configuration | Provisioning methods (RPS, PnP, DHCP), SBC setup |
| SIP Trunk Configuration | Trunk setup, codec preferences |
| Bulk Import | CSV template format, Microsoft 365 integration |
| Caller ID Formatting | Number format transformation rules |
| Busy Lamp Fields (BLF) | Button monitoring and speed dial |
| Advanced Call Routing | Multi-level IVR, DID routing, conditional routing, call forwarding |
| Multichannel Communication | Live Chat, WhatsApp, Facebook, SMS/MMS, unified queues |
| **3CX Web Client Usage** | Login, PWA installation, Click2Call, status management, calling, **Conference Calls** |
| Advanced Troubleshooting | Audio issues, registration failures, database queries |

---

### Skill File - Detailed Section Breakdown

#### Users & Extensions
- Creating users with role selection (7 role types defined)
- Assigning IP phones with MAC address and provisioning method
- Extension types reference (dn_type codes 0, 1, 2, 5, 13)
- **Groups**: Language, timezone, office hours, Mini IVR

#### 3CX Talk & Meet Links (NEW)
- Talk links: WebRTC-based weblinks for browser calling
- User vs Company Talk links
- Meet links: Ad-hoc video conferencing
- Spam prevention (Name/Email request)
- Editing friendly names

#### Call Queues & Ring Groups
- Queue vs Ring Group comparison
- Ring strategies (Ring All, Linear, Circular, Least Recent, Random)
- Queue configuration (wait time, size, wrap-up, failover)
- Queue statistics and reports

#### Call Routing & IVR
- Office hours with break times
- Holidays configuration
- Office hours override
- Digital Receptionist (IVR) with audio format requirements
- Multi-level IVR menus

#### IP Phone Configuration
- Provisioning methods: RPS, PnP, DHCP Option 66, SBC/Router Phone
- Router phone models list (Fanvil, Snom, Yealink)
- STUN configuration
- Manual phone configuration

#### SIP Trunk Configuration
- Standard vs 3CX Tunnel trunk types
- SIP server, domain, outbound proxy
- Authentication credentials
- Codec preferences

#### Bulk Import
- CSV template format
- Key fields (Number, FirstName, LastName, Email, Mobile, etc.)
- **Microsoft 365 integration** (dedicated instances)

#### Caller ID Formatting
- Inbound/outbound formatting rules
- Common format patterns (International, National, E.164)

#### Busy Lamp Fields (BLF)
- Monitoring other extensions
- Speed dial and call pickup buttons

#### Advanced Call Routing
- Multi-level IVR structures
- DID routing strategies
- Conditional routing (caller ID, time, day, trunk)
- Queue overflow strategies
- Call recording configuration
- Call privacy options

#### Multichannel Communication
- Live Chat integration with web widget
- WhatsApp Business API
- Facebook Messenger
- SMS/MMS with provider setup
- Unified queues for all channels

#### 3CX Web Client Usage
- **Login steps** (NEW)
- PWA installation (Chrome, Edge)
- Click2Call browser extension
- Notifications management
- Making & managing calls
- **Conference Calls** (NEW): Adding participants, managing conference
- Status & Boss-Secretary State
- Auto-switch status by working hours
- Caller ID exceptions
- Team view
- Chat features
- Contacts management
- Video conferencing

#### Advanced Troubleshooting
- Audio quality issues (one-way audio, choppy audio, echo)
- Call dropping
- Registration failures
- Queue issues
- IVR issues
- SIP trunk issues
- Network issues (ports, firewall, QoS)
- Database queries
- Log file analysis
- Performance issues

**Extension Types Reference:**
- `dn_type=0` - Extension
- `dn_type=1` - External Line/Trunk
- `dn_type=2` - Ring Group/Queue
- `dn_type=5` - Voicemail
- `dn_type=13` - Inbound Routing

### 2. Documentation Directory (`3cx-documentation/`)

Contains official 3CX HTML documentation files:

| File | Topics Covered |
|------|----------------|
| `Setup Your Team.html` | User creation, extension assignment |
| `Call Queues & Ring Groups.html` | Queue setup, ring strategies |
| `Call Routing Office Hours & IVR.html` | Time-based routing, IVR menus |
| `Configuring IP Phones.html` | Phone provisioning methods |
| `Configuring a SIP Trunk.html` | External line setup |
| `Importing Extensions in Bulk - CSV File Structure.html` | Bulk user import |
| `Caller ID Reformatting.html` | Number format rules |
| `Busy Lamp Fields.html` | BLF button configuration |
| `Manage Customer Queries Live Chat WhatsApp Facebook and SMS-MMS.html` | Multichannel setup |
| `PBX Dial Codes - How to use them directly from your phone.html` | Dial code reference |
| `3CX Phone System Parameters Table.html` | System parameters reference |
| `How to Migrate to 3CX Hosted.html` | Cloud migration guide |
| `3CX Web Client.html` | Web client end-user guide (NEW) |

### 3. CSV Template (`ImportExtensionTemplateV20.csv`)

Bulk import template for creating users and extensions. Key fields include:

| Field | Required | Description |
|-------|----------|-------------|
| Number | Yes | Extension number |
| FirstName | Yes | User's first name |
| LastName | Yes | User's last name |
| EmailAddress | Yes | User email |
| MAC | No | Phone MAC address for provisioning |
| Model | No | Phone model (e.g., Yealink T43U) |
| Template | No | Provisioning template file |
| Role | No | User role (users, receptionist, manager) |
| Department | No | Department assignment |

### 4. Distribution Package (`3cx-voip-system.skill`)

A ZIP archive containing the `SKILL.md` file for distribution and installation in other systems.

**Extension Types Reference:**
| Code | Type | Description |
|------|------|-------------|
| 0 | Extension | Individual user |
| 1 | External Line/Trunk | SIP trunk or provider |
| 2 | Ring Group/Queue | Call distribution group |
| 5 | Voicemail | Voicemail box |
| 13 | Inbound Routing | DID routing rules |

**User Roles Reference:**
| Role | Level | Key Capabilities |
|------|-------|------------------|
| User | Basic | Own account only, own calls, presence view |
| Receptionist | Group | Override office hours, group operations (divert, transfer, pickup, park, intercom) |
| Group Administrator | Group | Admin view for Call handling/SIP Trunks/channels, no reports/recordings |
| Manager | Group | User config, create users, elevate roles, reports, recordings, Listen in/Barge |
| Owner | Group | Full Group Admin + Manager, elevate to Manager/Group Admin within group |
| System Administrator | System (dedicated) | See everything, no Listen/Barge, cannot make others System Admin/Owner |
| System Owner | System (dedicated) | Full System Admin + Listen/Barge/recordings, elevate to System roles |

---

### 5. README.md (302 lines)

Project overview with:
- **3CX Talk & Meet Links** section: Talk links for browser calling, Meet links for video conferencing
- Quick start common tasks with links to skill sections
- Bulk user import instructions
- Technical reference (extension types, ports, STUN, audio requirements)
- Router phone models
- **Conference Calls** in Web Client features
- Enhanced Status & Forwarding options
- Troubleshooting quick reference
- Database reference with sample queries
- Log file location

### 6. KNOWLEDGE_BASE.md (818 lines)

Detailed knowledge base organized by major topics:
- Getting Started
- User Management (with enhanced roles table)
- **3CX Talk & Meet Links** (NEW)
- Call Handling
- Call Routing & IVR
- Phone Configuration
- Trunk Configuration
- Multichannel Communication
- Web Client Usage (with **Conference Calls**, Login steps)
- Troubleshooting
- Advanced Configuration
- Network Requirements
- Database Queries
- File Locations

---

## Quick Reference: Configuration Workflows

### Adding a New User

1. Go to **Users** → **Add User**
2. Enter name, extension number, email, password
3. Select user role (7 types available: User, Receptionist, Group Administrator, Manager, Owner, System Administrator, System Owner)
4. Select **Main Group Membership** (optional, dedicated systems)
5. Click **Save**
6. User receives email with account details

### Setting Up 3CX Talk & Meet Links

**User Talk Links:**
1. User logs in to Web Client
2. Go to **Settings > General**
3. Edit "friendly name" for Talk link
4. Add to email signature

**Company Talk Links:**
1. Go to **Admin > Call handling**
2. Select Call Queue or Ring Group
3. Edit company Talk link settings

**Meet Links:**
- Share user's Meet link: `https://[pbx]/meet/[username]/`
- Configure spam prevention (request Name/Email)

### Provisioning an IP Phone

1. Select user → Click **IP Phone** tab
2. Click **Configure a phone**
3. Select model → Enter MAC address (no dashes/colons)
4. Choose connection method:
   - **RPS** - Remote Provisioning Service (recommended)
   - **PnP** - Plug and Play (on-prem only)
   - **DHCP Option 66** - Managed networks
   - **SBC/Router Phone** - Cloud 3CX with on-site phones
5. Click **Add phone**

### Setting Up a Call Queue

1. Go to **Admin > Call handling** → **+ Add Queue**
2. Configure queue number, name, and members
3. Set ring strategy (Ring All, Linear, Circular, etc.)
4. Configure wait time, queue size, wrap-up time
5. Set failover destination
6. Upload announcements (welcome, hold music, position)
7. Click **Save**

### Configuring Office Hours

1. Go to **Admin > Office hours**
2. Set opening hours and breaks
3. Assign DIDs with destinations for:
   - During office hours
   - Out of office hours
   - During break
4. Set holidays in **Set your Holidays** section

### Installing Web Client as PWA (Chrome)

1. Login to Web Client
2. Click download icon in address bar
3. Click **Install**
4. Enable launch at startup: `chrome://apps` → right-click 3CX → enable

### Installing Web Client as PWA (Edge)

1. Login to Web Client
2. Click icon in address bar
3. Click **Install**
4. Enable **Pin to taskbar** and **Auto-start on device login**

### Starting a Conference Call from Web Client

1. Start or receive a call
2. Click **Conference** button
3. Enter name or number to add
4. Choose **Add directly** (immediate) or **Consultative** (announce first)
5. Click **Add** to include participant
6. Repeat to add more participants

**Conference Management:**
- View all participants
- Mute individual participants
- Remove participants
- Drop individual callers while keeping conference
- Transfer entire conference to another extension

### Logging In to Web Client

1. Navigate to your 3CX Web Client URL
2. Enter email address and password
3. Click **Login**
4. Select preferred device/browser for calls if prompted

---

## Technical Reference

### Network Ports

| Port | Protocol | Purpose |
|------|----------|---------|
| 5001 | TCP/HTTPS | Web management |
| 5060 | UDP/TCP | SIP signaling |
| 5061 | TCP/TLS | Secure SIP (tunnels) |
| 5090 | UDP/TCP | Secure SIP (local) |
| 9000-9049 | UDP | RTP audio |

### Audio Requirements for IVR Prompts

- **Format:** WAV, PCM, 8 kHz, 16-bit, Mono
- **Avoid:** MP3 format
- **Forbidden characters:** `< > : " / \ | ? * &`

### Router Phone Models (for Cloud 3CX)

**Fanvil:** V64, V65, V62, X4U-V2, X5U-V2, X6U-V2, X7-V2, X7C-V2, X210-V2, X210i-V2
**Snom:** D862, D865
**Yealink:** T53, T53C, T53W, T54W, T57W

### STUN Server

```
stun.3cx.com:3478
```

### Click2Call Extension Links

- **Chrome:** https://chrome.google.com/webstore/detail/3cx-click2call/baipgmmeifmofkcilhccccoipmjccehn
- **Edge:** https://microsoftedge.microsoft.com/addons/detail/3cx-click2call/kcijpkomlnpfpjmkbghnnmflfebimpfg

---

## Database Tables (for Advanced Debugging)

| Table | Purpose |
|-------|---------|
| `cl_calls` | Call summary records |
| `cl_participants` | Extension/queue/trunk details |
| `cl_segments` | Call flow paths |
| `cdroutput` | Full CDR records |
| `audit_log` | Configuration changes |

### Sample Queries

```sql
-- Recent calls to extension 100
SELECT * FROM cl_calls
WHERE id IN (
    SELECT call_id FROM cl_segments
    WHERE dst_part_id IN (
        SELECT id FROM cl_participants
        WHERE dn = '100' AND dn_type = 0
    )
)
ORDER BY start_time DESC
LIMIT 20;

-- Failed calls
SELECT * FROM cl_calls
WHERE is_answered = false
ORDER BY start_time DESC
LIMIT 20;

-- Recent configuration changes
SELECT * FROM audit_log
ORDER BY time_stamp DESC
LIMIT 50;
```

---

## Troubleshooting Reference

| Issue | Common Cause | Solution |
|-------|--------------|----------|
| Phone not registering | Wrong MAC address | Verify MAC (no dashes/colons) |
| Calls not reaching queue | Office hours closed | Check office hours configuration |
| Poor audio quality | Network/NAT issues | Enable STUN or use SBC |
| One-way audio | RTP ports blocked | Forward ports 9000-9049 or use SBC |
| Calls dropping | NAT timeout | Enable SIP keepalive (30-60s) |
| IVR not responding | Wrong audio format | Convert to WAV 8kHz 16-bit Mono |
| Trunk registration fails | Incorrect credentials | Verify with provider |
| Web Client not loading | Browser compatibility | Try Chrome/Edge, clear cache |

---

## Related Skills

The 3CX VoIP System skill is automatically triggered when users ask about:

- 3CX configuration
- Setting up extensions (including 7 user role types)
- Configuring call routing
- Managing queues
- Setting up IVR/digital receptionists
- Provisioning IP phones
- Configuring SIP trunks
- Importing extensions in bulk (CSV, Microsoft 365)
- Advanced routing scenarios
- Multichannel communication (Live Chat, WhatsApp, Facebook, SMS)
- **Web Client installation and usage**
- **3CX Talk & Meet links**
- **Click2Call browser extension**
- **Status management and team view**
- **Conference calls**
- **Video conferencing**
- **Call forwarding options**
- Troubleshooting audio/registration/call issues
- VoIP PBX configuration
- Phone system setup
- Call management topics

---

## Cross-References

- **Skill File:** `.claude/plugins/3cx-voip-system/SKILL.md`
- **Official Docs:** `3cx-documentation/` (12 HTML files)
- **CSV Template:** `3cx-documentation/ImportExtensionTemplateV20.csv`
- **Distribution Package:** `3cx-voip-system.skill`
- **Knowledge Base:** `KNOWLEDGE_BASE.md`
- **Project README:** `README.md`
- **Memory File:** `memory/MEMORY.md`

---

## Skill Description (Frontmatter)

The skill includes comprehensive descriptions for automatic triggering:

```
Guide users through 3CX VoIP PBX administration and configuration tasks,
plus end-user Web Client usage. Use this skill whenever the user asks about
3CX configuration, setting up extensions, configuring call routing, managing
queues, setting up IVR/digital receptionists, provisioning IP phones,
configuring SIP trunks, importing extensions in bulk, advanced routing
scenarios, multichannel communication (Live Chat, WhatsApp, Facebook, SMS),
troubleshooting audio/registration/call issues, installing/using the Web
Client app, Click2Call extension, managing status and team view, or any
other 3CX administration or end-user task.
```

---

## Last Updated

2026-03-09

## Version Information

- Documentation Source: 3CX Official Documentation (V20+)
- Skill Version: Custom aggregation for Claude Code
- 3CX Version Reference: V20+ (based on CSV template filename)

---

## Update History

### 2026-03-09 - Major Documentation Update

**Total Lines Added:** 266 lines across 4 documentation files

**New Content Added:**

1. **3CX Talk & Meet Links Section**
   - Talk links: WebRTC-based weblinks for browser calling
   - User vs Company Talk links with examples
   - Meet links: Ad-hoc video conferencing
   - Spam prevention (Name/Email request)
   - Editing friendly names

2. **Conference Calls Section**
   - Starting conferences from Web Client
   - Adding participants (direct vs consultative)
   - Conference management (mute, remove, drop, transfer)

3. **Enhanced User Roles**
   - Expanded from 4 to 7 role types
   - Detailed role capabilities table
   - System Administrator and System Owner for dedicated instances

4. **Groups Section**
   - Purpose and configuration steps
   - Mini IVR feature per group
   - Main Group Membership concept

5. **Enhanced Bulk Import**
   - CSV format details
   - Microsoft 365 integration (dedicated instances)

6. **Web Client Enhancements**
   - Login steps
   - Enhanced forwarding options (9 destinations)
   - Auto-switch status details (Available/DND/Away)
   - Also ring my mobile, Accept multiple calls

**Files Updated:**
| File | Before | After | Change |
|------|--------|-------|--------|
| SKILL.md | 874 | 989 | +115 lines |
| KNOWLEDGE_BASE.md | 701 | 818 | +117 lines |
| README.md | 268 | 302 | +34 lines |
| PROJECT_INDEX.md | 348 | 560 | +212 lines |
| **Total** | **2193** | **2669** | **+478 lines** |