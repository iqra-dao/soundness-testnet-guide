# Soundness CLI 🚀

A command-line tool for interacting with the Soundness Layer testnet.

## Getting Started Guide (Recommended)

This guide provides the simplest path for new users. Follow these steps to get started with the testnet.

---

### Step 1: Install the CLI ⚙️

We recommend installing via **`soundnessup`**. It's the easiest way to get set up.

1.  First, run the installer script by executing the following command in your terminal:
    ```bash
    curl -sSL [https://raw.githubusercontent.com/soundnesslabs/soundness-layer/main/soundnessup/install](https://raw.githubusercontent.com/soundnesslabs/soundness-layer/main/soundnessup/install) | bash
    ```

2.  Next, update your shell's environment so it can find the new command. You can either restart your terminal or run one of the following commands:
    * **For Bash users:**
        ```bash
        source ~/.bashrc
        ```
    * **For Zsh users:**
        ```bash
        source ~/.zshenv
        ```

3.  Finally, use `soundnessup` to install the main CLI tool:
    ```bash
    soundnessup install
    ```
    To update the tool in the future, you can run `soundnessup update`.

---

### Step 2: Get Testnet Access

To join the testnet, you will need one of the following:
* **Discord Role:** Join our [Soundness Labs Discord](https://discord.gg/soundness) and get the **Onboarded** role.
* **Invite Code:** Follow our [X (Twitter) account](https://twitter.com/SoundnessLabs). We regularly post invite codes.

---

### Step 3: Manage Your Key 🔑

A key is required to sign your proof submissions and identify you on the network.

#### Generating a New Key
* **If you have the "Onboarded" role from Discord:** You should already have a key. You do not need to generate a new one.
* **If you are using an invite code:** You will need to generate a new key pair. Run the following command, replacing `your-key-name` with a name of your choice:
    ```bash
    soundness-cli generate-key --name your-key-name
    ```
    **Important:** A **mnemonic phrase** will be displayed. Save it in a safe and secure place! This is the only way to recover your key if it's lost.

#### Importing (Recovering) a Key
If you need to restore your key on a new machine or after a reset, you can use the `import-key` command with your saved mnemonic phrase:
```bash
soundness-cli import-key --name <name> --mnemonic "<your-saved-mnemonic-phrase>"
