# Single Left Hand Keyboard

- Based on ZMK firmware
- Layout: 4x3 keys for the fingers; 3 keys for the thumb


## How to build locally


In the project root directory

```bash
# remove any existing initialization
rm -rf .west

west init -l ./config  # directory where west.yml is located
```
 creates and populates `.west` directory


```bash
west update
```

creates directories and checks out:

- `zephyr` - zephyr sources
- `zmk` - zmk sources
- `modules` - various modules

```bash
west zephyr-export