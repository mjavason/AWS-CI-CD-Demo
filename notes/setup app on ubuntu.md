### EC2 Instance Setup Cheat Sheet

#### Switch to Root User

```bash
sudo su -
```

#### Install NVM (Node Version Manager)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```

#### Activate NVM

```bash
. ~/.nvm/nvm.sh
```

#### Install Node.js

```bash
nvm install node
```

#### Install Git (No need for `sudo` as root user)

```bash
sudo apt-get update -y
sudo apt-get install git -y
```

#### Verify Installation

- **Check Node.js Version**
  ```bash
  node -v
  ```
- **Check Git Version**
  ```bash
  git --version
  ```

#### Clone a Git Repository (Initial Attempt Will Fail Without SSH Key)

```bash
git clone git@github.com:drsimplegraffiti/ec2-deploy.git
```

#### Set Up SSH Key for GitHub

1. **Generate an SSH Key**

   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   - Press `Enter` three times to accept defaults.
   - Optionally, add a passphrase for extra security.

2. **Start the SSH Agent**

   ```bash
   eval "$(ssh-agent -s)"
   ```

3. **Add the SSH Key to the Agent**

   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

4. **Copy SSH Key to Clipboard**

   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```

   - Paste the output into **GitHub**:
     - Navigate to **Settings > SSH and GPG Keys > New SSH Key**.
     - Paste the key and save it.

5. **Test the SSH Connection to GitHub**
   ```bash
   ssh-keyscan github.com >> ~/.ssh/known_hosts
   ssh -T git@github.com
   ```

#### Clone the Repository Again (Now It Should Work)

```bash
git clone git@github.com:drsimplegraffiti/ec2-deploy.git
```

#### Navigate to the Repository and Start the Application

1. **List Directory Contents**

   ```bash
   ls -la
   ```

2. **Enter the Repository Folder**

   ```bash
   cd ec2-deploy
   ```

3. **Install Dependencies and Start the Server**
   ```bash
   npm install
   npm start
   ```

#### (Optional) Use PM2 to Manage the Server

1. **Install PM2 Globally**

   ```bash
   npm install pm2 -g
   ```

2. **Start the Server with PM2**
   ```bash
   pm2 start app.js
   ```

#### Test the Server

- Use the EC2 instance's IP address to test the server:
  ```bash
  curl <EC2-IP-ADDRESS>
  ```
  🎉 **Your server is now running on EC2!** Note that it is insecure as it is currently using HTTP.
