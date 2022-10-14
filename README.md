# STM32F446_SineWave_DAC_ADC_Ex01
Generating of a sinusoidal signal using a DAC, in parallel with ADC conversions, and in the last a UART transfer when triggered..


This project is very similar with the example shown in STM32F103_SineWave_ADC_DMA_Ex03 repository.

Now, i´m using a different board. Here, i´m going to use  the Nucleo F466RE. This board has a DAC, which turn easy the things. 

To create the sinusoidal wave and control the correct time of the ADC conversions i´ve used the Timer 8. Furthermore, i´ve used a look up table where the values of the sine wave were stored.  

The timer 8 counts from 0 to 250. When the counter match 70, the ADC conversion by DMA is triggered. The conversion is done and the result is sent to a buffer called AdcRead[ ]. (Peripheral -> Memory)

When the counter overflows (match 250) the DAC is triggered. At this moment, The next value of look up table is sent from the memory to peripheral DAC.
The buffer where is stored the sine look up table in the memory is called seno[ ]. (Memory -> Peripheral)
