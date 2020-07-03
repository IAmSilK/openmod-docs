# Services and Dependency Injection

##Introduction

OpenMod, like other modern .NET projects, uses the dependency injection pattern. This guide aims to simplify it and explain what it means for plugin developers using OpenMod.

## What does Dependency Injection mean for me?

In short, you do not have to create public static instances of any of your classes.

Plugins, commands, event listeners and services can automatically get references to any other services provided by OpenMod or plugins just by adding their interfaces to the constructor.  

## Registering your own Services
You can register your own services by implementing the `IServiceConfigurator` or `IContainerConfigurator` interfaces in any class.

## List of services

| **Service**                                     |
|-------------------------------------------------|
| ICommandExecutor                                |
| ICommandStore                                   |
| ICommandPermissionBuilder                       |
| ICurrentCommandContextAccessor                  |
| IOpenModStringLocaliser                         | 
| IDataStoreFactory                               | 
| IOpenModDataStoreAccessor                       | 
| IEventBus                                       | 
| IOpenModHost                                    | 
| IPermissionChecker                              | 
| IPermissionRolesDataStore                       |    
| IUserDataSeeder                                 | 
| IUserDataStore                                  | 
| IUserManager                                    | 
| IRuntime                                        | 


## Dependency Injection Example

Assume you want to access your plugin's instance and configuration from a command. Here is how you could do it:

```c#
//This is now accessible from the execute method
private IConfiguration m_Configuration;

public AnnounceCommand(IServiceProvider serviceProvider, IConfiguration configuration) : base(serviceProvider)
{
    m_Configuration = configuration;
}
```

## Further reading
****
For more, read the [Dependency injection page on docs.microsoft.com](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection).