---
title: Eklentilerle .NET Core uygulaması oluşturma
description: Eklentileri destekleyen bir .NET Core uygulaması oluşturmayı öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: e8b02d9b2175b4663e665db1a5a40a9bf3c44d10
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216249"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="953dc-103">Eklentilerle .NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="953dc-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="953dc-104">Bu öğreticide nasıl yapılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="953dc-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="953dc-105">Eklentileri desteklemek için bir proje yapısı yapın.</span><span class="sxs-lookup"><span data-stu-id="953dc-105">Structure a project to support plugins.</span></span>
- <span data-ttu-id="953dc-106">Her bir eklentiyi <xref:System.Runtime.Loader.AssemblyLoadContext> yüklemek için özel oluşturun.</span><span class="sxs-lookup"><span data-stu-id="953dc-106">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="953dc-107">Eklentilerin bağımlılıklara sahip olmasını sağlamak için türükullanın.`System.Runtime.Loader.AssemblyDependencyResolver`</span><span class="sxs-lookup"><span data-stu-id="953dc-107">Use the `System.Runtime.Loader.AssemblyDependencyResolver` type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="953dc-108">Yalnızca derleme yapıtları kopyalanarak kolayca dağıtılabilecek olan eklentileri yazar.</span><span class="sxs-lookup"><span data-stu-id="953dc-108">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="953dc-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="953dc-109">Prerequisites</span></span>

