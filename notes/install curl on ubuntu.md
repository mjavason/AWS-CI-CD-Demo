The issue here is that the `curl` command is not installed on your system. You can resolve this by installing `curl` using your package manager.

### Steps to Install `curl` on Ubuntu

1. **Update the package index:**
   ```bash
   sudo apt update
   ```

2. **Install `curl`:**
   ```bash
   sudo apt install curl -y
   ```

3. **Verify the installation:**
   After the installation completes, verify that `curl` is available by running:
   ```bash
   curl --version
   ```

   You should see the installed version of `curl`.

4. **Retry your `nvm` installation:**
   Once `curl` is installed, you can run the `nvm` installation command again:
   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
   ```

Let me know if you encounter any further issues!