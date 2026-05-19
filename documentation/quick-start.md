# Quick Start for Cyverse

## Step 1: Launch the CyVerse analysis

Use the direct launch link for this workshop. It opens the correct CyVerse app,
so you do not need to search for the application manually.

https://de.cyverse.org/instantlaunch/75a5a13e-7980-11f0-b7e6-008cfa5ae621

If CyVerse asks you to sign in, log in with your CyVerse account and continue
with the launch.

### On the launch page:

1. Confirm that the app is the ESIIL OASIS training environment.
2. Ensure the container image **Version** is `Innovation_Summit_2026`.
3. Name the analysis, decide where you want it saved, and complete the remaining
   analysis information fields.
4. In **Advanced Settings**, select **4** or **8 CPU Cores**. Start with **4**,
   but if you run out of memory, select **8** in the future. Add **32 GiB
   Memory**
5. Click **Launch Analysis**, **Run**, or the final launch button shown by
   CyVerse.

"If the direct launch link is not working" Use the longer CyVerse navigation
path:

    1. Log in to CyVerse at [https://user.cyverse.org](https://user.cyverse.org).
    2. Click **Discovery Environment**.
    3. Launch the Discovery Environment.
    4. Under **Featured Apps**, launch the app **ESIIL_OASIS**.
    5. Ensure the **Version** is `Innovation_Summit_2026`.
    6. Name the analysis, decide where you want it saved, and complete the analysis information fields.
    7. In **Advanced Settings**, select **4** or **8 CPU Cores**. Start with **4**, but if you run out of memory, select **8** in the future.
    8. Click **Launch Analysis**.

## Step 2: Open the interactive session

When the analysis is ready, open the interactive workspace.

1. Go to your running analyses or notifications.
2. Find the analysis you just launched.
3. Click **Go to Analysis**, **Open**, **Launch**, **Access**, or the link
   provided by CyVerse.
4. For the `ESIIL_OASIS` app, launch **VS Code** from the analysis interface.
5. The session will open as a browser-based coding environment.

For this lesson, the most important tool is the terminal. In VS Code, open a
terminal with **Terminal -> New Terminal**. In JupyterLab, open a terminal with
**File -> New -> Terminal**, or by clicking the terminal icon in the launcher.

After VS Code opens, use **File -> Open Folder** and navigate to:

```text
/home/jovyan/work/
```

This is the working folder used in the current training image.

![Screenshot showing the VS Code launcher inside the CyVerse workspace.](assets/images/cyverse/cyverse-06-open-jupyterlab.png)

_Opening the interactive VS Code workspace._

![Screenshot showing the New Terminal menu item inside VS Code.](assets/images/cyverse/cyverse-07-terminal.png)

_Opening a terminal inside the CyVerse workspace._