- <span data-ttu-id="953dc-110">[.NET Core 3,0](https://dotnet.microsoft.com/download) veya daha yeni bir sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="953dc-110">Install the [.NET Core 3.0](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="953dc-111">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="953dc-111">Create the application</span></span>

<span data-ttu-id="953dc-112">İlk adım, uygulamayı oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="953dc-112">The first step is to create the application:</span></span>

1. <span data-ttu-id="953dc-113">Yeni bir klasör oluşturun ve bu klasörde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="953dc-113">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="953dc-114">Projeyi daha kolay hale getirmek için kullanarak bir Visual Studio çözüm dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="953dc-114">To make building the project easier, create a Visual Studio solution file using.</span></span> <span data-ttu-id="953dc-115">Aynı klasörde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="953dc-115">Run the following command in the same folder:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="953dc-116">Uygulama projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="953dc-116">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="953dc-117">Şimdi uygulamamızın iskektlerini dolduracağız.</span><span class="sxs-lookup"><span data-stu-id="953dc-117">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="953dc-118">*Appwithplugin/program. cs* dosyasındaki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="953dc-118">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="953dc-119">Eklenti arabirimlerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="953dc-119">Create the plugin interfaces</span></span>

<span data-ttu-id="953dc-120">Eklentilerle uygulama oluşturmanın bir sonraki adımı, eklentilerin uygulanması gereken arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="953dc-120">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="953dc-121">Uygulamanız ve eklentiler arasında iletişim kurmak için kullanmayı planladığınız türleri içeren bir sınıf kitaplığı almanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="953dc-121">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="953dc-122">Bu bölüm, tam uygulamanızı teslim etmek zorunda kalmadan eklenti arabiriminizi bir paket olarak yayımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="953dc-122">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="953dc-123">Projenin kök klasöründe, öğesini çalıştırın `dotnet new classlib -o PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="953dc-123">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="953dc-124">Ayrıca, projeyi `dotnet sln add PluginBase/PluginBase.csproj` çözüm dosyasına eklemek için öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="953dc-124">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="953dc-125">Dosyayı silin ve aşağıdaki arabirim tanımıyla adlı `PluginBase` `ICommand.cs` klasörde yeni bir dosya oluşturun: `PluginBase/Class1.cs`</span><span class="sxs-lookup"><span data-stu-id="953dc-125">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="953dc-126">Bu `ICommand` arabirim, tüm eklentilerin uygulayamayacağı arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="953dc-126">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="953dc-127">`ICommand` Arabirim tanımlandığına göre, uygulama projesi biraz daha fazla doldurulabilir.</span><span class="sxs-lookup"><span data-stu-id="953dc-127">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="953dc-128">Kök klasördeki `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` komutla projeye bir `AppWithPlugin` başvuru `PluginBase` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="953dc-128">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="953dc-129">Verilen dosya yollarından eklentileri yüklemesini etkinleştirmek için yorumuaşağıdakikodparçacığıiledeğiştirin:`// Load commands from plugins`</span><span class="sxs-lookup"><span data-stu-id="953dc-129">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="953dc-130">Sonra `// Output the loaded commands` yorumu aşağıdaki kod parçacığı ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="953dc-130">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="953dc-131">`// Execute the command with the name passed as an argument` Yorumu aşağıdaki kod parçacığıyla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="953dc-131">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="953dc-132">Son olarak, burada gösterildiği gibi, ve `Program` `CreateCommands`adlı `LoadPlugin` sınıfa statik yöntemler ekleyin:</span><span class="sxs-lookup"><span data-stu-id="953dc-132">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="953dc-133">Eklentileri yükle</span><span class="sxs-lookup"><span data-stu-id="953dc-133">Load plugins</span></span>

<span data-ttu-id="953dc-134">Artık uygulama, yüklenen eklenti derlemelerinden komutları doğru bir şekilde yükleyebilir ve örneklendirilecek, ancak hala eklenti derlemelerini yükleyemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="953dc-134">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it is still unable to load the plugin assemblies.</span></span> <span data-ttu-id="953dc-135">*Appwithplugin* klasöründe aşağıdaki içeriğe sahip *PluginLoadContext.cs* adlı bir dosya oluşturun:</span><span class="sxs-lookup"><span data-stu-id="953dc-135">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="953dc-136">`PluginLoadContext` Tür öğesinden<xref:System.Runtime.Loader.AssemblyLoadContext>türetilir.</span><span class="sxs-lookup"><span data-stu-id="953dc-136">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="953dc-137">Bu `AssemblyLoadContext` tür çalışma zamanında, geliştiricilerin, derleme sürümlerinin çakışmadığından emin olmak için yüklü derlemeleri farklı gruplara yalıtmalarına olanak tanıyan özel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="953dc-137">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions do not conflict.</span></span> <span data-ttu-id="953dc-138">Ayrıca, özel `AssemblyLoadContext` , derlemeleri yüklemek için farklı yollar seçebilir ve varsayılan davranışı geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="953dc-138">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="953dc-139">, `PluginLoadContext` Derleme adlarını yollara çözümlemek için `AssemblyDependencyResolver` .NET Core 3,0 ' de tanıtılan türün bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="953dc-139">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="953dc-140">`AssemblyDependencyResolver` Nesnesi, .NET sınıf kitaplığı yoluyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="953dc-140">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="953dc-141">Derlemeleri ve yerel kitaplıkları, yolu `AssemblyDependencyResolver` oluşturucuya geçilen sınıf kitaplığı için *. Deps. JSON* dosyasını temel alarak göreli yollarına çözümler.</span><span class="sxs-lookup"><span data-stu-id="953dc-141">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="953dc-142">Özel `AssemblyLoadContext` , eklentilerin kendi bağımlılıklarına sahip olmasını sağlar `AssemblyDependencyResolver` ve bağımlılıkları doğru şekilde yüklemeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="953dc-142">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="953dc-143">`AppWithPlugin` `Program.LoadPlugin` Projenin türüolduğunagöre,yöntemiaşağıdakigövdelegüncelleştirin`PluginLoadContext` :</span><span class="sxs-lookup"><span data-stu-id="953dc-143">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="953dc-144">Her eklenti için farklı `PluginLoadContext` bir örnek kullanarak, Eklentiler, sorun olmadan farklı veya hatta çakışan bağımlılıklara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="953dc-144">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="create-a-simple-plugin-with-no-dependencies"></a><span data-ttu-id="953dc-145">Bağımlılıkları olmayan basit bir eklenti oluşturma</span><span class="sxs-lookup"><span data-stu-id="953dc-145">Create a simple plugin with no dependencies</span></span>

<span data-ttu-id="953dc-146">Kök klasöre geri döndüğünüzde şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="953dc-146">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="953dc-147">Adlı `HelloPlugin`yeni bir sınıf kitaplığı projesi oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="953dc-147">Run the following command to create a new class library project named `HelloPlugin`:</span></span>
    
    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="953dc-148">Projeyi `AppWithPlugin` çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="953dc-148">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="953dc-149">*Merhaba Plugin/Class1. cs* dosyasını aşağıdaki içeriklerle *HelloCommand.cs* adlı bir dosyayla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="953dc-149">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="953dc-150">Şimdi, *Helloplugin. csproj* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="953dc-150">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="953dc-151">Şuna benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="953dc-151">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="953dc-152">`<Project>` Etiketler arasında, aşağıdaki öğeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="953dc-152">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

<span data-ttu-id="953dc-153">`<Private>false</Private>` Öğesi çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="953dc-153">The `<Private>false</Private>` element is very important.</span></span> <span data-ttu-id="953dc-154">Bu, MSBuild 'in *Pluginbase. dll dosyasını* helloplugin çıkış dizinine kopyalamamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="953dc-154">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="953dc-155">' Nin çıkış dizininde *pluginbase. dll* derlemesi varsa, `PluginLoadContext` derlemeyi bulur ve *Merhaba Plugin. dll* derlemesini yüklediğinde yükler.</span><span class="sxs-lookup"><span data-stu-id="953dc-155">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="953dc-156">Bu noktada, `HelloPlugin.HelloCommand` türü, varsayılan yükleme bağlamına `ICommand` yüklenen `ICommand` arabirimi değil,, `HelloPlugin` projenin çıkış dizinindeki *pluginbase. dll* ' den arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="953dc-156">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="953dc-157">Çalışma zamanı, bu iki türü farklı derlemelerden farklı türler olarak gördüğünden, `AppWithPlugin.Program.CreateCommands` bu yöntem komutları bulamaz.</span><span class="sxs-lookup"><span data-stu-id="953dc-157">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method will not find the commands.</span></span> <span data-ttu-id="953dc-158">Sonuç olarak, `<Private>false</Private>` eklenti arabirimlerini içeren derlemeye başvuru için meta veriler gerekir.</span><span class="sxs-lookup"><span data-stu-id="953dc-158">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="953dc-159">Proje tamamlandığına göre, `HelloPlugin` eklentinin nerede bulunabileceğinizi bilmesi için `AppWithPlugin` projeyi güncelleştirmemiz gerekir. `HelloPlugin`</span><span class="sxs-lookup"><span data-stu-id="953dc-159">Now that the `HelloPlugin` project is complete, we should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="953dc-160">Açıklamadan sonra, `pluginPaths` dizinin bir öğesi olarak ekleyin. `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` `// Paths to plugins to load`</span><span class="sxs-lookup"><span data-stu-id="953dc-160">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="create-a-plugin-with-library-dependencies"></a><span data-ttu-id="953dc-161">Kitaplık bağımlılıklarıyla eklenti oluşturma</span><span class="sxs-lookup"><span data-stu-id="953dc-161">Create a plugin with library dependencies</span></span>

<span data-ttu-id="953dc-162">Neredeyse tüm eklentiler basit bir "Merhaba Dünya" öğesinden daha karmaşıktır ve birçok eklenti diğer kitaplıklara bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="953dc-162">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="953dc-163">Örnekteki `JsonPlugin` `Newtonsoft.Json`ve `OldJson` eklenti projeleri üzerinde NuGet paketi bağımlılıklarını içeren iki eklenti örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="953dc-163">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="953dc-164">Proje dosyaları, proje başvuruları için özel bilgilere sahip değildir ve (eklenti yolları `pluginPaths` diziye eklendikten sonra) Eklentiler, appwithplugin uygulamasının yürütülmesi halinde çalıştırılsa bile kusursuz bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="953dc-164">The project files themselves do not have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="953dc-165">Ancak, bu projeler başvurulan derlemeleri çıkış dizinine kopyalamadıkları için, eklentilerin çalışması için kullanıcının makinesinde derlemelerin mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="953dc-165">However, these projects do not copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="953dc-166">Bu sorunu geçici olarak çözmek için iki yol vardır.</span><span class="sxs-lookup"><span data-stu-id="953dc-166">There are two ways to work around this problem.</span></span> <span data-ttu-id="953dc-167">İlk seçenek, sınıf kitaplığını yayımlamak için `dotnet publish` komutunu kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="953dc-167">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="953dc-168">Alternatif olarak, eklenti `dotnet build` için çıkışını kullanmak istiyorsanız, eklentinin proje dosyasındaki `<PropertyGroup>` Etiketler arasına `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` özelliği ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="953dc-168">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="953dc-169">Örnek için bkz. eklentiprojesi.`XcopyablePlugin`</span><span class="sxs-lookup"><span data-stu-id="953dc-169">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-plugin-examples-in-the-sample"></a><span data-ttu-id="953dc-170">Örnekteki diğer eklenti örnekleri</span><span class="sxs-lookup"><span data-stu-id="953dc-170">Other plugin examples in the sample</span></span>

<span data-ttu-id="953dc-171">Bu öğreticinin tüm kaynak kodu [DotNet/Samples deposunda](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="953dc-171">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="953dc-172">Tamamlanan örnek, bazı `AssemblyDependencyResolver` davranış örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="953dc-172">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="953dc-173">Örneğin, `AssemblyDependencyResolver` nesne yerel kitaplıkları ve NuGet paketlerine dahil edilen yerelleştirilmiş uydu derlemelerini de çözümleyebilir.</span><span class="sxs-lookup"><span data-stu-id="953dc-173">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="953dc-174">Örnekler deposunda `FrenchPlugin` ve bu senaryolar gösterilmektedir. `UVPlugin`</span><span class="sxs-lookup"><span data-stu-id="953dc-174">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a><span data-ttu-id="953dc-175">NuGet paketinde tanımlanan eklenti arabirimi derlemesine başvurma</span><span class="sxs-lookup"><span data-stu-id="953dc-175">How to reference a plugin interface assembly defined in a NuGet package</span></span>

<span data-ttu-id="953dc-176">Adlı bir uygulama olan, adlı `A.PluginBase`NuGet paketinde tanımlanmış bir eklenti arabirimi olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="953dc-176">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="953dc-177">Eklenti projenizde pakete doğru şekilde nasıl başvurdunuz?</span><span class="sxs-lookup"><span data-stu-id="953dc-177">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="953dc-178">Proje başvuruları için, proje dosyasındaki `<Private>false</Private>` `ProjectReference` öğesindeki meta verilerin kullanılması dll 'nin çıkışa kopyalanmasını engelledi.</span><span class="sxs-lookup"><span data-stu-id="953dc-178">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="953dc-179">`A.PluginBase` Pakete doğru bir şekilde başvurmak için proje dosyasındaki `<PackageReference>` öğeyi şu şekilde değiştirmek istersiniz:</span><span class="sxs-lookup"><span data-stu-id="953dc-179">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="953dc-180">Bu, `A.PluginBase` derlemelerin eklentinin çıkış dizinine kopyalanmasını engeller ve eklenti 'un `A.PluginBase`bir sürümünü kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="953dc-180">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="953dc-181">Eklenti hedef Framework önerileri</span><span class="sxs-lookup"><span data-stu-id="953dc-181">Plugin target framework recommendations</span></span>

<span data-ttu-id="953dc-182">Eklenti bağımlılık yüklemesi *. Deps. JSON* dosyasını kullandığından, eklentinin hedef çerçevesiyle ilgili bir Gotcha vardır.</span><span class="sxs-lookup"><span data-stu-id="953dc-182">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="953dc-183">Özellikle, eklentilerinizin bir .NET Standard sürümü yerine .NET Core 3,0 gibi bir çalışma zamanını hedeflemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="953dc-183">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="953dc-184">*. Deps. JSON* dosyası, projenin hedeflediği çerçeveye göre oluşturulur ve birçok .NET Standard uyumlu paket, belirli çalışma zamanları için .NET Standard ve uygulama derlemelerinin oluşturulmasına yönelik başvuru derlemeleri sunduğundan, *. Deps. JSON* uygulama derlemelerini doğru görmeyebilir veya Istediğiniz .NET Core sürümü yerine bir derlemenin .NET Standard sürümünü alabilir.</span><span class="sxs-lookup"><span data-stu-id="953dc-184">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>
