# Single Left Hand Keyboard

- Based on ZMK firmware
- Layout: 4x3 keys for the fingers; 3 keys for the thumb

## Why

- Inspiration by guitar players playing cords with left hand
- Right hand is free to operate the mouse touch pat or similar
- Both hands can rest on their "familiar" input device and input
  at full speed while you get feedback by spotting the changes on the
  display.

## Layout Considerations

- Each finger operates only one column
- Each column has only rest position (middle) plus one up and one down
  in total 3 for minimal movements
- A key press is either one key or simultaneously two keys at a time.
- Index, middle and ring finger are almost autonomous controllable.
- Pinky is quite often (except for guitar players) somehow linked to
  ring finger
- Thumb

- Combinations
- Ctrl - letter/number/symbol
- Alt - letter/symbol
- Shift - letter
- Ctrl+Shift - letter
- GUI+ Arrow keys
- Ctrl+Alt+Del


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

## Hardware and other Documentation

- [Temper PCB based chord keyboard](docs/temper-shield)

## TODO

- [ ] dev container
- [ ] ci build via chord subfolder
- [ ] Program F keys in NAV_CMD layer - check double meaning GUI plus arrow keys
- [ ] sticky behavior seems not to work across layers or in combos


