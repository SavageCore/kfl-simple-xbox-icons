# Kirby and the Forgotten Land: Icon Swap Guide

This guide covers how to visually swap the Nintendo Switch button icons (A/B and X/Y) to match the physical layout of an Xbox controller.

## 1. Extracting the Game Data

1. Open your emulator (**Yuzu** or **Ryujinx**).
2. Right-click **Kirby and the Forgotten Land** in your game list.

#### Yuzu

3. Select **Dump RomFS** > **Dump RomFS**. Choose **Program** as the Dump Target and then **Full** as the Dump Mode.
4. To find the dumped files, click **File** > **Open yuzu folder**, then navigate to `dump/01004D300C5AE000/romfs/lyt/Cmn/BtnIcon/`.

#### Ryujinx

3. Select **Extract Data** > **RomFS** and choose a destination folder.
4. Navigate to `lyt/Cmn/BtnIcon/` inside the folder you selected.

---

5. Copy the `Parts.arc.cmp` file to a safe location to modify.

## 2. Opening the Archive in Switch Toolbox

> **Linux users:** See [Running Switch Toolbox on Linux](SWITCH-TOOLBOX-LINUX.md) for setup instructions using Bottles.

1. Launch **Switch Toolbox**.
2. Go to `File` > `Open` and select the `Parts.arc.cmp` file.
3. In the left-hand tree view, expand the following:

- `Parts.arc.cmp`
- `timg`
- `__Combined.bntx` (Double-click this to open, then you can expand it to see the textures).

## 3. Swapping the Icons

To match an Xbox layout, you must swap the **image data** while keeping the **original Nintendo names** so the game logic remains intact.

### The Swap Logic:

- **A** ↔ **B** (Right ↔ Bottom)
- **X** ↔ **Y** (Top ↔ Left)

### The Steps:

1. **Export Originals**: Right-click each icon (e.g., `BtnIconA^t`, `BtnIconLargeB^t`, etc.) and select **Export**.
2. **Replace**:

- Right-click the **A** entry in Toolbox -> **Replace** -> Select your exported **B** file.
- Right-click the **B** entry in Toolbox -> **Replace** -> Select your exported **A** file.
- Repeat this for **X** and **Y** (and the `BtnIconLarge` variants).

3. **Verify**: Click each entry in the Toolbox and check the **Preview Window**. The name `BtnIconA^t` should now visually show a **B** button.

## 4. Saving and Compressing

1. In Switch Toolbox, go to `File` > `Save`.
2. A compression prompt will appear. **Crucial:** Select **Yes** to use **ZSTD (Kirby)** compression.
3. This will generate the updated `Parts.arc.cmp`.

---

## 5. Mod Deployment

Place your modified file in the following directory structure within your emulator's load/mod folder:

`Simple Xbox Icons/romfs/lyt/Cmn/BtnIcon/Parts.arc.cmp`
