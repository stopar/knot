# Knot 🪢

**Self-hosted Docker registry & remote builder for Kamal 2 with zero external dependencies**

Deploy your own private Docker registry and build server in 3 commands. No Docker Hub account required.

## Why?

- **Zero Dependencies**: No Docker Hub or external registry required
- **Private**: Your containers stay on your infrastructure  
- **Fast**: No rate limits or slow pulls from Docker Hub
- **Remote Building**: Build images directly on your VPS
- **Mac-Friendly**: Perfect for M1/M2/M3 Macs with ARM64 → AMD64 builds
- **Architecture Freedom**: Build AMD64 images from any machine
- **Kamal 2 Ready**: Works perfectly with Kamal 2 out of the box
- **Secure**: HTTPS + authentication included

## Perfect for Mac Users

- ✅ **ARM64 → AMD64** - build server images from your M1/M2/M3 Mac  
- ✅ **Consistent environment** - Linux builds for Linux deployments
- ✅ **Zero external dependencies** - no Docker Hub account needed

## Quick Start

**Run these commands on your local machine** (not on the VPS):

```bash
git clone https://github.com/deployTo-Dev/knot.git
cd knot

./knot setup   # Configure your VPS and domain
./knot deploy  # Deploy registry + builder to your VPS (zero dependencies!)
./knot test    # Verify it works
```

## 📹 Video Walkthrough

Watch Knot in action - from setup to deployment in just a few minutes:

[![Knot Walkthrough](https://img.youtube.com/vi/pNO0p8X1udc/0.jpg)](https://www.youtube.com/watch?v=pNO0p8X1udc)

**[▶️ Watch on YouTube](https://www.youtube.com/watch?v=pNO0p8X1udc)**

## What you need

- **VPS** with SSH access (1GB RAM minimum)
- **Domain** pointing to your VPS (e.g., `registry.yourdomain.com`)  
- **That's it!** No Docker Hub or external registry accounts needed

## How it works

Knot uses a clever workaround inspired by [Jason Nochlin's blog post](https://nochlin.com/blog/host-your-own-docker-registry-with-kamal-2#conclusion) to bypass Kamal's external registry requirement. Instead of needing Docker Hub credentials, it uses smart bootstrapping with `deployto.dev` to deploy your own registry with zero external dependencies.

## Using your registry & builder

After deployment, use it in your Kamal 2 apps:

```yaml
# config/deploy.yml in your app
registry:
  server: registry.yourdomain.com
  username: admin
  password: <%= ENV["REGISTRY_PASSWORD"] %>

builder:
  arch: amd64
  remote: ssh://user@your-vps-ip
```

Then build and deploy normally:
```bash
kamal build   # Builds on your VPS (fast!)
kamal deploy  # Deploys from your registry
```

## Commands

Run from your local machine:

- `./knot setup` - Configure registry & builder (one time)
- `./knot deploy` - Deploy to your VPS via SSH (zero dependencies)
- `./knot status` - Check if running
- `./knot logs` - View registry logs
- `./knot test` - Test connectivity

## Zero Dependencies

Unlike traditional Kamal setups that require:
- ❌ Docker Hub account and credentials
- ❌ External registry service
- ❌ Temporary registry setup

Knot requires:
- ✅ Just your VPS and domain
- ✅ Uses smart bootstrapping
- ✅ Self-contained deployment

## Credits

This project was inspired by the excellent work in [Jason Nochlin's blog post](https://nochlin.com/blog/host-your-own-docker-registry-with-kamal-2#conclusion) about hosting your own Docker registry with Kamal 2. Knot automates and simplifies his approach while adding the zero-dependency bootstrap method.

## That's it

Your VPS now runs:
- ✅ Docker Registry v2 with HTTPS via Let's Encrypt
- ✅ Remote builder for Kamal 2 deployments
- ✅ Password authentication  
- ✅ Works with any Kamal 2 deployment 
- ✅ Zero external dependencies

## License

MIT License - see [LICENSE](LICENSE) file for details. 