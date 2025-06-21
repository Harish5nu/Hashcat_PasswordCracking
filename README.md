
# 🔐 Basic Guide to Password Cracking with Hashcat

Hashcat is a fast and flexible password cracking tool used in ethical hacking and cybersecurity testing.

---

## ✅ Step 1: Identify the Hash Type

Use Hashcat's help to identify the mode ID for a hash type.

### Common Hash Modes:
| Hash Type | Mode | Example Hash |
|-----------|------|---------------|
| MD5       | 0    | e807f1fcf82d132f9bb018ca6738a19f |
| SHA1      | 100  | aaf4c61ddcc5e8a2dabede0f3b482cd9aea9434d |
| NTLM      | 1000 | 32ed87bdb5fdc5e9cba88547376818d4 |

Use:
```bash
hashcat --help
```

---

## ✅ Step 2: Prepare Your Files

### Create a file containing your hash:
```bash
echo "e807f1fcf82d132f9bb018ca6738a19f" > hash.txt
```

### Use a wordlist:
The most common wordlist is:
```
/usr/share/wordlists/rockyou.txt
```

---

## ✅ Step 3: Crack the Hash

### Basic Syntax:
```bash
hashcat -m <mode> <hash_file> <wordlist>
```

### Example: Crack an MD5 hash
```bash
hashcat -m 0 hash.txt /usr/share/wordlists/rockyou.txt
```

### Show Cracked Passwords
```bash
hashcat -m 0 hash.txt /usr/share/wordlists/rockyou.txt --show
```

---

## 🔁 Brute-Force Attack Examples (`-a 3`)

Brute-force uses patterns instead of a wordlist.

### Pattern symbols:
| Symbol | Meaning         |
|--------|------------------|
| ?l     | lowercase letter |
| ?u     | uppercase letter |
| ?d     | digit (0–9)      |
| ?s     | special char     |
| ?n     | number (same as ?d) |

### Examples:

```bash
hashcat -m 0 -a 3 662c2b58a7130417825951643c2fe32e ?l?l?l?s?n?n?n?n
hashcat -m 0 -a 3 662c2b58a7130417825951643c2fe32e ?l?l?l?s?d?d?d?d
hashcat -m 0 -a 3 e468b60fd5c6dc9aeec15b2f1d7c14be ?l?l?l?l?s?s?d?d?d?d
```

---

## ✅ Bonus: Create Your Own Hash for Testing

### Create an MD5 or SHA1 hash:
```bash
echo -n "yourpassword" | md5sum
echo -n "yourpassword" | sha1sum
```

Use the resulting hash in your `hash.txt` file.

---

## ⚠️ Important Tips

- Always have **permission** before testing with hashes.
- Use **GPU** for faster cracking.
- Use the `--help` command to explore more features.

---

🛡️ Practice responsibly and ethically!
