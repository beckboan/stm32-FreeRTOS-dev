# RTOS Task Creation

A _task_ is nothing but a piece of code that can be scheduled.

Task creation means creating a task in the memory

Task implementation means running the task on the CPU

Typical implementation

```
void ATaskFunction(void *pvParameters) {
	int iVariableExample = 0;
		for (;;)
		{
			// Task code
		}
		// Task must be deleted once broken our of the for loop
		vTaskDelete( NULL )
}
```

**Note**: static variables will be kept in the handler function regardless of what task uses it

## Task Creation

FreeRTOS task API is xTaskCreate

Arguments:

1. Address of task handler
2. Name for task
3. Amount of stack memory allocated to task (in words, not bytes)
4. Pointer of data which needs to be passed to the handler
5. Task priority value
6. Task handle (address of the task created)

A _word_ is the max size of data that can be accessed by the processor in a single clock cycle using a single instruction

Word size could be 8, 16, 32 or more bits. For ARM Cortex Mx, word size is 32 bits.

## Task Priorities

A priority values comes into the picture where there are 2 or more tasks in the system

Priority value helps the scheduler to device which task runs first

Lower the priority value, less the task priority

In freeRTOS, each task an be assigned a priority value from 0 to configMAX_PRIORITIES-1.

You must decide configMAX_PRIORITIES depending on your application. Too many task priority values could lead to RAM's overconsumption.

Good rule of thumb, limit to 5.
