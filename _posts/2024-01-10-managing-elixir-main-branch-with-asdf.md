---
title: "Managing Elixir's main branch with asdf"
categories: [tech, elixir]
---

I've always used [asdf](https://github.com/asdf-vm/asdf) to manage Elixir versions, and I've also had a persistent need to run projects or experiments with the latest code from the Elixir repo (main branch). Installing the main branch is quite simple:

1. Clone the Elixir code and build it locally:
```bash
git clone https://github.com/elixir-lang/elixir.git /path/to/elixir
cd /path/to/elixir && make
```

2. Create a symlink in the asdf installs directory and switch to the main version:
```bash
ln -s /path/to/elixir ~/.asdf/installs/elixir/main
asdf reshim elixir main
asdf shell elixir main | asdf global elixir main
```

3. Verify:
```bash
$ asdf list elixir
  1.15.7-otp-26
  1.16.0-otp-26
 *main
```

4. Daily update:
```bash
cd /path/to/elixir && git pull && make
```

* You can write the above  update commands to a script and run it periodically to ensure you're always using the latest version of the main branch.

* If running make directly throws compilation errors, you need to delete the previous build artifacts before rebuilding:
```bash
cd /path/to/elixir
make clean && make
```

* Using the main branch can be somewhat unstable as it's still under development.
