
# 🔐 GitHub SSH Key Demo — CSCI 135

This guide walks through setting up a new SSH key on GitHub.
More information on GitHub:
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
---

## 1. Check for Existing SSH Keys:
Open your terminal and run:

```bash
ls -al ~/.ssh
```
Look for these files:
- `id_ed25519` and `id_ed25519.pub`
- or `id_rsa` and `id_rsa.pub` (older RSA type)
If they exist, you might already have a key. 

---

## 2. Generate a new key:

```bash
ssh-keygen -t ed25519 -C "yourEmail@example.com"
```

- `-t ed25519`: uses the modern key type
- `-C`: adds a comment (usually your email)
- `-f`: specifies the output file name (optional to give it a name)

You'll see prompts like this:

```
Enter file in which to save the key (/Users/you/.ssh/id_ed25519): [Press Enter]
Enter passphrase (empty for no passphrase): [Press Enter]
Enter same passphrase again: [Press Enter]
```

> ℹ️ If you just press **Enter** at each step, it will accept the default file path and **no passphrase**.

---

## 3. Start the SSH agent and add the key:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

---

## 4. Copy the public key to your clipboard:

```bash
cat ~/.ssh/id_ed25519.pub
```

Then go to [GitHub → SSH Settings](https://github.com/settings/keys), click **New SSH Key**, and paste it there.

---

## 5. Test your connection:

```bash
ssh -T git@github.com
```

Expected output:
```
Hi your-username! You've successfully authenticated...
```

---

