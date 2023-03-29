# nicehatharry

A small 'hat' that sits ontop of the nice!nano to support a nice!view



## ZMK
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
