---
title: Eklentilerle .NET Core uygulaması oluşturma
description: Eklentileri destekleyen bir .NET Core uygulaması oluşturmayı öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: 5267a56d0742d8e1cae4a81c058bc4ee05e83b4e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579499"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="e5e9d-103">Eklentilerle .NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5e9d-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="e5e9d-104">Bu öğreticide, eklentileri yüklemek için özel bir <xref:System.Runtime.Loader.AssemblyLoadContext> nasıl oluşturacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-104">This tutorial shows you how to create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load plugins.</span></span> <span data-ttu-id="e5e9d-105">@No__t_0, eklentinin bağımlılıklarını çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> is used to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="e5e9d-106">Öğretici, eklentinin bağımlılıklarını barındırma uygulamasından doğru şekilde yalıtır.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-106">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span> <span data-ttu-id="e5e9d-107">Şunları yapmayı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-107">You'll learn how to:</span></span>

- <span data-ttu-id="e5e9d-108">Eklentileri desteklemek için bir proje yapısı yapın.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-108">Structure a project to support plugins.</span></span>
- <span data-ttu-id="e5e9d-109">Her eklentiyi yüklemek için özel bir <xref:System.Runtime.Loader.AssemblyLoadContext> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-109">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="e5e9d-110">Eklentilerin bağımlılıklara sahip olmasını sağlamak için <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-110">Use the <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="e5e9d-111">Yalnızca derleme yapıtları kopyalanarak kolayca dağıtılabilecek olan eklentileri yazar.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-111">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5e9d-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="e5e9d-112">Prerequisites</span></span>

- <span data-ttu-id="e5e9d-113">[.NET Core 3,0 SDK](https://dotnet.microsoft.com/download) veya daha yeni bir sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-113">Install the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="e5e9d-114">Uygulamayı oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5e9d-114">Create the application</span></span>

<span data-ttu-id="e5e9d-115">İlk adım, uygulamayı oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-115">The first step is to create the application:</span></span>

1. <span data-ttu-id="e5e9d-116">Yeni bir klasör oluşturun ve bu klasörde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-116">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="e5e9d-117">Projeyi daha kolay hale getirmek için aynı klasörde bir Visual Studio çözüm dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-117">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="e5e9d-118">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-118">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="e5e9d-119">Uygulama projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-119">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="e5e9d-120">Şimdi uygulamamızın iskektlerini dolduracağız.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-120">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="e5e9d-121">*Appwithplugin/program. cs* dosyasındaki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-121">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

```csharp
using PluginBase;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Reflection;

namespace AppWithPlugin
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                if (args.Length == 1 && args[0] == "/d")
                {
                    Console.WriteLine("Waiting for any key...");
                    Console.ReadLine();
                }

                // Load commands from plugins.

                if (args.Length == 0)
                {
                    Console.WriteLine("Commands: ");
                    // Output the loaded commands.
                }
                else
                {
                    foreach (string commandName in args)
                    {
                        Console.WriteLine($"-- {commandName} --");

                        // Execute the command with the name passed as an argument.

                        Console.WriteLine();
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex);
            }
        }
    }
}

```

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="e5e9d-122">Eklenti arabirimlerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5e9d-122">Create the plugin interfaces</span></span>

<span data-ttu-id="e5e9d-123">Eklentilerle uygulama oluşturmanın bir sonraki adımı, eklentilerin uygulanması gereken arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-123">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="e5e9d-124">Uygulamanız ve eklentiler arasında iletişim kurmak için kullanmayı planladığınız türleri içeren bir sınıf kitaplığı almanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-124">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="e5e9d-125">Bu bölüm, tam uygulamanızı teslim etmek zorunda kalmadan eklenti arabiriminizi bir paket olarak yayımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-125">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="e5e9d-126">Projenin kök klasöründe `dotnet new classlib -o PluginBase` ' ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-126">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="e5e9d-127">Ayrıca, projeyi çözüm dosyasına eklemek için `dotnet sln add PluginBase/PluginBase.csproj` ' ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-127">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="e5e9d-128">@No__t_0 dosyasını silin ve aşağıdaki arabirim tanımıyla `ICommand.cs` adlı `PluginBase` klasörde yeni bir dosya oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-128">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="e5e9d-129">Bu `ICommand` arabirimi, tüm eklentilerin uygulayamayacağı arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-129">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="e5e9d-130">@No__t_0 arabirimi tanımlandığına göre, uygulama projesi biraz daha fazla doldurulabilir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-130">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="e5e9d-131">Kök klasördeki `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` komutuyla `AppWithPlugin` projesinden `PluginBase` projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-131">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="e5e9d-132">@No__t_0 açıklamasını, belirtilen dosya yollarından eklentileri yüklemesini etkinleştirmek için aşağıdaki kod parçacığı ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-132">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

```csharp
string[] pluginPaths = new string[]
{
    // Paths to plugins to load.
};

IEnumerable<ICommand> commands = pluginPaths.SelectMany(pluginPath =>
{
    Assembly pluginAssembly = LoadPlugin(pluginPath);
    return CreateCommands(pluginAssembly);
}).ToList();
```

<span data-ttu-id="e5e9d-133">Sonra `// Output the loaded commands` yorumunu aşağıdaki kod parçacığı ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-133">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="e5e9d-134">@No__t_0 açıklamasını aşağıdaki kod parçacığıyla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-134">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="e5e9d-135">Son olarak, burada gösterildiği gibi, `LoadPlugin` ve `CreateCommands` adlı `Program` sınıfına statik yöntemler ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-135">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    throw new NotImplementedException();
}

