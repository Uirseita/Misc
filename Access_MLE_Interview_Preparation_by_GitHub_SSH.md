
To clone a GitHub repository using SSH, you need to set up SSH access to GitHub and then use the SSH URL of the repository to clone it. Here’s a step-by-step guide on how to do it:

### 1. **Set Up SSH Key (if not already done)**

If you haven't already set up an SSH key for GitHub, you'll need to generate one and add it to your GitHub account.

#### **Generate an SSH Key:**
- On your local machine, open a terminal and run the following command to generate an SSH key (replace `your_email@example.com` with your email):

  ```bash
  ssh-keygen -t ed25519 -C "your_email@example.com"
  ```

  (If your system doesn't support Ed25519, use RSA: `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`).

- When prompted, press Enter to accept the default file location or specify a different path.

- You'll also be asked to create a passphrase. This is optional, but it's recommended for security.

#### **Add the SSH Key to the SSH Agent:**

- Start the SSH agent:

  ```bash
  eval "$(ssh-agent -s)"
  ```

- Add your private key to the SSH agent:

  ```bash
  ssh-add ~/.ssh/id_ed25519
  ```

  (If you used RSA, it might be `~/.ssh/id_rsa` instead of `id_ed25519`.)

#### **Add the SSH Key to Your GitHub Account:**

- Copy your SSH public key to the clipboard:

  ```bash
  cat ~/.ssh/id_ed25519.pub
  ```

  (If RSA, use `~/.ssh/id_rsa.pub` instead.)

- Go to your [GitHub SSH settings page](https://github.com/settings/ssh/new) and add a new SSH key.
  - Click "New SSH key"
  - Paste the key from the clipboard and give it a title
  - Click "Add SSH key"

### 2. **Clone a GitHub Repository via SSH**

Once your SSH key is set up, you can clone repositories using SSH.

#### **Find the SSH URL of the Repository:**

- Go to the repository on GitHub you want to clone.
- Click the green **Code** button, and in the dropdown, select **SSH**. You’ll see an SSH URL that looks like:

  ```
  git@github.com:username/repo_name.git
  ```

#### **Clone the Repository:**

- In your terminal, run:

  ```bash
  git clone git@github.com:username/repo_name.git
  ```

Replace `username/repo_name` with the actual GitHub repository's SSH URL.

### 3. **Verify the Clone**

After the clone is complete, you can navigate into the repository folder:

```bash
cd repo_name
```

Then, you can interact with the repository using Git commands (e.g., `git pull`, `git push`).

### Troubleshooting

- **Permission denied (publickey):** This error indicates SSH is not properly configured. Ensure your public key is added to your GitHub account, and your SSH agent is running with the key added (`ssh-add`).
  
- **SSH key authentication issues:** Test your SSH connection to GitHub by running:

  ```bash
  ssh -T git@github.com
  ```

  If successful, you'll see a message like:

  ```
  Hi username! You've successfully authenticated, but GitHub does not provide shell access.
  ```

That's it! You should now be able to clone repositories using SSH by 
```bash
git clone git@github.com:Uirseita/MLE_interview_prep.git
```
