<img src="text.png" alt="COOLTEXT" width="850" height="150"> 
<h2>Por: Joshua Benitez Peraza</h2>
<h1>PIR Motion Sensor</h1>
<p1>
Los sensores PIR permiten detectar movimiento, casi siempre se usan para detectar si un alguien se ha movido dentro o fuera del alcance de los sensores. Son pequeños, económicos, de bajo consumo, fáciles de usar y no se desgastan. Por esa razón, se encuentran comúnmente en electrodomésticos y aparatos que se usan en los hogares o negocios. A menudo se los conoce como sensores PIR, "infrarrojos pasivos", "piroeléctricos" o "de movimiento IR".

Los PIR están hechos básicamente de un  sensor piroeléctrico, que puede detectar niveles de radiación infrarroja. Todo emite algo de radiación de bajo nivel, y cuanto más caliente está algo, más radiación se emite. El sensor en un detector de movimiento en realidad está dividido en dos mitades. La razón de esto es que buscamos detectar movimiento (cambio), no niveles de IR promedio. Las dos mitades están cableadas de manera que se anulan entre sí. Si una mitad ve más o menos radiación IR que la otra, la salida oscilará hacia arriba o hacia abajo.
</p1>  

<img src="Motion.jpg" alt="Motion" width="500" height="600">

|  Especificaciones |   |
|---|---|
| Operating temperature range  | -40 C to 70 C  |
|  Field of View |  theta1=theta2=45deg |
| Electrode  | (2.0x1.0mm)x2  |
| Responsivity(typ.)  | 4.6mV  |
| Optical Filter  |  5micro meter Long Pass  |
|  Supply Voltage Range  | 2V TO 15 V  |
| Storage Temperature Range  | -40 C to 85 C  |

## LINK DEL WORKI
https://wokwi.com/projects/349002300756329042

<h2>GIF</h2>
<img src="gift.gif" alt="GIFT" width="500" height="600">


<h2>CODIGO</h2>

    ### Joshua Benitez Peraza
    ### El codigo siguiente permite hacer uso del sensor PIR, el cual encendera el led al recibir una señal.
    
    import board
    import digitalio

    LED_PIN = board.GP28  # Pin number for the board's built in LED.
    PIR_PIN = board.GP16   # Pin number connected to PIR sensor output wire.

    # Setup digital input for PIR sensor:
    pir = digitalio.DigitalInOut(PIR_PIN)
    pir.direction = digitalio.Direction.INPUT

    # Setup digital output for LED:
    led = digitalio.DigitalInOut(LED_PIN)
    led.direction = digitalio.Direction.OUTPUT

    # Main loop that will run forever:
    old_value = pir.value
    while True:
        pir_value = pir.value
        if pir_value:
            # PIR is detecting movement! Turn on LED.
            led.value = True
            # Check if this is the first time movement was
            # detected and print a message!
            if not old_value:
                print('Motion detected!')
        else:
            # PIR is not detecting movement. Turn off LED.
            led.value = False
            # Again check if this is the first time movement
            # stopped and print a message.
         if old_value:
                print('Motion ended!')
        old_value = pir_value
