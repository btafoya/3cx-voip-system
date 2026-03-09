---
name: 3cx-voip-system
description: Guide users through 3CX VoIP PBX administration and configuration tasks, plus end-user Web Client usage. Use this skill whenever the user asks about 3CX configuration, setting up extensions, configuring call routing, managing queues, setting up IVR/digital receptionists, provisioning IP phones, configuring SIP trunks, importing extensions in bulk, advanced routing scenarios, multichannel communication (Live Chat, WhatsApp, Facebook, SMS), troubleshooting audio/registration/call issues, installing/using the Web Client app, Click2Call extension, managing status and team view, or any other 3CX administration or end-user task. Even if the user doesn't explicitly mention 3CX but is asking about VoIP PBX configuration, phone system setup, call management, or Web Client usage topics that 3CX handles, use this skill.
---

# 3CX VoIP System Administration & Web Client Usage

## Overview

This skill provides guidance for configuring and managing 3CX VoIP PBX systems, plus using the 3CX Web Client. 3CX is a software-based IP PBX that handles voice over IP calls, call routing, queues, and communication channels including phone, chat, WhatsApp, SMS, and video conferencing. The Web Client provides a browser-based interface for making calls, managing status, conferencing, and multichannel communication.

## Quick Start

Identify the user's configuration goal:

| User says... | Go to section... |
|--------------|------------------|
| "Add a user/extension" | Users & Extensions |
| "Set up call queue" or "ring group" | Call Queues & Ring Groups |
| "Configure office hours" or "IVR menu" | Call Routing & IVR |
| "Provision a phone" or "add IP phone" | IP Phone Configuration |
| "Add external phone line" or "SIP trunk" | SIP Trunk Configuration |
| "Import many users at once" | Bulk Import |
| "Format caller ID" | Caller ID Formatting |
| "Set up BLF" | Busy Lamp Fields |
| "Set up live chat", "WhatsApp", or "Facebook" | Multichannel Communication |
| "Multi-level IVR", "call forwarding", or "overflow" | Advanced Call Routing |
| "Calls dropping", "poor audio", or "one-way audio" | Advanced Troubleshooting |
| "Install Web Client app", "Click2Call", or "how to use Web Client" | 3CX Web Client Usage |
| "Boss-Secretary state", "team view", or "status settings" | 3CX Web Client Usage |

---

## Users & Extensions

### Creating a User

1. Go to **Users** in the admin console
2. Click **Add User**
3. Enter:
   - First name, last name
   - Extension number (3-6 digits)
   - Email address
   - Set a password for the user
