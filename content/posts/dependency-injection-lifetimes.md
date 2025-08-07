+++
title = 'Dependency injection lifetimes'
date = 2025-08-07T09:13:18+01:00
draft = false
+++

### Context

So I am on my paternity leave and it's driving me nuts. I need to work with code, write, learn, something.

Everywhere I keep reading that you need to master the basics. It's the same in Jiu Jitsu. Master the basics and you get a very long way.

I am by no means any where near master of any basics, so why not just start with different subjects. Randomly. But subjects I find interesting. And by coinsidence I stumpled across Dependency Injection (DI) lifetimes and thought to my self, why not study it? And not just read about it?
Not just read about it, but try - when possible - to demo it and then hopefully understand it better. Because the concept is quite easy to understand - even for me, but being able to demo it via code, I believe brings the understanding further. So here we go.

### Singleton, Trancient, Scoped

What are they and what is the difference between them?

In .NET when we dependency inject services, we need to decide the lifetime of it. 

Do we create a new instance for each HTTP request, do we create a new instance for each object created in the HTTP request or is there only one service instance throughout the entire lifetime?

That's basically how the 3 dependency injection lifetimes are used.

As mentioned - instead of just explaining it in text, it sometimes makes better sense to demo the difference using code, so I've created an experimental console application in Visual Studio to try and visualize the differences between the 3 lifetimes.

In my `Program.cs`, I set up a simple console app using the built-in .NET Generic Host. Here’s what happens:

```cs
using Experiment;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;

using IHost host = Host.CreateDefaultBuilder(args)
    .ConfigureServices(services =>
    {
        services.AddSingleton<ISingletonService, SingletonService>();
        services.AddTransient<ITransientService, TransientService>();
        services.AddScoped<IScopedService, ScopedService>();
    }).Build();

TestLifetimes("Scope 1");
TestLifetimes("Scope 2");

void TestLifetimes(string scopeName)
{
    Console.WriteLine($"\n--- {scopeName} ---");

    using var scope = host.Services.CreateScope();
    var services = scope.ServiceProvider;

    var singleton = services.GetRequiredService<ISingletonService>();
    var transient1 = services.GetRequiredService<ITransientService>();
    var transient2 = services.GetRequiredService<ITransientService>();
    var scoped1 = services.GetRequiredService<IScopedService>();
    var scoped2 = services.GetRequiredService<IScopedService>();

    singleton.Run();
    transient1.Run();
    transient2.Run();
    scoped1.Run();
    scoped2.Run();
}
```

What this does:
The host builds the service container with 3 services registered:

SingletonService as singleton

TransientService as transient

ScopedService as scoped

Then, it calls TestLifetimes twice — simulating two separate scopes (think of scopes like “requests” or units of work).

Inside TestLifetimes:

A new scope is created using CreateScope().

The services are resolved from the scope’s ServiceProvider.

Each service’s Run() method logs its own unique Guid.

Let's look at the service implementation. They are basically all the same, just different class names:


```cs
internal class SingletonService : ISingletonService
{
    readonly ILogger _logger;
    readonly Guid _id = Guid.NewGuid();

    public SingletonService(ILogger<SingletonService> logger)
    {
        _logger = logger;
    }

    public void Run()
    {
        _logger.LogInformation("Singleton " + "GUID: " + _id);
    }
}
```

The interface contains a simple Run() method:

```cs
namespace Experiment
{
    internal interface ISingletonService
    {
        void Run();
    }
}
```

### So what do they do?


Each service creates a new Guid when constructed.

Because of DI lifetimes:

The SingletonService instance is created once for the entire app — so the _id stays the same forever.

The TransientService gets a new instance every time it’s requested, so every GetRequiredService<ITransientService>() call returns a new GUID.

The ScopedService gets a new instance once per scope, so within a scope, repeated requests get the same _id, but different scopes get different ones.

The output:

![](/images/dependency-injection-lifetime-output.png)

Or in text:

```
--- Scope 1 ---
info: Experiment.SingletonService[0]
      Singleton GUID: f48df15a-8eeb-438e-b8b9-2034ab693591
info: Experiment.TransientService[0]
      Transient GUID: e988b94f-2e16-41e4-9705-522567e81ed4
info: Experiment.TransientService[0]
      Transient GUID: 912c8533-54c1-4fba-82da-7a8018f4e264
info: Experiment.ScopedService[0]
      Scoped GUID: 6409c5c6-182d-487d-8870-68f715d72258
info: Experiment.ScopedService[0]
      Scoped GUID: 6409c5c6-182d-487d-8870-68f715d72258

--- Scope 2 ---
info: Experiment.SingletonService[0]
      Singleton GUID: f48df15a-8eeb-438e-b8b9-2034ab693591
info: Experiment.TransientService[0]
      Transient GUID: 21f2eca8-c387-4997-89a2-97d97eebd72f
info: Experiment.TransientService[0]
      Transient GUID: 4d0632dd-f7ca-48a1-a176-7d7af509da65
info: Experiment.ScopedService[0]
      Scoped GUID: 0df87ed6-e37f-4e3d-992f-d99e0451256f
info: Experiment.ScopedService[0]
      Scoped GUID: 0df87ed6-e37f-4e3d-992f-d99e0451256f
```

What we see is that the singleton has the same GUID across scopes. The transient creates a new GUID for each time while the scoped has the same GUID within the scope, but has a new GUID when a new scope is created.

That's it. Very simple way to demonstrate the differences.

