# Azure RTOS ThreadX

This advanced real-time operating system (RTOS) is designed specifically for deeply embedded applications. Among the multiple benefits it provides are advanced scheduling facilities, message passing, interrupt management, and messaging services. Azure RTOS ThreadX has many advanced features, including picokernel architecture, preemption threshold, event chaining, and a rich set of system services.

## Documentation

All Azure RTOS products can be found at: https://github.com/azure-rtos

Azure RTOS ThreadX can be found at: https://github.com/azure-rtos/threadx

Documentation for this library can be found at: http://docs.microsoft.com/azure/rtos/threadx

## Understanding inter-component dependencies

The main components of Azure RTOS are each provided in their own repository, but there are dependencies between them--shown in the following graph--that are important to understand when setting up your builds.

![dependency graph](docs/deps.png)

## Security

Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms. It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.

## Contribution, feedback and issues

If you encounter any bugs, have suggestions for new features or if you would like to become an active contributor to this project please follow the instructions provided in the contribution guideline for the corresponding repo.

For general support, please post a question to [Stack Overflow](http://stackoverflow.com/questions/tagged/azure-rtos+threadx) using the `threadx` and `azure-rtos` tags.