static IEnumerable<ICommand> CreateCommands(Assembly assembly)
{
    int count = 0;

    foreach (Type type in assembly.GetTypes())
    {
        if (typeof(ICommand).IsAssignableFrom(type))
        {
            ICommand result = Activator.CreateInstance(type) as ICommand;
            if (result != null)
            {
                count++;
                yield return result;
            }
        }
    }

    if (count == 0)
    {
        string availableTypes = string.Join(",", assembly.GetTypes().Select(t => t.FullName));
        throw new ApplicationException(
            $"Can't find any type which implements ICommand in {assembly} from {assembly.Location}.\n" +
            $"Available types: {availableTypes}");
    }
}
```

## <a name="load-plugins"></a><span data-ttu-id="e5e9d-136">Eklentileri yükle</span><span class="sxs-lookup"><span data-stu-id="e5e9d-136">Load plugins</span></span>

<span data-ttu-id="e5e9d-137">Artık uygulama yüklenen eklenti derlemelerinden komutları doğru bir şekilde yükleyebilir ve örneklendirilecek, ancak hala eklenti derlemelerini yükleyemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-137">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it's still unable to load the plugin assemblies.</span></span> <span data-ttu-id="e5e9d-138">*Appwithplugin* klasöründe aşağıdaki içeriğe sahip *PluginLoadContext.cs* adlı bir dosya oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-138">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="e5e9d-139">@No__t_0 türü <xref:System.Runtime.Loader.AssemblyLoadContext> türetilir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-139">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="e5e9d-140">@No__t_0 türü, geliştiricilerin, derleme sürümlerinin çakışmadığından emin olmak için yüklü derlemeleri farklı gruplara yalıtmalarına olanak tanıyan özel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-140">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions don't conflict.</span></span> <span data-ttu-id="e5e9d-141">Ayrıca, özel bir `AssemblyLoadContext` ' dan derlemeleri yüklemek için farklı yollar seçebilir ve varsayılan davranışı geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-141">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="e5e9d-142">@No__t_0, derleme adlarını yollara çözümlemek için .NET Core 3,0 ' de tanıtılan `AssemblyDependencyResolver` türünün bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-142">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="e5e9d-143">@No__t_0 nesnesi, .NET sınıf kitaplığı yoluyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-143">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="e5e9d-144">Yol `AssemblyDependencyResolver` oluşturucusuna geçilen sınıf kitaplığı için *. Deps. JSON* dosyasını temel alan derlemeleri ve yerel kitaplıkları göreli yollarına çözümler.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-144">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="e5e9d-145">Özel `AssemblyLoadContext`, eklentilerin kendi bağımlılıklarına sahip olmasını sağlar ve `AssemblyDependencyResolver` bağımlılıkları doğru şekilde yüklemeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-145">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="e5e9d-146">Artık `AppWithPlugin` projesi `PluginLoadContext` türüne sahip olduğuna göre `Program.LoadPlugin` yöntemini aşağıdaki gövdele güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-146">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    // Navigate up to the solution root
    string root = Path.GetFullPath(Path.Combine(
        Path.GetDirectoryName(
            Path.GetDirectoryName(
                Path.GetDirectoryName(
                    Path.GetDirectoryName(
                        Path.GetDirectoryName(typeof(Program).Assembly.Location)))))));

    string pluginLocation = Path.GetFullPath(Path.Combine(root, relativePath.Replace('\\', Path.DirectorySeparatorChar)));
    Console.WriteLine($"Loading commands from: {pluginLocation}");
    PluginLoadContext loadContext = new PluginLoadContext(pluginLocation);
    return loadContext.LoadFromAssemblyName(new AssemblyName(Path.GetFileNameWithoutExtension(pluginLocation)));
}
```

