# DID Extension Additions — Project Manager Direct Lines

## Overview

Add 6 purchased DIDs from Florida High Speed Internet (FHSI) trunk as direct lines for project managers. Each DID routes to a dedicated PM extension with personal voicemail and email notification.

## DID → Extension Map

| DID | E.164 | Extension |
|-----|-------|-----------|
| 321-392-6024 | +13213926024 | 200 |
| 321-392-6025 | +13213926025 | 201 |
| 321-392-6026 | +13213926026 | 202 |
| 321-392-6027 | +13213926027 | 203 |
| 321-392-6028 | +13213926028 | 204 |
| 321-533-1177 | +13215331177 | 205 |

---

## Step 1: Add DIDs to FHSI Trunk

1. Go to **Admin > SIP Trunks**
2. Select the **Florida High Speed Internet** trunk
3. In **Additional DIDs** section, add all 6 numbers in E.164 format:
   - +13213926024
   - +13213926025
   - +13213926026
   - +13213926027
   - +13213926028
   - +13215331177
4. Click **Save**
5. Verify trunk status remains green/registered

> **Note:** Confirm with FHSI whether they require E.164 (+1XXXXXXXXXX) or 10-digit format (3213926024). Adjust if needed.

---

## Step 2: Enable Voicemail on Each PM Extension

Repeat for extensions 200, 201, 202, 203, 204, 205:

1. Go to **Users** → select PM user
2. Click **Forwarding** tab
3. Enable **Voicemail**
4. Set a **Voicemail PIN** (PM can change via Web Client)
5. Under **No Answer**:
   - Destination: **Voicemail**
6. Under **Busy**:
   - Destination: **Voicemail**
7. Enable **Email Notification**:
   - Enter PM's email address
   - Enable **Attach recording to email**
8. Click **Save**

---

## Step 3: Create Inbound Routing Rules

Create 6 inbound rules (one per DID):

1. Go to **Admin > Call handling**
2. Click **Add Inbound Rule**
3. For each rule:

| Rule Name | DID | Office Hours Destination | Out of Hours Destination |
|-----------|-----|--------------------------|--------------------------|
| PM Direct - 321-392-6024 | 3213926024 | Ext 200 | Ext 200 Voicemail |
| PM Direct - 321-392-6025 | 3213926025 | Ext 201 | Ext 201 Voicemail |
| PM Direct - 321-392-6026 | 3213926026 | Ext 202 | Ext 202 Voicemail |
| PM Direct - 321-392-6027 | 3213926027 | Ext 203 | Ext 203 Voicemail |
| PM Direct - 321-392-6028 | 3213926028 | Ext 204 | Ext 204 Voicemail |
| PM Direct - 321-533-1177 | 3215331177 | Ext 205 | Ext 205 Voicemail |

4. For each rule, set:
   - **Name**: as shown above
   - **DID**: select from dropdown (populated after Step 1)
   - **During office hours** → Extension (PM's extension)
   - **Out of office hours** → Extension Voicemail
5. Click **Save**

---

## Step 4: (Optional) Outbound Caller ID per PM

If PMs should display their personal DID on outbound calls:

1. Go to **Admin > Caller ID**
2. Click **Add Rule** for each PM:

| Outbound From | Set Caller ID To |
|---------------|-----------------|
| Ext 200 | +13213926024 |
| Ext 201 | +13213926025 |
| Ext 202 | +13213926026 |
| Ext 203 | +13213926027 |
| Ext 204 | +13213926028 |
| Ext 205 | +13215331177 |

---

## Step 5: Test Each DID

For each of the 6 numbers:

- [ ] Call DID from external mobile → correct PM extension rings
- [ ] Put PM on DND → call DID → falls to voicemail immediately
- [ ] Let DID ring unanswered → falls to voicemail after timeout
- [ ] Leave voicemail → PM receives email with attached recording
- [ ] (If Step 4 done) PM outbound call shows correct DID as caller ID

---

## Front Desk Transfer Instructions

Project managers can receive transfers from front desk/receptionist via their extension number.

### Blind Transfer (Fast)

1. Answer incoming call
2. Press **Transfer** button (or dial `*2`)
3. Dial PM extension:
   - `200` → PM at 321-392-6024
   - `201` → PM at 321-392-6025
   - `202` → PM at 321-392-6026
   - `203` → PM at 321-392-6027
   - `204` → PM at 321-392-6028
   - `205` → PM at 321-533-1177
4. Press **Transfer** again to complete

> **Note:** Caller transfers immediately. If PM unavailable, call goes to their voicemail.

### Attended Transfer (Confirm First)

1. Answer incoming call
2. Press **Transfer** button (or dial `*2`)
3. Dial PM extension (200–205)
4. Wait for PM to answer
5. Brief PM on caller/reason
6. Press **Transfer** to complete

> **Note:** If PM declines, you can resume call with original caller.

---

## Verification Checklist

- [ ] All 6 DIDs in FHSI trunk Additional DIDs list
- [ ] Trunk status green after save
- [ ] Voicemail enabled on extensions 200–205 with email notification
- [ ] 6 inbound routing rules created and mapped correctly
- [ ] All 6 DID test calls pass
- [ ] Voicemail email delivery confirmed per PM
- [ ] Front desk tested blind transfer to each PM extension
- [ ] Front desk tested attended transfer to each PM extension
