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
```

And now the build

```bash
rm -rf build
mkdir build
west build -s zmk/app -b nice_nano_v2 -d build --  \
   -DZMK_CONFIG="$(pwd)/config" \
   -DZMK_EXTRA_MODULES="$(pwd)/chord" \
   -DSHIELD="chord_temper"
```

The alternative shield with direct wiring is `direct15`

## Hardware and other documentTion

- [Temper PCB based chord keyboard](docs/temper-shield)

## TODO

- [ ] dev container
- [ ] ci build via chord subfolder
- [ ] measurement i2c of temper


