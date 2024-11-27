# Git Tricks

Some extra instructions on working with Git.

## Generating SSH Keys and Adding Them to GitHub

### What are SSH Keys?

SSH (Secure Shell) keys are a pair of cryptographic keys used to authenticate a user to a remote server. They provide a secure way to connect to services like GitHub without needing to enter a username and password every time.

- **Public Key:** This key can be shared with anyone. It is used to encrypt data.
- **Private Key:** This key is kept secret. It is used to decrypt data that was encrypted with the corresponding public key.

When you set up SSH keys, you add your public key to the service you want to connect to (e.g., GitHub). When you try to connect, the service uses your public key to encrypt a message. Only your private key can decrypt this message, proving your identity.

### Why Use SSH Keys?

- **Security:** SSH keys are more secure than passwords because they are much harder to guess or crack.
- **Convenience:** Once set up, you can connect to services like GitHub without needing to enter your username and password every time.

### How to Generate SSH Keys

Follow these steps to generate SSH keys and add them to your GitHub account.

#### Step 1: Check for Existing SSH Keys

First, check if you already have SSH keys on your computer.

1. Open your terminal (macOS/Linux) or Git Bash (Windows).
2. Enter the following command:
   ```bash
   ls -al ~/.ssh
   ```
3. Check if you see files named `id_rsa` and `id_rsa.pub`. If you do, you already have SSH keys and can skip to Step 3.


#### Step 2: Generate New SSH Keys
If you don't have SSH keys, generate a new pair.

1. In your terminal (macOS/Linux) or Git Bash (Windows), enter the following command:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

- Replace `your_email@example.com` with your email address.

2. When prompted to "Enter a file in which to save the key," press Enter. This will save the key in the default location `(~/.ssh/id_rsa)`.

3. When prompted to enter a passphrase, you can either enter a secure passphrase or press Enter to leave it empty (not recommended for security reasons).


#### Step 3. Add Your SSH Key to the SSH Agent

1. Start the SSH agent in the background:
- macOS/Linux:
```bash
eval "$(ssh-agent -s)"
```

- Windows (Git Bash):
```bash
eval $(ssh-agent -s)
```

2. Add your SSH private key to the SSH agent:
- macOS/Linux:

```bash
ssh-add ~/.ssh/id_rsa
```

- Windows (Git Bash)
```bash
ssh-add /c/Users/YOUR_USERNAME/.ssh/id_rsa
```
- Replace `YOUR_USERNAME` with your Windows username.


#### Step 4: Add Your SSH Key to GitHub

1. Copy the SSH public key to your clipboard:
- macOS/Linux:
```bash
pbcopy < ~/.ssh/id_rsa.pub
```

- Linux:
```bash
xclip -sel clip < ~/.ssh/id_rsa.pub
```


- Windows (Git Bash)
```bash
cat ~/.ssh/id_rsa.pub | clip
```
2. Go to GitHub and log in to your account.
3. In the upper-right corner of any page, click your profile photo, then click **Settings**.
4. In the user settings sidebar, click **SSH and GPG keys.**
5. Click **New SSH key**.
6. In the "Title" field, add a descriptive label for the new key. For example, "My Laptop".
7. Paste your key into the "Key" field.
8. Click **Add SSH key**.


#### Step 5: Test Your SSH Connection

1. In your terminal (macOS/Linux) or Git Bash (Windows), enter the following command to test your connection

```bash
ssh -T git@github.com
```
2. You may see a warning about the authenticity of the host. Type yes to continue.
3. If everything is set up correctly, you should see a message like:

```
Hi YOUR_GITHUB_USERNAME! You've successfully authenticated, but GitHub does not provide shell access.
```

### Summary
By generating SSH keys and adding them to your GitHub account, you can securely and conveniently connect to GitHub without needing to enter your username and password every time. This is especially useful for working with repositories and collaborating on projects.

Feel free to reach out if you have any questions or need further assistance!