4. Select user role:
   - **Owner** - Full admin access including users, configuration, reports, recordings. Can elevate users to Manager or Group Administrator within own group. Can Barge in, Listen in, Whisper.
   - **Manager** - Has Admin view, can configure user settings, create users and elevate roles. Can see reports and recordings. Can Barge in, Listen in.
   - **Group Administrator** - Has Admin view, can configure Call handling, SIP Trunks, WhatsApp, Live chat. By default cannot see reports/recordings, cannot Listen in or Barge in.
   - **Receptionist** - Can override office hours for groups they're a member of. Can see group calls, presence, and perform operations (divert, transfer, pickup, park, intercom).
   - **User** - Basic role. Can only manage their own account and see their own calls (not others'). Can see presence of other users.
   - **System Administrator** (dedicated only) - Can see everything for all groups and SIP trunks. Cannot Barge in or Listen in. Cannot make others System Admin/Owner.
   - **System Owner** (dedicated only) - Can do everything System Admin can plus Barge in, Listen in, view recordings and reports. Only one who can elevate users to System Admin or Owner.
5. **Main Group membership** (dedicated only) - Ideally one group per user, but can join multiple. The main group's office hours apply to the user.
6. **3CX Talk link** - Each user is automatically assigned a unique 3CX Talk link.
7. Click **Save**
8. Team members will receive an email with their account details.

### Assigning an IP Phone to a User

1. Go to **Users** and select the user
2. Click the **IP Phone** tab
3. Click **Configure a phone**
4. Select phone model from dropdown
5. Enter the MAC address (no dashes or colons)
6. Choose connection type:
   - **RPS** - Remote Provisioning Service (easiest, works for cloud and on-prem)
   - **PnP** - Plug and Play (on-prem only)
   - **DHCP Option 66** - For managed networks
   - **SBC/Router Phone** - For cloud-hosted 3CX with on-site phones
7. Click **Add phone**

### Extension Types

- **Extension** (dn_type=0) - Individual user
- **External Line/Trunk** (dn_type=1) - SIP trunk or provider
- **Ring Group/Queue** (dn_type=2) - Call distribution group
- **Voicemail** (dn_type=5) - Voicemail box
- **Inbound Routing** (dn_type=13) - DID routing rules

### Groups

Extension groups allow you to group extensions together to apply the same language, time zone, and office hours. All extensions are initially assigned to the **Default** group.

**Group Features:**
- Each group has its own **Mini IVR** for routing calls based on group office hours
- Extension can be part of multiple groups, but follows the office hours of the **Main Group Membership**

**Creating a Group:**
1. Go to **Users** and click **Groups**
2. Click **Add Group**
3. Specify a name for the group
4. In the members section, click **Add** to add members
5. Click **Save**

---

## Call Queues & Ring Groups

### Call Queue vs Ring Group

| Feature | Call Queue | Ring Group |
|---------|------------|------------|
| Callers wait in queue | Yes | No |
| Plays music/announcement | Yes | Yes |
| Reports statistics | Yes | Basic |
| Best for | Support centers | Small teams |

### Creating a Call Queue

1. Go to **Admin > Call handling**
2. Click **+ Add Queue**
3. Configure:
   - **Queue Number** - The DN number callers dial
   - **Name** - Display name (e.g., "Support Queue")
   - **Members** - Add extensions to the queue
4. Set ring strategy:
   - **Ring All** - All members ring simultaneously
   - **Linear** - Members ring in order
   - **Circular** - Round-robin distribution
   - **Least Recent** - Member who hasn't answered longest
   - **Random** - Random member selection
5. Configure queue settings:
   - **Maximum wait time** - How long callers wait
   - **Maximum queue size** - Maximum callers waiting
   - **Wrap-up time** - Time before agent receives next call
   - **Failover destination** - Where calls go if queue is full/timeout
6. Upload or record queue announcements (welcome, music on hold, position announcement)
7. Click **Save**

### Creating a Ring Group

1. Go to **Admin > Call handling**
2. Click **+ Add Ring Group**
3. Configure similar to Queue but without queue-specific options
4. Set ring strategy for the group
5. Click **Save**

### Queue Statistics Available

- Call volume per queue
- Average wait time
- Abandoned call rate
- Agent performance
- SLA compliance

---

## Call Routing & IVR

### Office Hours Configuration

1. Go to **Admin > Office hours**
2. Click on days to set opening hours
3. Add break times (lunch, meetings)
4. Set time zone if group is in different zone
5. In **Assigned DID numbers** section:
   - Select an unassigned DID
   - Set destination for:
     - **During office hours** - Ring group, user, voicemail, digital receptionist, or queue
     - **Out of office hours** - Same destination options
     - **During break** - Same destination options

### Holidays Configuration

1. In Office hours page, click **Add** under **Set your Holidays**
2. Specify date and time for each holiday
3. Calls on holidays route as "out of office hours"

### Overriding Office Hours

1. Click your avatar (requires Receptionist or Manager role)
2. Select **Override office hours**
3. Choose:
   - Pre-set status (Open, Closed, Break, etc.)
   - **Custom** - Set your own status and duration
   - **Play announcement and end call** - For emergencies or training
4. Click **OK**
5. Override remains active until time expires

### Digital Receptionist (IVR) Configuration

1. Go to **Admin > Call handling**
2. Click **+ Add digital receptionist**
3. Enter name (e.g., "Main Menu", "Public Holiday")
4. Optionally assign a DID directly:
   - Calls will ALWAYS go to this IVR, skipping office hours
5. Upload or record greeting:
   - Format: **PCM, 8 kHz, 16 bit, Mono WAV**
   - Do not use MP3
   - Don't use reserved characters: `< > : " / \ | ? * &`
   - Example: "Thank you for calling XYZ. Press 1 for sales, 2 for support"
6. For each digit, set destination:
   - User, Voicemail box, Ring group, Queue, or another Digital receptionist
7. In **Options** tab, configure:
   - Prompt language
   - SMS alternative route
8. Click **Save**

---

## IP Phone Configuration

### Provisioning Methods

**RPS (Remote Provisioning Service)**
- Easiest method, works for cloud and on-prem
- Phone contacts vendor RPS server on boot
- 3CX sends provisioning URL to vendor RPS

**PnP (Plug and Play)**
- For on-prem installs or with SBC on-site
- Phone broadcasts, 3CX detects it
- Assign phone in admin console

**DHCP Option 66**
- For large managed networks
- Phones all from same vendor
- Enter base URL in DHCP server

### Adding a Phone to Extension

1. Go to **Users** and select user
2. Click **IP Phone** tab
3. Click **Configure a phone**
4. Select phone model
5. Enter MAC address (no dashes/colons)
6. Select connection method

### Router Phone / SBC (for Cloud 3CX)

If 3CX is hosted in cloud, need router phone or SBC on local network:

**Router Phone Models:**
- Fanvil: V64, V65, V62, X4U-V2, X5U-V2, X6U-V2, X7-V2, X7C-V2, X210-V2, X210i-V2
- Snom: D862, D865
- Yealink: T53, T53C, T53W, T54W, T57W

Router phone provides:
- Encrypted voice traffic
- Automatic reconnection on dropout
- Combines SIP and RTP to overcome firewall issues
- Saves bandwidth by routing internal calls locally

### Provisioning with STUN

1. In phone configuration, enable STUN
2. Enter STUN server: `stun.3cx.com:3478`
3. Helps with NAT traversal

### Manual Phone Configuration

1. Get provisioning URL from 3CX admin
2. Access phone web interface (get IP from phone display)
3. Enter provisioning URL in phone's provisioning settings

---

## SIP Trunk Configuration

### Adding a SIP Trunk

1. Go to **Admin > SIP Trunks**
2. Click **Add SIP Trunk**
3. Select trunk type:
   - **Standard** - Most SIP providers
   - **3CX Tunnel** - For connecting to another 3CX
4. Enter trunk details:
   - **Trunk Name** - Display name
   - **Main DID Number** - Primary phone number
   - **Additional DIDs** - Add more numbers if available
5. Enter provider SIP details:
   - SIP server/Registrar
   - SIP domain
   - Outbound proxy (if required)
   - Authentication credentials (username/password)
6. Configure codec preferences
7. Click **Save**
8. Test the trunk

---

## Bulk Import

### CSV Template Format

The `ImportExtensionTemplateV20.csv` template contains these key fields:

| Field | Description | Required |
|-------|-------------|----------|
| Extension | Extension number | Yes |
| First Name | User's first name | Yes |
| Last Name | User's last name | Yes |
| Email | User email address | Yes |
| Mobile | Mobile number | No |
| Department | Department name | No |
| Role | Extension/Receptionist/Manager | No |
| Password | User password | Yes |
| MAC Address | For IP phone provisioning | No |
| Phone Model | If provisioning phone | No |

### Importing Extensions

**CSV Import:**
1. Create a CSV file with this format: `FirstName,LastName,EmailAddress,MobileNumber`
   - Example: `James,Bond,jamesbond@3cx.com,+35999979777`
   - Download a sample template from the import page
   - Additional fields can be imported: Extension, Department, Role, Password, MAC Address, Phone Model
2. Go to **Admin > Users**
3. Click **Import**
4. Upload the CSV file
5. Review and confirm import

**Microsoft 365 Integration:**
- Requires a dedicated 3CX instance
- Automatically import extensions and sync users when Microsoft 365 users are added/removed
- See Microsoft 365 integration guide for setup details

---

## Caller ID Formatting

### Configuring Caller ID Rules

1. Go to **Admin > Caller ID**
2. Click **Add rule**
3. Set conditions:
   - **Inbound from** - Trunk or DID
   - **Outbound from** - Extension or ring group
4. Define format transformation:
   - Remove/add country code
   - Reformat number pattern
5. Test the rule

### Common Format Patterns

- **International**: `+1XXXXXXXXXX`
- **National (US)**: `(XXX) XXX-XXXX`
- **E.164**: `+<country_code><number>`

---

## Busy Lamp Fields (BLF)

### Setting Up BLF

1. Go to **Users** and select the user
2. Click **BLF** tab
3. Add BLF buttons:
   - **Target Extension** - Which extension to monitor
   - **Label** - Display text on button
4. Configure button behavior:
   - Speed dial (press to call)
   - Call pickup (press to answer ringing call)
5. Save changes
6. Reboot phone to apply

---

## Advanced Call Routing

### Multi-Level IVR Menus

Create nested IVRs for complex call trees:

**Example Structure:**
```
Main Menu (IVR: 100)
├── Press 1 → Sales Department (IVR: 101)
│   ├── Press 1 → New Sales (Queue: 201)
│   ├── Press 2 → Existing Accounts (Queue: 202)
│   └── Press 0 → Receptionist (Ext: 100)
├── Press 2 → Support (Queue: 200)
├── Press 3 → Billing (Ext: 150)
└── Press 0 → Operator (Ext: 100)
```

**To configure:**
1. Create child IVRs first (Sales, Billing, etc.)
2. Create parent IVR (Main Menu)
3. In parent IVR, set destinations to child IVRs for relevant digits
4. Configure "Return to main menu" option in child IVRs if needed

### DID Routing Strategies

**Multiple DIDs to Single Queue**
- Assign multiple DIDs to one queue
- Useful for different marketing numbers, regional numbers
- Callers don't see difference in service

**DID to Direct Extension**
- Assign DID directly to a user
- Bypasses IVR for VIP customers or dedicated lines

**DID to Digital Receptionist**
- Use when IVR should always apply
- Bypasses office hours routing

**Time-Based DID Routing**
- Route same DID differently based on:
  - Office hours (configured in DID settings)
  - Specific time periods (requires rule-based routing)

### Call Forwarding

**Types of Call Forwarding:**
- **Forward All** - All calls to another number/extension
- **Forward Busy** - When user is on another call
- **Forward No Answer** - After X rings
- **Forward External** - Forward to mobile or external number

**To configure:**
1. Go to **Users** and select user
2. Click **Forwarding** tab
3. Set forwarding rules for each type
4. Configure ring count before no-answer forward
5. Optionally require confirm before external forward

### Conditional Routing

Create routing based on:
- **Caller ID** - Route specific callers differently
- **Time of day** - Different routes for business/after hours
- **Day of week** - Weekend vs weekday routing
- **Trunk** - Different routes per incoming trunk

**To configure caller-based routing:**
1. Go to **Admin > Inbound Rules**
2. Click **Add Rule**
3. Set condition (Caller number or pattern)
4. Define destination

### Queue Overflow Strategies

When queue is full or timeout reached:

**Options:**
- **Forward to another queue** - Overflow to backup queue
- **Send to voicemail** - Leave a message
- **Route to digital receptionist** - Offer other options
- **Transfer to external number** - Overflow to call center or backup line
- **Play announcement and disconnect** - Inform and hang up

**To configure:**
1. Edit queue settings
2. Set **Maximum wait time** and **Maximum queue size**
3. Configure **Failover destination**
4. Set **No answer timeout** for individual queue members

### Recording Calls

**Enable call recording:**
1. Go to **Admin > Settings > Advanced**
2. Enable **Call Recording**
3. Choose recording scope:
   - All calls
   - External calls only
   - Per extension/queue
4. Set storage location
5. Configure retention policy

**Per-extension recording:**
1. Go to **Users** and select user
2. Enable recording for specific extension
3. Set to "Always", "Never", or "User can enable"

### Call Privacy

**Privacy options:**
- **Hide caller ID** - Block outbound caller ID
- **Anonymous call rejection** - Reject calls with blocked caller ID
- **Do not disturb** - Send all calls to voicemail

**To configure:**
1. Go to **Users** and select user
2. Click **Privacy** tab
3. Enable desired privacy options

---

## 3CX Talk & Meet Links

### 3CX Talk Links

**What are 3CX Talk links?**
- Weblinks that allow people to call you or your company just by clicking
- No need to dial a number or pay for the call
- Visitors don't need any special app - works from any browser on computer or smartphone using WebRTC
- Example links:
  - User link: `https://pbx002.3cx.cloud/mariajohnson/`
  - Company link: `https://pbx002.3cx.cloud/mycompany/`

**User Talk Links:**
- Each user gets their own 3CX Talk link
- Add to email signature or share with clients
- Users can find and edit their Talk link "friendly name" in **Settings > General**

**Company Talk Links:**
- Paste on your website or company email signature
- Edit from **Admin > Call Handling** in your **Call Queue** or **Ring Group** settings

### 3CX Meet Links

**What are 3CX Meet links?**
- Sharing the 3CX Meet link lets visitors go directly to your meeting room
- Start ad-hoc video conferences instantly
- Example: `https://pbx002.3cx.cloud/meet/mariajohnson/`

**Spam Prevention:**
- Configure to request Name and Email first
- Accept or reject calls based on caller information

---

## Multichannel Communication

### Live Chat Integration

3CX includes built-in live chat for web visitors.

**To enable live chat:**
1. Go to **Admin > Multichannel**
2. Enable **Live Chat**
3. Configure chat widget:
   - Widget title, welcome message
   - Branding colors
   - Operating hours (links to office hours)
   - Queue destination for incoming chats
4. Get embed code for website

**Chat routing:**
- Route to queue, ring group, or specific user
- Use same queue for phone and chat (agents handle both)
- Chat-only queues for dedicated chat agents

### WhatsApp Integration

**Prerequisites:**
- WhatsApp Business API access
- Phone number verified with WhatsApp

**To configure:**
1. Go to **Admin > Multichannel > WhatsApp**
2. Connect WhatsApp Business API
3. Map WhatsApp number to 3CX extension
4. Configure routing (queue, ring group, or user)
5. Set auto-reply messages

### Facebook Messenger Integration

**To configure:**
1. Go to **Admin > Multichannel > Facebook**
2. Connect Facebook page
3. Configure routing destination
4. Set auto-reply and office hours behavior

### SMS/MMS Integration

**Prerequisites:**
- SMS provider account
- Virtual SMS number

**To configure:**
1. Go to **Admin > Multichannel > SMS**
2. Add SMS provider (Twilio, 3CX SMS, etc.)
3. Configure credentials
4. Map SMS number to 3CX extension
5. Set routing rules

### Unified Queue for All Channels

Create a single queue handling phone, chat, WhatsApp, and SMS:

1. Create or select existing queue
2. In queue settings, enable additional channels
3. Configure channel-specific routing rules
4. Agents receive interactions from all enabled channels

---

## 3CX Web Client Usage

### Logging In

1. Open your web browser and navigate to your 3CX Web Client URL
2. Enter your email address and password
3. Click **Login**
4. Select your preferred device/browser for calls if prompted

### Installing Web Client as PWA (Chrome)

1. Login to your Web Client
2. Click the download icon in your browser's address bar
3. Click **Install** in the dialog that appears
4. Choose whether to pin 3CX to your taskbar (recommended for easier access)
5. To enable launch at startup: type `chrome://apps`, right-click on 3CX, enable **Launch at Startup**

### Installing Web Client as PWA (Microsoft Edge)

1. Login to your Web Client
2. Click the icon highlighted in your address bar
3. Click **Install**
4. In the **App Installed** dialog:
   - Enable **Pin to taskbar**
   - Enable **Auto-start on device login**
   - Click **Allow**

### Click2Call Browser Extension

The Click2Call extension enables you to initiate calls from any website or CRM system. Phone numbers appear "hyperlinked" for you to click and send to the 3CX Web Client.

**Installing:**
- **Chrome**: https://chrome.google.com/webstore/detail/3cx-click2call/baipgmmeifmofkcilhccccoipmjccehn
- **Edge**: https://microsoftedge.microsoft.com/addons/detail/3cx-click2call/kcijpkomlnpfpjmkbghnnmflfebimpfg

**Configuration:**
1. After installation, choose which 3CX app to use: Softphone or Web Client
2. Add URLs to **Exception URL list** to exclude specific websites from phone number linking
3. Useful for websites with accounting information or other sensitive data

### Managing Notifications

Click the **Bell** icon in the Web Client to receive notifications for incoming chats and calls.

### Making & Managing Calls

**To place a call:**
1. Click the dialer icon in the top right corner
2. Enter phone number or search by name, extension number, or email
3. Click the handset icon to start

**During a call, you can:**
- **Transfer a call** - Click Transfer and enter name or number
- **Attended Transfer** - Click Att. transfer to announce the call before transferring (call is put on hold)
- **Record a call** - Click Record button to start/stop recording
- **Start a new call** - Click New Call to start a separate line without hanging up
- **Switch to video** - Click Video icon to convert audio to video call
- **Start a conference** - Add another party directly or in consultative fashion (put on hold, connect to new party, then decide to add or drop)

**Call device selection:**
- Under the search bar, click "Call using: Browser"
- Choose from available devices/apps

### Conference Calls

**Starting a Conference from Web Client:**
1. Start or receive a call
2. Click **Conference** button
3. Enter name or number to add
4. Choose **Add directly** to add participant immediately, or **Consultative** to put first caller on hold and speak to new participant first
5. Click **Add** to include in conference
6. Repeat to add more participants

**Managing Conference:**
- View all active participants
- Mute individual participants
- Remove participants from conference
- Drop individual callers while keeping conference going
- Transfer entire conference to another extension

### Managing Status & Boss-Secretary State

**Setting your status:**
1. Click your avatar in the top right corner
2. Select status from dropdown
3. Status color automatically changes to yellow when line is busy
4. Use pencil icon to set custom status message
5. Click "Set status temporarily" to time-limit your status

**Status & Forwarding Settings (Settings → Call Forwarding):**
- Enable/disable push notifications per status
- Rename Lunch and Business Trip statuses
- Set seconds before unanswered call forwarding for Available and Lunch statuses
- Configure forwarding rules for unanswered calls
- Set Caller ID exceptions to override forwarding
- Set office and break hours
- **Also ring my mobile** - Simultaneous ringing to mobile
- **Accept multiple calls** - Allow multiple simultaneous incoming calls
- **Accept PUSH notifications** - Enable for browser-based calling

**Forwarding Destination Options:**
- **Same as all calls** - Use the default forwarding rule
- **Voicemail** - Send directly to voicemail
- **Extension number** - Forward to another extension or its voicemail
- **My Mobile** - Forward to external mobile number (external calls only)
- **Rebound** - Announce caller and allow accept/reject
- **Call Deflection (302)** - Forward at provider level (provider must support)
- **External Number** - Forward to any external number
- **System Extension** - Forward to system extension
- **Send busy** - Return busy signal

**Admin Option:**
- To prevent users from configuring their own forwarding rules, enable **Hide Call Forwarding Rules** in **Users > Options > Restrictions**

**Boss-Secretary State:**
- If enabled for your account, set to Active/Inactive from status menu
- Allows executive/assistant call handling configuration

### Auto-Switch Status Based on Working Hours

**To configure:**
1. Go to **Settings → Call Forwarding → Switch Status**
2. Choose to use regular office hours or add your own
3. Your extension will follow these hours and automatically change status

**Automatic Status Changes:**
- **During office hours** - Extension status switches to "Available"
- **Outside office hours** - Extension status switches to "Do Not Disturb"
- **During break times** - Extension status is set to "Away"

**Optional:**
- Override group office hours and create specific office hours for your extension
- Disable outbound calls outside of office hours

### Caller ID Exceptions to Working Hours

**To create exceptions:**
1. Go to **Settings → Call Forwarding → Exceptions**
2. Click **+** to add new exception
3. Enter caller ID (specific number or pattern)
4. Select "Received During" hours
5. Select "Forward To" destination
6. Optionally enable "Rebound" - forwarded calls not answered by destination automatically return to original extension
7. Click **OK**

**Use cases:**
- Always accept calls from VIP clients regardless of working hours
- Always send marketing calls to voicemail during working hours

### Team View - Departments & Groups

**View options:**
- Default view shows all members of groups you're part of
- Change view from dropdown (departments, groups, etc.)
- Click star icon to add colleagues to Favorites
- Use contacts toggle to show personal contacts (listed after colleagues)

### Chat with Colleagues and Customers

**Access:** Web Client → Chat (left-side menu)

**Features:**
- Send/receive instant messages with colleagues
- Live chat with website visitors
- WhatsApp integration
- Facebook Messenger integration
- SMS/MMS messages from customers

**Chat Templates:**
- Can be created and edited by group managers
- Allow quick response with predefined messages
- Can be organized into categories and languages

### Managing Contacts

**Contacts tab features:**
- Manage (edit, add, delete) and call contacts
- Searchable list of all contacts
- Filter by Phonebook source (Company, Department, Personal, M365, Google, CRM)
- Badge indicates which Phonebook a contact belongs to

### Video Conferencing

**To start:**
1. Click **Meet** option in left-hand menu of Web Client
2. Start immediate conference or schedule for later

See Video Conferencing manual for full feature details.

---

## Advanced Troubleshooting

### Audio Quality Issues

**One-way audio (can hear but not be heard)**
- Cause: NAT/Firewall blocking RTP ports
- Solutions:
  - Enable SIP ALG on router (may cause issues, test first)
  - Use 3CX SBC or router phone
  - Disable SIP ALG and enable STUN
  - Configure port forwarding (5004-5060 for SIP, 9000-9049 for RTP)

**Choppy audio or echo**
- Cause: Network latency, codec mismatch
- Solutions:
  - Check codec priority (G.711 for best quality, G.729 for bandwidth saving)
  - Check network bandwidth and QoS settings
  - Disable echo cancellation on IP phone if using SIP trunk with built-in echo cancellation

### Call Dropping

**Common causes:**
- NAT timeout (UDP connections closed by router)
- Poor internet connectivity
- SIP keepalive not configured

**Solutions:**
- Enable SIP keepalive (register every 30-60 seconds)
- Use 3CX SBC for better NAT handling
- Configure NAT keepalive on IP phones
- Check internet stability

### Registration Failures

**Phone says "Registering" or "Registration Failed"**

Check:
1. **Correct MAC address** - No dashes or colons
2. **Network connectivity** - Phone can reach 3CX server
3. **Firewall rules** - Ports 5001 (https) and 5090 (secure SIP) open
4. **SBC status** - If using SBC, ensure it's running
5. **Extension availability** - Extension not already assigned to another device

**Debug steps:**
1. Check phone's web interface for error logs
2. Restart 3CX services
3. Delete and re-add phone in 3CX admin
4. Reset phone to factory defaults and re-provision

### Queue Issues

**Calls not reaching queue**
- Check office hours - may be routing elsewhere
- Verify DID is assigned correctly
- Check if queue members are enabled
- Review queue failover destination

**High abandonment rate**
- Reduce maximum wait time
- Add more queue members
- Improve queue announcements (provide wait time, position)
- Reduce wrap-up time

**Agents not receiving calls**
- Verify agent is logged in
- Check agent's status (available, busy, DND)
- Review ring strategy settings
- Ensure agent is enabled in queue member list

### IVR Issues

**Callers can't press keys**
- Check DTMF settings on SIP trunk
- Verify IVR prompt format (WAV, 8kHz, 16-bit, Mono)
- Test IVR from different phones

**IVR loops or misrouted calls**
- Check IVR digit destinations
- Verify child IVRs exist if referenced
- Review office hours configuration (may be overriding IVR)

### SIP Trunk Issues

**Outbound calls failing**
- Check trunk registration status
- Verify authentication credentials
- Review codec compatibility with provider
- Check provider documentation for required settings

**Inbound calls not ringing**
- Verify DID is assigned correctly
- Check inbound rules
- Review office hours configuration
- Test with provider (they may see calls but not reaching)

**Trunk registration fails**
- Verify SIP server address
- Check username/password
- Confirm firewall allows outbound SIP (port 5060)
- Some providers require specific outbound proxy

### Network Issues

**Port Requirements for 3CX**

| Port | Protocol | Purpose |
|------|----------|---------|
| 5001 | TCP/HTTPS | Web management |
| 5060 | UDP/TCP | SIP signaling |
| 5061 | TCP/TLS | Secure SIP (for tunnels) |
| 5090 | UDP/TCP | Secure SIP (local) |
| 9000-9049 | UDP | RTP audio |

**Firewall configuration:**
- Open inbound ports for 3CX server
- Allow outbound from IP phones to 3CX server
- Configure QoS to prioritize VoIP traffic

**QoS recommendations:**
- Tag VoIP traffic as DSCP EF (Expedited Forwarding)
- Prioritize SIP signaling over RTP
- Reserve bandwidth for voice calls

### Database Troubleshooting

**Check call records:**
```sql
-- Find recent calls to specific extension
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

**Find failed calls:**
```sql
SELECT * FROM cl_calls
WHERE is_answered = false
ORDER BY start_time DESC
LIMIT 20;
```

**Check audit log for recent changes:**
```sql
SELECT * FROM audit_log
ORDER BY time_stamp DESC
LIMIT 50;
```

### Log File Analysis

**Main log location:** `/var/lib/3cxpbx/Bin/3CXPhoneSystem.log`

**Common log entries:**
- `SIP registration failed` - Registration issue
- `Call failed` - Call termination reason
- `NAT traversal` - STUN/SBC status
- `Codec mismatch` - Audio quality issue

**Enable verbose logging:**
1. Go to **Admin > Settings > Advanced**
2. Set logging level to **Verbose**
3. Reproduce the issue
4. Export logs from **Admin > Maintenance**
5. Set logging back to normal (verbose logs use disk space)

### Performance Issues

**High CPU usage:**
- Check for excessive call recordings
- Review number of active calls
- Verify server meets minimum requirements

**Poor call quality during peak times:**
- Review network bandwidth
- Check for other traffic competing for bandwidth
- Implement QoS for VoIP
- Consider adding more SBCs for distributed locations

---

## Troubleshooting Common Issues

| Issue | Possible Cause | Solution |
|-------|---------------|----------|
| Phone not registering | Wrong MAC address | Verify MAC in user settings |
| Calls not reaching queue | Office hours closed | Check office hours configuration |
| Poor audio quality | Network/NAT issues | Enable STUN or use SBC |
| Calls dropping | Router not configured for 3CX | Configure SIP ALG or use SBC |
| CSV import fails | Invalid format | Use correct CSV template format |
| One-way audio | RTP ports blocked | Forward ports 9000-9049 or use SBC |
| Queue not receiving calls | DID not assigned to queue | Assign DID in inbound rules |
| IVR not responding | Wrong audio format | Convert to WAV 8kHz 16-bit Mono |
| Trunk registration fails | Incorrect credentials | Verify username/password with provider |

---

## Database & Logging (for Advanced Debugging)

If you have access to the 3CX database (PostgreSQL):

Key tables:
- `cl_calls` - Call summary records
- `cl_participants` - Extension/queue/trunk details
- `cl_segments` - Call flow paths
- `cdroutput` - Full CDR records
- `audit_log` - Configuration changes

DN Type codes:
- 0 = Extension
- 1 = External Line/Provider
- 2 = Ring Group/Queue
- 5 = Voicemail
- 13 = Inbound Routing

---

## File Locations

| File | Location |
|------|----------|
| Main 3CX log file | `/var/lib/3cxpbx/Bin/3CXPhoneSystem.log` |
| CSV import template | `3cx-documentation/ImportExtensionTemplateV20.csv` |
| Official 3CX HTML docs | `3cx-documentation/*.html` |
| Project index | `PROJECT_INDEX.md` |
| Knowledge base | `KNOWLEDGE_BASE.md` |

---

## Related Documentation

- [3CX Official Website](https://www.3cx.com/)
- [3CX Documentation Portal](https://www.3cx.com/docs/)
- [Project Index](PROJECT_INDEX.md)
- [Knowledge Base](KNOWLEDGE_BASE.md)
- [README](README.md)