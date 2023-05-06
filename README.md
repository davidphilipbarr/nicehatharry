# nicehatharry

A small 'hat' that sits ontop of the nice!nano to support a nice!view

## ZMK (version >= 3.2)
```
&pinctrl {
    spi0_default: spi0_default {
        group1 {
            psels = <NRF_PSEL(SPIM_SCK, 1, 2)>,
                <NRF_PSEL(SPIM_MOSI, 1, 7)>,
                <NRF_PSEL(SPIM_MISO, 0, 19)>; /* GPIO0 19 is not broken on a nice!nano.*/
        };
    };
    spi0_sleep: spi0_sleep {
        group1 {
            psels = <NRF_PSEL(SPIM_SCK, 1, 2)>,
                <NRF_PSEL(SPIM_MOSI, 1, 7)>,
                <NRF_PSEL(SPIM_MISO, 0, 19)>; /* GPIO0 19 is not broken on a nice!nano.*/
            low-power-enable;
        };
    };
};


nice_view_spi: &spi0 {
    compatible = "nordic,nrf-spim";
    pinctrl-0 = <&spi0_default>;
    pinctrl-1 = <&spi0_sleep>;
    pinctrl-names = "default", "sleep";
    cs-gpios = <&gpio1 1 GPIO_ACTIVE_HIGH>;
};

```

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
