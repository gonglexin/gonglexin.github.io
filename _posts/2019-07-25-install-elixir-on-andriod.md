---
title: "在安卓手机上安装 Elixir"
categories: [tech, elixir]
---

记录一下在安卓手机上安装 [Elixir](https://elixir-lang.org/) 的过程。

1. 在手机上安装 [Termux](https://termux.com/) 应用

2. 开启 SSH 服务（**非必须**, 开 `ssh` 只是为了便于 PC 端访问操作手机，比在手机上打字方便）
  * 安装相关包
  ```bash
  apt update
  apt upgrade
  pkg install openssh
  pkg install net-tools
  ```
  * 设置密码并开启 ssh
  ```bash
  # 设置一个密码
  passwd
  # 开启服务
  sshd
  ```
  * 查看手机 ip
  ```bash
  ifconfig
  ```

3. 安装 Elixir
  * 从 PC 端登录手机
  ```bash
  # 确保手机和 PC 处在同一网络，用上一步获取的安卓手机 ip 登录
  # 拷贝公钥到安卓手机(需输入前面设置的密码)
  ssh-copy-id -p 8022 -i your_public_key_file andriod_ip
  # 登录
  ssh -p 8022 android_ip
  ```
  * 安装相关包 (PC 端登录之后，就可以开始正式的安装步骤了)
  ```bash
  pkg install unzip
  pkg install erlang
  ```
  * 安装 Elixir, 参考 [https://github.com/hexpm/bob#elixir-builds](https://github.com/hexpm/bob#elixir-builds) 确定好 elixir 和 erlang otp 版本, 这里以 elixir 1.9.1 otp 22 为例:
  ```bash
  mkdir elixir
  cd elixir
  # wget https://repo.hex.pm/builds/elixir/{REF}-otp-{OTP_MAJOR_VERSION}.zip
  wget https://repo.hex.pm/builds/elixir/v1.9.1-otp-22.zip
  unzip v1.9.1-otp-22.zip
  rm v1.9.1-otp-22.zip
  ```
  * 设置 PATH, 保存到 bashrc
  ```bash
  vi .bashrc
  export PATH=$PATH:$HOME/elixir/bin
  ```

4. 验证
```bash
elixir -v
#> Erlang/OTP 22 [erts-10.4.4] [source] [64-bit] [smp:8:8] [ds:8:8:10] [async-threads:1]
#>
#> Elixir 1.9.1 (compiled with Erlang/OTP 22)
```
