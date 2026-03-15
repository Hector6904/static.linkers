# Atomic Shard Deception

**CTF:** Cipathon '26 — Round 1
**Category:** Web Exploitation
**Difficulty:** Expert
**Points:** 500
**Solved by:** Hector1516

---

## Challenge Description

> Every edge-node in the ApexCache network is a digital mirror. It remembers what it sees, but its memory is triggered by the "Signature" of the asset. The sharding logic uses a simple heuristic to decide what is persistent and what is volatile. If you can poison the mirror's memory by masking a sensitive identity request as a static, harmless invariant, you might just catch the Admin's ghost lingering in the cache.

**Default credentials provided:**
- Login: `admin@apexcache.io`
- Password: `ApexAdmin123!@#`

**Target:** `http://78.46.147.244:8893/`

---

## Approach

### Step 1 — Access the Application

Navigated to the provided URL and logged in using the default credentials.

![Landing Page](./1773571000018_image.png)

### Step 2 — Explore the Dashboard

After logging in, landed on the **Cluster Management Hub**. Explored every available button and section on the dashboard to understand the application's functionality.

![Dashboard](./1773571014112_image.png)

### Step 3 — Inspect Network Traffic

Opened **DevTools → Network tab** and monitored the API requests being made in the background while interacting with the dashboard. Found a `metadata` endpoint making a `Fetch/XHR` request.

### Step 4 — Extract the Flag

Clicked on the `metadata` request and checked the **Response** tab. The JSON response contained the flag directly in the `flag` field.

```json
{
  "access_key": "AKIA-APEX-9921-X",
  "flag": "CIPH{C4CH3_D3C3PT10N_IS_TH3_N3W_BLACK}",
  "role": "Global Optimizer",
  "server_status": "Overheated",
  "username": "admin"
}
```

![DevTools Network Response](./1773565855248_image.png)

---

## Flag

```
CIPH{C4CH3_D3C3PT10N_IS_TH3_N3W_BLACK}
```

---

## Solve Confirmation

![Solve Screenshot](./1773570981378_image.png)

---

## Key Takeaway

The flag wasn't hidden behind any complex exploitation — it was sitting in a background API response that the dashboard was already fetching on load. The challenge description hinted at cache poisoning, but the actual solve was simply checking the **Network tab in DevTools** for unprotected API responses leaking sensitive data. Always inspect background requests before going deep on a web challenge.