<span data-ttu-id="e5e9d-147">Her eklenti için farklı bir `PluginLoadContext` örneği kullanarak, Eklentiler, sorun olmadan farklı veya hatta çakışan bağımlılıklara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-147">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="simple-plugin-with-no-dependencies"></a><span data-ttu-id="e5e9d-148">Bağımlılıkları olmayan basit eklenti</span><span class="sxs-lookup"><span data-stu-id="e5e9d-148">Simple plugin with no dependencies</span></span>

<span data-ttu-id="e5e9d-149">Kök klasöre geri döndüğünüzde şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-149">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="e5e9d-150">@No__t_0 adlı yeni bir sınıf kitaplığı projesi oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-150">Run the following command to create a new class library project named `HelloPlugin`:</span></span>
    
    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="e5e9d-151">Projeyi `AppWithPlugin` çözümüne eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-151">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="e5e9d-152">*Merhaba Plugin/Class1. cs* dosyasını aşağıdaki içeriklerle *HelloCommand.cs* adlı bir dosyayla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-152">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="e5e9d-153">Şimdi, *Helloplugin. csproj* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-153">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="e5e9d-154">Şuna benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-154">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="e5e9d-155">@No__t_0 etiketleri arasında, aşağıdaki öğeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-155">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

<span data-ttu-id="e5e9d-156">@No__t_0 öğesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-156">The `<Private>false</Private>` element is important.</span></span> <span data-ttu-id="e5e9d-157">Bu, MSBuild 'in *Pluginbase. dll dosyasını* helloplugin çıkış dizinine kopyalamamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-157">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="e5e9d-158">Eğer *Pluginbase. dll* derlemesi çıkış dizininde mevcutsa, `PluginLoadContext` derlemeyi bulur ve *helloplugin. dll* derlemesini yüklediğinde yükler.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-158">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="e5e9d-159">Bu noktada `HelloPlugin.HelloCommand` türü, varsayılan yükleme bağlamına yüklenen `ICommand` arabirimine değil, `HelloPlugin` projesinin çıkış dizinindeki *Pluginbase. dll* ' den `ICommand` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-159">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="e5e9d-160">Çalışma zamanı bu iki türü farklı derlemelerden farklı türler olarak gördüğü için `AppWithPlugin.Program.CreateCommands` yöntemi komutları bulamaz.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-160">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method won't find the commands.</span></span> <span data-ttu-id="e5e9d-161">Sonuç olarak, eklenti arabirimlerini içeren derlemeye başvuru için `<Private>false</Private>` meta verisi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-161">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="e5e9d-162">@No__t_0 proje tamamlandığına göre, `HelloPlugin` eklentisinin nerede bulunabileceğinizi bildirmek için `AppWithPlugin` projesini güncelleştirmemiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-162">Now that the `HelloPlugin` project is complete, we should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="e5e9d-163">@No__t_0 açıklamasıyla sonra, `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` `pluginPaths` dizisinin bir öğesi olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-163">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="plugin-with-library-dependencies"></a><span data-ttu-id="e5e9d-164">Kitaplık bağımlılıkları olan eklenti</span><span class="sxs-lookup"><span data-stu-id="e5e9d-164">Plugin with library dependencies</span></span>

