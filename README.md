# STM32-DMA-Multichannel-ADC
This is a simple code you can use to implement Multichannel ADC using DMA on an STM32 Microcontroller. The full tutorial video is available on YouTube:

    /* USER CODE BEGIN Includes */
    #include <stdio.h>
    #include "string.h"
    /* USER CODE END Includes */
    
    
    /* USER CODE BEGIN PV */
    uint16_t pot1;
    uint16_t pot2;
    uint32_t readValue[2];
    char buffer[50];
    /* USER CODE END PV */
    
    
    /* USER CODE BEGIN 2 */
     HAL_ADC_Start_DMA(&hadc1,(uint32_t*) readValue, 2);
    /* USER CODE END 2 */
    
    
    /* USER CODE BEGIN 3 */
    	  for (uint8_t i =0; i<hadc1.Init.NbrOfConversion; i++){
    		  pot1 = (uint16_t) readValue[0];
    		  pot2 = (uint16_t) readValue[1];
    		  }
    	  snprintf(buffer, sizeof(buffer), "Pot1: %d, Pot2: %d\r\n", pot1, pot2);
    	  HAL_UART_Transmit(&huart2, (uint8_t*)buffer, strlen(buffer), HAL_MAX_DELAY);
    	  HAL_Delay(500);
    
     }
    /* USER CODE END 3 */
