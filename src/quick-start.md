# Quick Start

Before diving into the theory and concepts of how everything works, let's jump straight into action. Use this simple code to turn on the onboard LED of the Pico2.

### Blink LED with Embassy Framework
[Embassy framework](https://github.com/embassy-rs/embassy) is a robust framework for developing asynchronous embedded applications in Rust.

This example code is taken from embassy repo (It also has additional examples): ["https://github.com/embassy-rs/embassy/tree/main/examples/rp/src/bin"](https://github.com/embassy-rs/embassy/tree/main/examples/rp/src/bin)

It creates a blinking effect by toggling the pin's output state between high and low.

## The code snippet
This is only part of the code. You'll need to set up some initial configurations and import the necessary crates.
```rust
#[embassy_executor::main]
async fn main(_spawner: Spawner) {
    let p = embassy_rp::init(Default::default());

    // The onboard LED is actually connected to pin 25
    let mut led = Output::new(p.PIN_25, Level::Low);

    loop {
        led.set_high(); // <- Turn on the LED
        Timer::after_millis(500).await;

        led.set_low(); // <- Turn off the LED
        Timer::after_millis(500).await;
    }
}
```

## Clone the Quick start project
You can clone the quick start project I created and navigate to the project folder and run it.

```sh
git clone https://github.com/ImplFerris/pico2-quick
cd pico2-quick
```

## How to Run?

You refer the ["Running The Program"](../running.md) section
