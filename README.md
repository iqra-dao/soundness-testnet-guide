# Soundness Testnet: Complete Guide

This guide provides all the steps needed to prepare your server, register for the testnet, play a game, and submit your proof.

---

### Step 1: Prepare Server & Install CLI

First, we will update the server and install all the required software, including Rust and the Soundness CLI.

1.  **Update your server packages:**
    ```bash
    sudo apt update && sudo apt upgrade -y
    ```

2.  **Install Rust (a prerequisite):**
    ```bash
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    ```
    *(When prompted, choose option 1 for the default installation.)*

3.  **Install and update the Soundness CLI:**
    *(Copy and paste the entire block below into your terminal)*
    ```bash
    curl -sSL https://raw.githubusercontent.com/soundnesslabs/soundness-layer/main/soundnessup/install | bash
    source ~/.bashrc
    soundnessup install
    soundnessup update
    ```

---

### Step 2: Generate & Manage Your Key

Your key is your identity on the network. You must generate one and submit your public key to get access.

1.  **Generate a New Key:**
    *(Replace `my-key` with a name of your choice.)*
    ```bash
    soundness-cli generate-key --name my-key
    ```
    After running this, two important things will be displayed:
    * **Mnemonic Phrase:** A list of words. **SAVE THIS IN A VERY SAFE PLACE.** This is the only way to recover your key.
    * **Public Key:** A long string of characters. You will need this for the next step.

2.  **Get Testnet Access via Discord:**
    * Join the [Soundness Labs Discord](https://discord.gg/soundnesslabs).
    * Go to the `🐬│soundness-cockpit` channel.
    * Use the `/access` command and paste your **Public Key** when prompted.

3.  **(Optional) Importing an Existing Key:**
    If you already have a mnemonic phrase, you can recover your key using this command:
    ```bash
    soundness-cli import-key --name <name> --mnemonic "<mnemonic>"
    ```
    * **REPLACE `<name>`** with the key name you want to use.
    * **REPLACE `<mnemonic>`** with your saved seed phrase.

---

### Step 3: Play a Game & Get Your Proof

Now that you have access, it's time to play.

* Go to the [Soundness Website](https://soundness.xyz/) and play a game (e.g., 8queens or tictactoe).
* When you win, the game will provide you with a **Proof Blob ID**. This is the code that proves you won. Copy this ID.

---

### Step 4: Submit Your Proof

Use the CLI to send your winning proof to the network.

1.  **Run the `send` command:**
    *(Fill in the details between the `< >` brackets.)*
    ```bash
    soundness-cli send \
    --proof-file <your-proof-blob-id> \
    --game <game-name> \
    --key-name <your-key-name> \
    --proving-system ligetron \
    --payload '<json-payload>'
    ```

2.  **Command Details:**
    * `--proof-file`: The **Proof Blob ID** you got from the game.
    * `--game`: The name of the game you played (e.g., `8queens` or `tictactoe`).
    * `--key-name`: The name you chose for your key in Step 2 (e.g., `my-key`).
    * `--proving-system`: Use `ligetron` for the current testnet games.
    * `--payload`: A JSON string with specific inputs for the proof (usually provided with the proof).

---

### Advanced: Alternative `send` Commands

Here are other ways to use the `send` command for more advanced scenarios.

* **Using Local Files:**
    ```bash
    soundness-cli send --proof-file path/to/proof.proof --elf-file path/to/program.elf --key-name my-key
    ```

* **Using a mix of local files and Blob IDs:**
    ```bash
    soundness-cli send --proof-file path/to/proof.proof --elf-file <walrus-blob-id> --key-name my-key
    ```

* **Specifying a different Proving System:**
    ```bash
    soundness-cli send --proof-file <path-or-blob-id> --elf-file <path-or-blob-id> --key-name my-key --proving-system <sp1||ligetron||risc0>
    ```

✅ **That's it! You have completed the full process.**
