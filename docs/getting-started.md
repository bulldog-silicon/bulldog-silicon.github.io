# Getting Started

Welcome to Bulldog Silicon! This guide will walk you through setting up your environment for hands-on integrated circuit design.

## STEP 1: Prepare Your Computer

Before getting started, make sure you have:

1. A laptop or computer running Windows, macOS, or Linux.
2. A stable internet connection.
3. Recommended **20 GB of available storage space.** 
4. Permission to install software on your computer.


## Step 2: Install Git

Git is a version control tool that allows us to download and manage project files from GitHub.

"Check if Git is already installed"
    Open your terminal and run:

    bash
    git --version
    
    If a version number appears, Git is installed and you can continue to the next step.

=== "Windows"

    1. Visit [Git](https://git-scm.com/install).
    2. Download the installer for your computer.
    3. Run the installer and follow the installation wizard.
    4. Keep the default settings unless instructed otherwise.
    5. Open PowerShell or Git Bash and verify:

    ```bash
    git --version
    ```

=== "macOS"

    1. Open Terminal.
    2. Check if Git is installed:

    ```bash
    git --version
    ```

    3. If Git is missing, install Apple's Command Line Tools:

    ```bash
    xcode-select --install
    ```

    4. Follow the prompts and verify the installation.

=== "Linux (Ubuntu)"

    1. Open Terminal.
    2. Update the package list and install Git:

    ```bash
    sudo apt update
    sudo apt install git
    ```

    3. Verify the installation:

    ```bash
    git --version
    ```


## STEP 3: Install the Required Software

Throughout the program, we'll use open-source Electronic Design Automation (EDA) tools to design, simulate, and verify integrated circuits.

We'll use **[IIC-OSIC-TOOLS](https://github.com/iic-jku/IIC-OSIC-TOOLS)**, which includes Xschem, ngspice, Magic VLSI, Netgen, KLayout, and several Process Design Kits (PDKs).

You don't need to install these tools individually.

### Installation Instructions

Select your operating system below and follow the instructions.

=== "macOS"

    **1. Install Docker Desktop**

    1. Visit [Docker Desktop for Mac](https://docs.docker.com/desktop/setup/install/mac-install/).
    2. Download the version compatible with your Mac (Apple Silicon or Intel).
    3. Open the downloaded `.dmg` file and move Docker into Applications.
    4. Open Docker Desktop and complete the setup.

    **2. Verify Docker Installation**

    Open Terminal and run:

    ```bash
    docker --version
    docker info
    ```

    Both commands should execute successfully.

    **3. Download IIC-OSIC-TOOLS**

    First, verify that Git is installed:

    ```bash
    git --version
    ```

    Create a directory for the software:

    ```bash
    mkdir -p ~/eda
    cd ~/eda
    ```

    Clone the official repository:

    ```bash
    git clone https://github.com/iic-jku/IIC-OSIC-TOOLS.git
    cd IIC-OSIC-TOOLS
    ```

    **4. Create Your Design Folder**

    ```bash
    mkdir -p ~/eda/designs
    ```

    Your circuit files will be saved here so they remain accessible outside the Docker container.

    **5. Launch IIC-OSIC-TOOLS**

    Make sure Docker Desktop is running.

    ```bash
    ./start_vnc.sh
    ```

    The first launch downloads the design environment.

    Once it starts, follow the browser address shown in Terminal.

=== "Windows"

    **1. Install Docker Desktop**

    1. Visit [Docker Desktop for Windows](https://docs.docker.com/desktop/setup/install/windows-install/).
    2. Download and run the installer.
    3. Enable the WSL2 backend when prompted.
    4. Restart your computer if required.
    5. Open Docker Desktop.

    **Note:** Your computer must support virtualization and meet Docker's WSL2 requirements.

    **2. Verify Docker Installation**

    Open PowerShell and run:

    ```powershell
    docker --version
    docker info
    ```

    **3. Install Git**

    Download [Git for Windows](https://git-scm.com/install/windows) if it is not already installed.

    Verify with:

    ```powershell
    git --version
    ```

    **4. Download IIC-OSIC-TOOLS**

    In PowerShell:

    ```powershell
    mkdir "$HOME\eda" -Force
    cd "$HOME\eda"
    ```

    Download the repository:

    ```powershell
    git clone https://github.com/iic-jku/IIC-OSIC-TOOLS.git
    cd IIC-OSIC-TOOLS
    ```

    **5. Create Your Design Folder**

    ```powershell
    mkdir "$HOME\eda\designs" -Force
    ```

    **6. Launch IIC-OSIC-TOOLS**

    Make sure Docker Desktop is running.

    ```powershell
    .\start_vnc.bat
    ```

    Once the environment starts, follow the browser address displayed in PowerShell.

=== "Linux (Ubuntu)"

    These instructions are for Ubuntu or compatible Debian-based systems.

    **1. Install Docker**

    Follow the official [Docker Engine installation instructions for Ubuntu](https://docs.docker.com/engine/install/ubuntu/).

    Verify the installation:

    ```bash
    docker --version
    docker info
    ```

    Make sure your user account has the necessary permissions to run Docker. See the [Docker post-installation guide](https://docs.docker.com/engine/install/linux-postinstall/).

    **2. Install Git**

    Open Terminal and run:

    ```bash
    sudo apt update
    sudo apt install git -y
    ```

    **3. Download IIC-OSIC-TOOLS**

    ```bash
    mkdir -p ~/eda
    cd ~/eda
    ```

    ```bash
    git clone https://github.com/iic-jku/IIC-OSIC-TOOLS.git
    cd IIC-OSIC-TOOLS
    ```

    **4. Create Your Design Folder**

    ```bash
    mkdir -p ~/eda/designs
    ```

    **5. Launch IIC-OSIC-TOOLS**

    ```bash
    ./start_vnc.sh
    ```

    Follow the browser address displayed in Terminal after startup.

### Access the Design Environment

Once IIC-OSIC-TOOLS is running, open the browser address printed by the launch script.

If prompted for a password, the project's default is:

```text
abc123
```

You should now see a Linux desktop environment where you can access the design tools.

---

### Select the SKY130 PDK

For Bulldog Silicon, we'll use the **SkyWater SKY130A Process Design Kit (PDK)**.

Inside the IIC-OSIC-TOOLS Linux desktop, open a terminal.

**1. Check the current PDK**

```bash
echo $PDK
```

If the output is `sky130A`, you're ready to proceed.

If another PDK is selected, enter:

```bash
sak-pdk sky130A
```

**2. Verify the selection**

```bash
echo $PDK
```

Expected output:

```text
sky130A
```

**3. Launch Xschem**

If Xschem is already open, close it first.

From the Linux terminal, enter:

```bash
cd /foss/designs
xschem
```

### Verify Your Installation

Before moving to Lab 0, make sure Xschem can access the SKY130 transistor library.

1. Open Xschem.
2. Create a new schematic.
3. Press `Insert` to open the symbol selector.
4. Locate the SKY130 device library (`sky130_fd_pr`).
5. Find and place the following components:
   - `nfet_01v8.sym` — NMOS transistor
   - `pfet_01v8.sym` — PMOS transistor

---

### Troubleshooting

If you encounter persistent problems during setup, take a screenshot of the error and contact a Bulldog Silicon team lead.

---

## STEP 3: Start Lab 0

Once you've successfully installed the software, launched Xschem, and confirmed access to the SKY130 transistor library, you're ready to begin!

Head over to the [Lab 0 overview](labs/lab0.md) to start designing your first CMOS circuits.