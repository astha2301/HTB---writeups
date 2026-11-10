# Hack The Box - Redeemer

## Machine Information

| Field | Details |
|---|---|
| Platform | Hack The Box |
| Machine Name | Redeemer |
| Difficulty | Very Easy |
| Operating System | Linux |
| IP Address | `<TARGET_IP>` |
| Main Service | Redis |
| Tools Used | Nmap, Redis CLI |

## Objective

The objective of this machine is to identify exposed services, discover an unsecured Redis database, enumerate its keys, and retrieve the flag.

## 1. Reconnaissance

First, scan the target machine to identify open ports and running services.

```bash
nmap -sV -sC -p- <TARGET_IP>
```

**What this does:**
- `-sV` – Detects service versions.
- `-sC` – Runs default NSE scripts.
- `-p-` – Scans all TCP ports.

### Findings

- Port 6379 – Redis database service.
- Redis was accessible without authentication.

## 2. Redis Enumeration

Connect to the Redis server using:

```bash
redis-cli -h <TARGET_IP>
```

Check the Redis server version:

```bash
INFO
```

Look for the Redis version in the server information.

## 3. Database Enumeration

Check the number of databases:

```bash
INFO keyspace
```

Select database index 0:

```bash
SELECT 0
```

Find the number of keys:

```bash
DBSIZE
```

List all available keys:

```bash
KEYS *
```

Retrieve the stored values using:

```bash
GET <key>
```

For keys containing other Redis data types, use the appropriate commands such as `HGETALL`, `LRANGE`, or `SMEMBERS`.

## 4. Retrieving the Flag

After identifying the key containing the flag, retrieve its value.

```bash
GET <flag_key>
```

Copy the flag and submit it on the Hack The Box platform.

## 5. Key Takeaways

- Learned how to perform network scanning using Nmap.
- Understood Redis and its default port (6379).
- Practised connecting to Redis using Redis CLI.
- Learned database enumeration using `INFO`, `DBSIZE`, and `KEYS`.
- Understood the security risks of exposing Redis without authentication.

## Conclusion

Redeemer demonstrates how an improperly secured Redis database can expose sensitive information. It was a useful introduction to database enumeration and understanding the importance of securing exposed services.

**Status:** Machine Completed ✅