<span data-ttu-id="e5e9d-165">Neredeyse tüm eklentiler basit bir "Merhaba Dünya" öğesinden daha karmaşıktır ve birçok eklenti diğer kitaplıklara bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-165">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="e5e9d-166">Örnekteki `JsonPlugin` ve `OldJson` eklenti projeleri, `Newtonsoft.Json` ' de NuGet paketi bağımlılıkları olan eklentilerin iki örneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-166">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="e5e9d-167">Proje dosyaları, proje başvuruları için özel bilgilere sahip değildir ve (`pluginPaths` dizisine eklenti yolları eklendikten sonra), Eklentiler, AppWithPlugin uygulamasının yürütülmesi halinde çalıştırılsa bile kusursuz bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-167">The project files themselves don't have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="e5e9d-168">Ancak, bu projeler başvurulan derlemeleri çıkış dizinine kopyalamadıkları için, eklentilerin çalışması için kullanıcının makinesinde derlemelerin mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-168">However, these projects don't copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="e5e9d-169">Bu sorunu geçici olarak çözmek için iki yol vardır.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-169">There are two ways to work around this problem.</span></span> <span data-ttu-id="e5e9d-170">İlk seçenek, sınıf kitaplığını yayımlamak için `dotnet publish` komutunu kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-170">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="e5e9d-171">Alternatif olarak, eklenti için `dotnet build` çıktısını kullanmak istiyorsanız, eklentinin proje dosyasındaki `<PropertyGroup>` etiketleri arasına `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` özelliğini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-171">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="e5e9d-172">Örnek için `XcopyablePlugin` eklenti projesine bakın.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-172">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-examples-in-the-sample"></a><span data-ttu-id="e5e9d-173">Örnekteki diğer örnekler</span><span class="sxs-lookup"><span data-stu-id="e5e9d-173">Other examples in the sample</span></span>

<span data-ttu-id="e5e9d-174">Bu öğreticinin tüm kaynak kodu [DotNet/Samples deposunda](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-174">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="e5e9d-175">Tamamlanan örnek, `AssemblyDependencyResolver` davranışından oluşan diğer örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-175">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="e5e9d-176">Örneğin, `AssemblyDependencyResolver` nesnesi yerel kitaplıkları ve NuGet paketlerine dahil edilen yerelleştirilmiş uydu derlemelerini de çözümleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-176">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="e5e9d-177">Örnek deposundaki `UVPlugin` ve `FrenchPlugin` bu senaryoları gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-177">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="reference-a-plugin-from-a-nuget-package"></a><span data-ttu-id="e5e9d-178">NuGet paketinden bir eklentiye başvur</span><span class="sxs-lookup"><span data-stu-id="e5e9d-178">Reference a plugin from a NuGet package</span></span>

<span data-ttu-id="e5e9d-179">@No__t_0 adlı NuGet paketinde tanımlanmış bir eklenti arabirimine sahip bir uygulama olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-179">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="e5e9d-180">Eklenti projenizde pakete doğru şekilde nasıl başvurdunuz?</span><span class="sxs-lookup"><span data-stu-id="e5e9d-180">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="e5e9d-181">Proje başvuruları için proje dosyasındaki `ProjectReference` öğesindeki `<Private>false</Private>` meta verisinin kullanılması dll 'nin çıkışa kopyalanmasını engelledi.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-181">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="e5e9d-182">@No__t_0 paketine doğru bir şekilde başvurmak için, proje dosyasındaki `<PackageReference>` öğesini şu şekilde değiştirmek istersiniz:</span><span class="sxs-lookup"><span data-stu-id="e5e9d-182">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="e5e9d-183">Bu, `A.PluginBase` derlemelerinin, eklentinin çıkış dizinine kopyalanmasını önler ve bu eklentinin `A.PluginBase` ' in bir sürümünü kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-183">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="e5e9d-184">Eklenti hedef Framework önerileri</span><span class="sxs-lookup"><span data-stu-id="e5e9d-184">Plugin target framework recommendations</span></span>

<span data-ttu-id="e5e9d-185">Eklenti bağımlılık yüklemesi *. Deps. JSON* dosyasını kullandığından, eklentinin hedef çerçevesiyle ilgili bir Gotcha vardır.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-185">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="e5e9d-186">Özellikle, eklentilerinizin bir .NET Standard sürümü yerine .NET Core 3,0 gibi bir çalışma zamanını hedeflemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-186">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="e5e9d-187">*. Deps. JSON* dosyası, projenin hedeflediği çerçeveye göre oluşturulur ve birçok .NET Standard uyumlu paket, belirli çalışma zamanları için .NET Standard ve uygulama derlemelerinin oluşturulmasına yönelik başvuru derlemeleri sunduğundan, *. Deps. JSON* uygulama derlemelerini doğru görmeyebilir veya Istediğiniz .NET Core sürümü yerine bir derlemenin .NET Standard sürümünü alabilir.</span><span class="sxs-lookup"><span data-stu-id="e5e9d-187">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>
