# Lily58 ZMK Configuration

A custom ZMK (Zephyr Mechanical Keyboard) firmware configuration for the Lily58 split keyboard with advanced power management and Bluetooth connectivity.

## Features

- **Split 58-key layout** optimized for ergonomic typing
- **Bluetooth connectivity** with support for up to 5 paired devices
- **Advanced power management** with soft-off mode for extended battery life
- **Three-layer keymap** with dedicated function and symbol layers
- **Custom key bindings** including media controls and navigation

## Quick Start

### Prerequisites

- [ZMK development environment](https://zmk.dev/docs/development/setup) set up
- Compatible Lily58 PCB with wireless controller (nice!nano recommended)

### Building the Firmware

1. Clone this repository:

   ```bash
   git clone <your-repo-url>
   cd lily58-config
   ```

2. Build using ZMK's build system:

   ```bash
   west build -d build/left -b nice_nano_v2 -- -DSHIELD=lily58_left
   west build -d build/right -b nice_nano_v2 -- -DSHIELD=lily58_right
   ```

3. Flash the resulting `.uf2` files to your controllers

### GitHub Actions

This repository includes automated builds via GitHub Actions. Simply push changes to trigger a build, and download the firmware files from the Actions artifacts.

### Automated Keymap Diagrams

This repository uses [keymap-drawer](https://github.com/caksoylar/keymap-drawer) to automatically generate visual keymap diagrams. The diagrams are automatically updated when you make changes to your keymap files.

## Keymap Layout

Visual keymap diagrams are automatically generated and can be found in the `keymap-drawer/` folder after the first workflow run:

- **Base Layer**: `keymap-drawer/lily58_Base.svg`
- **Lower Layer**: `keymap-drawer/lily58_Lower.svg`
- **Raise Layer**: `keymap-drawer/lily58_Raise.svg`

> **Note**: The visual diagrams will be generated automatically when you push changes to your keymap files. If this is your first time setting up the repository, trigger the "Draw ZMK keymaps" workflow manually from the Actions tab to generate the initial diagrams.

## Power Management

### Soft-Off Mode

This configuration includes advanced power management with soft-off functionality:

- **Enter soft-off**: Press `Lower + =` (top-right key on default layer)
- **Wake from soft-off**: Press any key
- **Battery savings**: Soft-off mode provides significant battery life extension compared to deep sleep

### Bluetooth Management

- **Clear all pairings**: `Lower + BTCLR`
- **Select device 1-5**: `Lower + BT1-BT5`
- Supports up to 5 paired devices with easy switching

## Customization

### Modifying the Keymap

Edit `config/lily58.keymap` to customize your layout:

1. **Key positions**: Refer to the generated SVG diagrams for visual reference
2. **Key codes**: Use [ZMK key codes](https://zmk.dev/docs/codes/)
3. **Behaviors**: Add custom behaviors like tap-dance, hold-tap, etc.
4. **Layers**: Add or modify layers as needed

After making changes, the keymap diagrams will be automatically regenerated when you push your changes.

### Keymap Drawing Configuration

Customize the visual appearance of your keymap diagrams by editing `keymap_drawer.config.yaml`:

- **Styling**: Modify SVG styles, colors, and fonts
- **Layout**: Adjust key sizes, spacing, and split gap
- **Layer names**: Ensure proper layer detection
- **Custom legends**: Add special symbols or glyphs

For advanced customization options, see the [keymap-drawer documentation](https://github.com/caksoylar/keymap-drawer).

### Configuration Options

Edit `config/lily58.conf` for firmware settings:

- Sleep timeouts
- Bluetooth settings
- Power management options

## Troubleshooting

### Common Issues

**Keyboard not connecting via Bluetooth:**

- Clear Bluetooth pairings: `Lower + BTCLR`
- Reset the keyboard by pressing the reset button
- Re-pair with your device

**Keys not responding:**

- Check battery levels
- Verify firmware flashed correctly to both halves
- Ensure proper TRRS cable connection

**Power issues:**

- Use soft-off mode (`Lower + =`) for long-term storage
- Check battery connections
- Verify power switch position

## Resources

- [ZMK Documentation](https://zmk.dev/docs/)
- [Lily58 Build Guide](https://docs.splitkb.com/hc/en-us/articles/360010533820)
- [ZMK Discord Community](https://discord.gg/8cfMkQksSB)

## License

This configuration is released under the MIT License. See the original ZMK license headers in the keymap files.
