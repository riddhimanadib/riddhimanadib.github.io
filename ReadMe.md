## Simple site: Easy websites with GitHub pages

[Github Pages](https://pages.github.com) provide a simple way to make a
website using Markdown and git.

This is a minimal tutorial to get started.

View the thing [here](https://kbroman.org/simple_site).

---

To the extent possible under law,
[Karl Broman](https://github.com/kbroman)
has waived all copyright and related or neighboring rights to
&ldquo;[simple site](https://github.com/kbroman/simple_site)&rdquo;.
This work is published from the United States.
<br/>
[![CC0](https://i.creativecommons.org/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

---

### Run and check website locally

[Check this page](https://kbroman.org/simple_site/pages/local_test.html)

---

### HOW TO INSTALL RUBY AND GEM TO MAC

Here’s a **clean, safe, and up-to-date way** to install and update Ruby and RubyGems on macOS **without touching the system Ruby**.
You’ll use **Homebrew + rbenv**, the most common modern setup (Ruby 3.4.7 is the latest release as of October 2025).

---

## 🧩 Step-by-Step Instructions

### **1️⃣ Install Xcode Command Line Tools**

You need these for compiling Ruby.

```bash
xcode-select --install
```

Follow the pop-up instructions and wait for installation to complete.

---

### **2️⃣ Install Homebrew (if not installed)**

Check:

```bash
brew -v
```

If not installed:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After install, make sure your shell sees `brew`:

**Apple Silicon (M1/M2/M3):**

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

**Intel Macs:**

```bash
echo 'eval "$(/usr/local/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/usr/local/bin/brew shellenv)"
```

---

### **3️⃣ Install rbenv and ruby-build**

```bash
brew install rbenv ruby-build
```

These manage multiple Ruby versions completely separate from system Ruby.

---

### **4️⃣ Initialize rbenv**

Add rbenv to your shell startup:

```bash
echo 'eval "$(rbenv init - zsh)"' >> ~/.zshrc
source ~/.zshrc
```

Check rbenv:

```bash
rbenv -v
```

---

### **5️⃣ Install the Latest Ruby Version (e.g., 3.4.7)**

List available Ruby versions:

```bash
rbenv install -l
```

Install the latest stable (3.4.7):

```bash
rbenv install 3.4.7
```

Set it as the default for all shells:

```bash
rbenv global 3.4.7
```

Reload environment:

```bash
rbenv rehash
```

Confirm:

```bash
ruby -v
# → ruby 3.4.7 (2025-10-07)
```

---

### **6️⃣ Update RubyGems (gem command)**

Now that you’re using your own Ruby, safely update RubyGems:

```bash
gem update --system
```

Then update all installed gems:

```bash
gem update
```

---

### **7️⃣ Verify Everything**

Check where your Ruby and gem live (should **not** be `/usr/bin`):

```bash
which ruby
which gem
```

You should see something like:

```
/Users/<you>/.rbenv/shims/ruby
/Users/<you>/.rbenv/shims/gem
```

---

### **8️⃣ (Optional) Keep Ruby Updated**

To update later:

```bash
brew upgrade rbenv ruby-build
rbenv install -l
rbenv install 3.4.x   # whatever the latest is
rbenv global 3.4.x
rbenv rehash
```

---

✅ **Now you can safely run any `gem install ...` command** — it’ll use your rbenv Ruby and not touch the macOS system Ruby.