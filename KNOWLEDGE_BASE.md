# 3CX VoIP System - Knowledge Base

## Table of Contents

- [Getting Started](#getting-started)
- [User Management](#user-management)
- [3CX Talk & Meet Links](#3cx-talk--meet-links)
- [Call Handling](#call-handling)
- [Call Routing & IVR](#call-routing--ivr)
- [Phone Configuration](#phone-configuration)
- [Trunk Configuration](#trunk-configuration)
- [Multichannel Communication](#multichannel-communication)
- [Web Client Usage](#web-client-usage)
- [Troubleshooting](#troubleshooting)
- [Advanced Configuration](#advanced-configuration)

---

## Getting Started

### What is 3CX?

3CX is a software-based IP PBX that handles:
- Voice over IP (VoIP) calls
- Call routing and queuing
- Multichannel communication (Phone, Chat, WhatsApp, SMS, Facebook)
- Voicemail and IVR systems

### Quick Navigation

| Task | Section |
|------|---------|
| Add a user | [User Management](#user-management) |
| Set up a call queue | [Call Handling](#call-handling) |
| Configure office hours | [Call Routing & IVR](#call-routing--ivr) |
| Provision an IP phone | [Phone Configuration](#phone-configuration) |
| Add external phone line | [Trunk Configuration](#trunk-configuration) |
| Import multiple users | [Bulk Import](#bulk-import) |
| Use Web Client | [Web Client Usage](#web-client-usage) |
| Troubleshoot issues | [Troubleshooting](#troubleshooting) |

---

## User Management

### Creating a User

```
Admin Console → Users → Add User
```

**Required Fields:**
- First Name
- Last Name
- Extension Number (3-6 digits)
- Email Address
- Password

**User Roles:**
| Role | Capabilities |
|------|--------------|
| **User** | Basic role. Can only manage own account, see own calls, and view presence of others |
| **Receptionist** | Can override office hours for groups, see group calls, perform operations (divert, transfer, pickup, park, intercom) |
| **Group Administrator** | Has Admin view for Call handling, SIP Trunks, WhatsApp, Live chat. Cannot see reports/recordings, cannot Listen in or Barge in |
| **Manager** | Has Admin view, can configure user settings, create users and elevate roles. Can see reports/recordings, Barge in, Listen in |
| **Owner** | Full Group Admin + Manager capabilities. Can elevate users to Manager/Group Admin within own group. Can Barge in, Listen in, Whisper |
| **System Administrator** (dedicated only) | See everything for all groups and SIP trunks. Cannot Barge in/Listen in or make others System Admin/Owner |
| **System Owner** (dedicated only) - Can do everything System Admin can plus Barge in, Listen in, view recordings/reports. Only one who can elevate to System Admin/Owner |

### Assigning an IP Phone

1. Select user from **Users**
2. Click **IP Phone** tab
3. Click **Configure a phone**
4. Select phone model and enter MAC address
5. Choose provisioning method (see [Phone Configuration](#phone-configuration))
6. Click **Add phone**

### Extension Types (dn_type)

| Code | Type | Description |
|------|------|-------------|
| 0 | Extension | Individual user |
| 1 | External Line | SIP trunk/provider |
| 2 | Ring Group/Queue | Call distribution |
| 5 | Voicemail | Voicemail box |
| 13 | Inbound Routing | DID routing rules |

### Groups

**Purpose:** Group extensions to apply the same language, time zone, and office hours. All extensions start in the **Default** group.

**Creating a Group:**
```
Admin Console → Users → Groups → Add Group
```

1. Specify group name
2. Click **Add** in members section
3. Add members
4. Click **Save**

**Group Features:**
- Each group has its own **Mini IVR** for routing based on office hours
- Extension can be part of multiple groups, but follows **Main Group Membership** office hours

---

## 3CX Talk & Meet Links

### 3CX Talk Links

**What are they?**
- Weblinks that allow calling by clicking - no dialing or payment needed
- Works via WebRTC in any browser (computer or smartphone)
- No special app required

**Types of Talk Links:**
- **User Talk Links** - Each user gets their own link for email signatures
- **Company Talk Links** - Paste on website or company email signature

**Example Links:**
- User: `https://pbx002.3cx.cloud/mariajohnson/`
- Company: `https://pbx002.3cx.cloud/mycompany/`

**Editing Links:**
- **User Link:** Edit "friendly name" in **Settings > General**
- **Company Link:** Edit from **Admin > Call Handling** in Call Queue/Ring Group settings

### 3CX Meet Links

**Purpose:** Share link to let visitors go directly to your meeting room for ad-hoc video conferences

**Example:** `https://pbx002.3cx.cloud/meet/mariajohnson/`

**Spam Prevention:** Configure to request Name and Email first, then accept or reject based on that information.

---

---

## Call Handling

### Call Queues vs Ring Groups

| Feature | Call Queue | Ring Group |
|---------|-----------|------------|
| Callers wait in queue | Yes | No |
| Plays music/announcement | Yes | Yes |
| Reports statistics | Yes | Basic |
| Best for | Support centers | Small teams |

### Ring Strategies

| Strategy | Description |
|----------|-------------|
| Ring All | All members ring simultaneously |
| Linear | Members ring in order |
| Circular | Round-robin distribution |
| Least Recent | Member who hasn't answered longest |
| Random | Random member selection |

### Creating a Call Queue

```
Admin Console → Admin > Call handling → + Add Queue
```

**Configuration Steps:**
1. Set Queue Number (DN)
2. Enter Name (e.g., "Support Queue")
3. Add Members (extensions)
4. Select Ring Strategy
5. Configure:
   - Maximum wait time
   - Maximum queue size
   - Wrap-up time
   - Failover destination
6. Upload announcements (welcome, music on hold, position)
7. Click **Save**

### Queue Statistics

- Call volume per queue
- Average wait time
- Abandoned call rate
- Agent performance
- SLA compliance

---

## Call Routing & IVR

### Office Hours

```
Admin Console → Admin > Office hours
```

**Configuration:**
1. Click on days to set opening hours
2. Add break times (lunch, meetings)
3. Set time zone if different
4. Assign DIDs with destinations:
   - During office hours
   - Out of office hours
   - During break

### Overriding Office Hours

1. Click your avatar (Receptionist/Manager role)
2. Select **Override office hours**
3. Choose status or set custom status and duration
4. Click **OK**

### Digital Receptionist (IVR)

```
Admin Console → Admin > Call handling → + Add digital receptionist
```

**Audio Format Requirements:**
- Format: WAV, PCM, 8 kHz, 16-bit, Mono
- Do NOT use MP3
- Forbidden characters: `< > : " / \ | ? * &`

**Configuration Steps:**
1. Enter name (e.g., "Main Menu")
2. Optionally assign DID (always routes to IVR)
3. Upload or record greeting
4. Set destinations for each digit (0-9, *, #)
5. Configure options (language, SMS alternative)
6. Click **Save**

---

## Phone Configuration

### Provisioning Methods

#### RPS (Remote Provisioning Service) - Recommended
- Works for cloud and on-prem
- Phone contacts vendor RPS server on boot
- 3CX sends provisioning URL to vendor RPS

#### PnP (Plug and Play)
- For on-prem installs or with SBC on-site
- Phone broadcasts, 3CX detects it
- Assign phone in admin console

#### DHCP Option 66
- For large managed networks
- Phones all from same vendor
- Enter base URL in DHCP server

#### SBC/Router Phone (Cloud Only)
- Required for cloud-hosted 3CX with on-site phones
- Handles NAT traversal
- Encrypted voice traffic

### Router Phone Models

**Fanvil:** V64, V65, V62, X4U-V2, X5U-V2, X6U-V2, X7-V2, X7C-V2, X210-V2, X210i-V2
**Snom:** D862, D865
**Yealink:** T53, T53C, T53W, T54W, T57W

### STUN Configuration

```
STUN Server: stun.3cx.com:3478
```

Enables NAT traversal for better connectivity.

---

## Trunk Configuration

### Adding a SIP Trunk

```
Admin Console → Admin > SIP Trunks → Add SIP Trunk
```

**Trunk Types:**
- **Standard** - Most SIP providers
- **3CX Tunnel** - For connecting to another 3CX

**Required Information:**
- Trunk Name
- Main DID Number
- SIP Server/Registrar
- SIP Domain
- Authentication credentials

---

## Bulk Import

### CSV Template Location

```
3cx-documentation/ImportExtensionTemplateV20.csv
```

### Key CSV Fields

| Field | Required | Example |
|-------|----------|---------|
| Number | Yes | 101 |
| FirstName | Yes | John |
| LastName | Yes | Smith |
| EmailAddress | Yes | john@company.com |
| Mobile | No | +15551234567 |
| Department | No | Sales |
| MAC | No | ABC100000101 |
| Model | No | Yealink T43U |

### Import Process

**CSV Import:**
```
Admin Console → Admin > Users → Import
```

1. Create CSV with format: `FirstName,LastName,EmailAddress,MobileNumber`
2. Download sample template from import page
3. Additional fields available: Extension, Department, Role, Password, MAC Address, Phone Model
4. Upload CSV and confirm import

**Microsoft 365 Integration:**
- Requires dedicated 3CX instance
- Automatically import extensions and sync when M365 users are added/removed
- See Microsoft 365 integration guide for setup

---

## Caller ID Formatting

### Configuring Rules

```
Admin Console → Admin > Caller ID → Add rule
```

**Conditions:**
- Inbound from (Trunk or DID)
- Outbound from (Extension or ring group)

**Format Transformations:**
- Remove/add country code
- Reformat number pattern

### Common Formats

- International: `+1XXXXXXXXXX`
- National (US): `(XXX) XXX-XXXX`
- E.164: `+<country_code><number>`

---

## Busy Lamp Fields (BLF)

### Setting Up BLF

```
Admin Console → Users → Select User → BLF tab
```

**Configuration:**
1. Add BLF button
2. Set Target Extension to monitor
3. Set Label for button
4. Configure behavior:
   - Speed dial (press to call)
   - Call pickup (press to answer)
5. Save and reboot phone

---

## Multichannel Communication

### Live Chat

```
Admin Console → Admin > Multichannel → Live Chat
```

**Features:**
- Web widget for site visitors
- Route to queue or user
- Branding customization
- Operating hours

### WhatsApp

**Prerequisites:**
- WhatsApp Business API access
- Verified phone number

**Configuration:**
```
Admin Console → Admin > Multichannel > WhatsApp
```

### Facebook Messenger

```
Admin Console → Admin > Multichannel > Facebook
```

Connect your Facebook page and configure routing.

### SMS/MMS

**Prerequisites:**
- SMS provider account (Twilio, 3CX SMS, etc.)
- Virtual SMS number

**Configuration:**
```
Admin Console → Admin > Multichannel > SMS
```

### Unified Queue

Create a single queue handling all channels:
1. Create queue
2. Enable additional channels in settings
3. Configure channel-specific routing
4. Agents receive from all enabled channels

---

## Web Client Usage

### Logging In

1. Navigate to your 3CX Web Client URL
2. Enter email address and password
3. Click **Login**
4. Select preferred device/browser for calls if prompted

### Installing Web Client as PWA

#### Chrome
1. Login to Web Client
2. Click download icon in address bar
3. Click **Install**
4. Choose to pin to taskbar (recommended)
5. Enable **Launch at Startup**: type `chrome://apps`, right-click 3CX, enable option

#### Microsoft Edge
1. Login to Web Client
2. Click icon in address bar
3. Click **Install**
4. In App Installed dialog:
   - Enable **Pin to taskbar**
   - Enable **Auto-start on device login**
   - Click **Allow**

### Click2Call Browser Extension

Enables initiating calls from any website or CRM. Phone numbers appear clickable.

**Installation Links:**
- Chrome: https://chrome.google.com/webstore/detail/3cx-click2call/baipgmmeifmofkcilhccccoipmjccehn
- Edge: https://microsoftedge.microsoft.com/addons/detail/3cx-click2call/kcijpkomlnpfpjmkbghnnmflfebimpfg

**Configuration:**
- Choose preferred app: Softphone or Web Client
- Add **Exception URL list** for websites to exclude from phone number linking

### Managing Notifications

Click the **Bell** icon to receive notifications for incoming chats and calls.

### Making & Managing Calls

**Placing a Call:**
1. Click dialer icon (top right corner)
2. Enter number or search by name/extension/email
3. Click handset icon

**During a Call:**
- **Transfer** - Click Transfer, enter name/number
- **Attended Transfer** - Click Att. transfer to announce before transferring
- **Record** - Click Record button to start/stop
- **New Call** - Click New Call for separate line
- **Switch to Video** - Click Video icon
- **Conference** - Add another party directly or consultative

**Device Selection:**
- Click "Call using: Browser" under search bar
- Choose from available devices/apps

### Conference Calls

**Starting a Conference:**
1. Start or receive a call
2. Click **Conference** button
3. Enter name or number to add
4. Choose:
   - **Add directly** - Add participant immediately
   - **Consultative** - Put first caller on hold, speak to new participant, then add
5. Click **Add** to include in conference
6. Repeat to add more participants

**Managing Conference:**
- View all active participants
- Mute individual participants
- Remove participants from conference
- Drop individual callers while keeping conference going
- Transfer entire conference to another extension

### Managing Status & Boss-Secretary

**Setting Status:**
1. Click avatar (top right corner)
2. Select from dropdown
3. Status auto-changes to yellow when busy
4. Use pencil icon for custom message
5. Click "Set status temporarily" to time-limit

**Status & Forwarding (Settings → Call Forwarding):**
- Enable/disable push notifications per status
- Rename Lunch/Business Trip statuses
- Set forwarding timeout for Available/Lunch
- Configure forwarding rules
- Set Caller ID exceptions
- Set office and break hours
- **Also ring my mobile** - Simultaneous ringing
- **Accept multiple calls** - Allow multiple simultaneous calls
- **Accept PUSH notifications** - Enable for browser calling

**Forwarding Destination Options:**
| Option | Description |
|--------|-------------|
| Same as all calls | Use default forwarding rule |
| Voicemail | Send directly to voicemail |
| Extension number | Forward to another extension or its voicemail |
| My Mobile | Forward to external mobile (external calls only) |
| Rebound | Announce caller and allow accept/reject |
| Call Deflection (302) | Forward at provider level (provider must support) |
| External Number | Forward to any external number |
| System Extension | Forward to system extension |
| Send busy | Return busy signal |

**Admin Option:** Enable **Hide Call Forwarding Rules** in **Users > Options > Restrictions** to prevent users from configuring their own forwarding.

**Boss-Secretary State:**
- If enabled, set Active/Inactive from status menu

### Auto-Switch Status by Working Hours

```
Settings → Call Forwarding → Switch Status
```

Choose regular office hours or add your own.

**Automatic Status Changes:**
| Time Period | Status |
|-------------|--------|
| During office hours | Available |
| Outside office hours | Do Not Disturb |
| During break times | Away |

**Optional:**
- Override group office hours and set specific office hours for your extension
- Disable outbound calls outside of office hours

### Caller ID Exceptions

**To Create:**
```
Settings → Call Forwarding → Exceptions → Click +
```

1. Enter caller ID (specific or pattern)
2. Select "Received During" hours
3. Select "Forward To" destination
4. Enable "Rebound" (optional) - returned calls not answered go back to original extension
5. Click **OK**

**Use Cases:**
- Always accept VIP calls regardless of hours
- Always send marketing calls to voicemail

### Team View

**Features:**
- Default: shows groups you're part of
- Change view from dropdown (departments, groups)
- Star icon to add to Favorites
- Contacts toggle shows personal contacts (listed after colleagues)

### Chat Features

**Access:** Web Client → Chat (left menu)

**Channels:**
- Colleagues (instant messaging)
- Website visitors (live chat)
- WhatsApp
- Facebook Messenger
- SMS/MMS

**Chat Templates:**
- Created by group managers
- Quick response with predefined messages
- Organized by categories and languages

### Managing Contacts

**Contacts Tab Features:**
- Edit, add, delete, and call contacts
- Searchable list
- Filter by Phonebook (Company, Department, Personal, M365, Google, CRM)
- Badge shows phonebook source

### Video Conferencing

**Start:**
1. Click **Meet** option (left menu)
2. Start immediate or schedule for later

See Video Conferencing manual for full details.

---

## Troubleshooting

### Audio Quality Issues

| Issue | Cause | Solution |
|-------|-------|----------|
| One-way audio | NAT/Firewall blocking RTP | Enable STUN or use SBC |
| Choppy audio/echo | Network latency/codec mismatch | Check codecs and QoS |

### Call Dropping

**Causes:**
- NAT timeout (UDP connections closed)
- Poor internet connectivity
- SIP keepalive not configured

**Solutions:**
- Enable SIP keepalive (30-60 seconds)
- Use 3CX SBC
- Configure NAT keepalive on phones

### Registration Failures

**Checklist:**
1. Correct MAC address (no dashes/colons)
2. Network connectivity
3. Firewall rules (ports 5001, 5090)
4. SBC status (if using)
5. Extension availability

**Debug Steps:**
1. Check phone web interface for logs
2. Restart 3CX services
3. Delete and re-add phone
4. Reset phone to factory and re-provision

### Queue Issues

| Issue | Solution |
|-------|----------|
| Calls not reaching queue | Check office hours, DID assignment |
| High abandonment rate | Reduce wait time, add members, improve announcements |
| Agents not receiving calls | Verify login status, ring strategy, member list |

### SIP Trunk Issues

| Issue | Solution |
|-------|----------|
| Outbound calls failing | Check registration, credentials, codecs |
| Inbound calls not ringing | Verify DID assignment, inbound rules, office hours |
| Registration failing | Check SIP server, credentials, outbound proxy |

---

## Advanced Configuration

### Multi-Level IVR

```
Main Menu (IVR: 100)
├── Press 1 → Sales (IVR: 101)
│   ├── Press 1 → New Sales (Queue: 201)
│   ├── Press 2 → Existing (Queue: 202)
│   └── Press 0 → Receptionist
├── Press 2 → Support (Queue: 200)
├── Press 3 → Billing (Ext: 150)
└── Press 0 → Operator
```

**Setup Order:**
1. Create child IVRs first
2. Create parent IVR
3. Set destinations from parent to children

### DID Routing Strategies

- Multiple DIDs to single queue
- DID to direct extension (VIP lines)
- DID to digital receptionist (always IVR)
- Time-based DID routing

### Call Forwarding

**Types:**
- Forward All
- Forward Busy
- Forward No Answer (after X rings)
- Forward External (to mobile/external)

### Call Recording

```
Admin Console → Admin > Settings > Advanced
```

Enable recording scope:
- All calls
- External calls only
- Per extension/queue

### Privacy Options

- Hide caller ID
- Anonymous call rejection
- Do not disturb (DND)

---

## Network Requirements

### Ports

| Port | Protocol | Purpose |
|------|----------|---------|
| 5001 | TCP/HTTPS | Web management |
| 5060 | UDP/TCP | SIP signaling |
| 5061 | TCP/TLS | Secure SIP (tunnels) |
| 5090 | UDP/TCP | Secure SIP (local) |
| 9000-9049 | UDP | RTP audio |

### QoS Recommendations

- Tag VoIP as DSCP EF (Expedited Forwarding)
- Prioritize SIP signaling over RTP
- Reserve bandwidth for voice calls

---

## Database Queries

### Recent Calls to Extension

```sql
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
```

### Failed Calls

```sql
SELECT * FROM cl_calls
WHERE is_answered = false
ORDER BY start_time DESC
LIMIT 20;
```

### Audit Log

```sql
SELECT * FROM audit_log
ORDER BY time_stamp DESC
LIMIT 50;
```

---

## File Locations

- **Main Log:** `/var/lib/3cxpbx/Bin/3CXPhoneSystem.log`
- **Skill File:** `.claude/plugins/3cx-voip-system/SKILL.md`
- **CSV Template:** `3cx-documentation/ImportExtensionTemplateV20.csv`
- **HTML Documentation:** `3cx-documentation/*.html`

---

## Enable Verbose Logging

1. `Admin > Settings > Advanced`
2. Set logging level to **Verbose**
3. Reproduce issue
4. Export logs from `Admin > Maintenance`
5. Set back to normal (saves disk space)

---

## Related Documentation

- [Official 3CX Documentation](3cx-documentation/)
- [Project Index](PROJECT_INDEX.md)
- [Skill File](.claude/plugins/3cx-voip-system/SKILL.md)