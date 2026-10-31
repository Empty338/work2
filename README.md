# 电控组第二次培训作业
- **洪健毅**
- ***_**20263007306**_***

## 流水灯实现思路
本项目基于STM32F103C8T6 HAL库开发，使用`HAL_Delay()`阻塞延时实现流水灯效果。
程序在while(1)死循环内依次控制LED0、LED1、LED2的GPIO电平，每次只点亮一盏灯，其余两盏熄灭，延时500ms后切换下一盏，循环往复，实现LED0→LED1→LED2轮流点亮的流水效果。

### 核心代码片段
```c
while (1)
{
  // LED0亮，LED1、LED2灭
  HAL_GPIO_WritePin(LED0_GPIO_Port, LED0_Pin, GPIO_PIN_RESET);
  HAL_GPIO_WritePin(LED1_GPIO_Port, LED1_Pin, GPIO_PIN_SET);
  HAL_GPIO_WritePin(LED2_GPIO_Port, LED2_Pin, GPIO_PIN_SET);
  HAL_Delay(500);

  // LED1亮，LED0、LED2灭
  HAL_GPIO_WritePin(LED0_GPIO_Port, LED0_Pin, GPIO_PIN_SET);
  HAL_GPIO_WritePin(LED1_GPIO_Port, LED1_Pin, GPIO_PIN_RESET);
  HAL_GPIO_WritePin(LED2_GPIO_Port, LED2_Pin, GPIO_PIN_SET);
  HAL_Delay(500);

  // LED2亮，LED0、LED1灭
  HAL_GPIO_WritePin(LED0_GPIO_Port, LED0_Pin, GPIO_PIN_SET);
  HAL_GPIO_WritePin(LED1_GPIO_Port, LED1_Pin, GPIO_PIN_SET);
  HAL_GPIO_WritePin(LED2_GPIO_Port, LED2_Pin, GPIO_PIN_RESET);
  HAL_Delay(500);
}
