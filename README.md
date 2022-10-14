# STM32F446_SineWave_DAC_ADC_Ex01
Generating of a sinusoidal signal using a DAC, in parallel with ADC conversions, and in the last a UART transfer when triggered..


This project is very similar with the example shown in STM32F103_SineWave_ADC_DMA_Ex03 repository.

Now, i´m using a different board. Here, i´m going to use  the Nucleo F466RE. This board has a DAC, which turn easy the things. 

To create the sinusoidal wave and control the correct time of the ADC conversions i´ve used the Timer 8. Furthermore, i´ve used a look up table where the values of the sine wave were stored.  

The timer 8 counts from 0 to 250. When the counter match 70, the ADC conversion by DMA is triggered. The conversion is done and the result is sent to a buffer called AdcRead[ ]. (Peripheral -> Memory)

When the counter overflows (match 250) the DAC is triggered. At this moment, The next value of look up table is sent from the memory to peripheral DAC.
The buffer where is stored the sine look up table in the memory is called seno[ ]. (Memory -> Peripheral)


The next images shown the configuration done in STMCubeIDE.

1. Clock Configuration
![ClockConfig](https://user-images.githubusercontent.com/114233216/195801958-58fc212a-a3b4-4cc5-b028-97effce09598.png)

2. ADC Configuration

![ADCa](https://user-images.githubusercontent.com/114233216/195802015-166e1378-3209-4bb9-875c-6f92aee94317.png)
![ADCb](https://user-images.githubusercontent.com/114233216/195802036-dee4ddd5-203a-43ba-9a79-bf767abc9568.png)
![ADCc](https://user-images.githubusercontent.com/114233216/195802056-4b2e9c7b-3fe3-4205-aebb-d960eb7ab5ea.png)


3. DAC Configuration

![DACa](https://user-images.githubusercontent.com/114233216/195802096-b0fa852a-898d-43cf-b97a-7566601abc48.png)
![DACb](https://user-images.githubusercontent.com/114233216/195802124-3d6c2115-d829-4153-b0ef-6130a09f39ae.png)
![DACc](https://user-images.githubusercontent.com/114233216/195802142-278612bb-4509-4dc4-86e6-4cd9cfdb50f1.png)


4. TIM8 Configuration

![TIM8a](https://user-images.githubusercontent.com/114233216/195802189-447d06ab-b4df-4b26-af56-e906417793c7.png)
![TIM8b](https://user-images.githubusercontent.com/114233216/195802235-5ccf408c-6e6a-435d-90bf-6ab3cd693ed2.png)

5. UART Configuration

![UARTa](https://user-images.githubusercontent.com/114233216/195802289-624e8dfc-fd7a-48cb-8e33-5f0fb24e6a36.png)


The sinewave created has 255 points. Each point receive a value that range from 0 to 4095. i,e the resolution of DAC is 12 bits.

To calculate the frequency of the signal generated, we can use the following formule:




