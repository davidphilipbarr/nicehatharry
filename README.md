# nicehatharry

A small 'hat' that sits ontop of the nice!nano to support a nice!view

## ZMK (version >= 3.2)

In your zmk-config repo, in `config/west.yml` file:

In `manifest.remotes`

```
    - name: davidphilipbarr
      url-base: https://github.com/davidphilipbarr
```

And then in `manifest.projects`:

```
    - name: nicehatharry
      remote: davidphilipbarr
      clone-depth: 1
      revision: main
````

And finally, in `build.yaml`:

```
    - board: nice_nano_v2
      shield: reviung34 nicehatharry nice_view
```

Place the `nicehatharry` in place of the nice_view_adapter from the nice_view instructions.

 
## ZMK (version < 3.2)
```
nice_view_spi: &spi0 {

    compatible = "nordic,nrf-spim";
    
    mosi-pin = <39>;
    
    sck-pin = <34>;
    
    miso-pin = <2>; // unused on sweep
    
    cs-gpios = <&gpio1 1 GPIO_ACTIVE_HIGH>;

};  
```
### NB

This hat might, in theory, effect the signal strength of the nice!nano, I haven't experiened this, some minor efforts have been made to reduce any effects, but I'm just saying.
