---
title: Eklentilerle .NET Core uygulaması oluşturma
description: Eklentileri destekleyen bir .NET Core uygulamasını nasıl oluşturabilirsiniz öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: eae792ddaa6655bfdcd932d3cb695f9dafa68130
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240850"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="96859-103">Eklentilerle .NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="96859-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="96859-104">Bu öğretici, eklentileri yüklemek <xref:System.Runtime.Loader.AssemblyLoadContext> için özel bir oluşturmak için nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="96859-104">This tutorial shows you how to create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load plugins.</span></span> <span data-ttu-id="96859-105">A, <xref:System.Runtime.Loader.AssemblyDependencyResolver> eklentinin bağımlılıklarını gidermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="96859-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> is used to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="96859-106">Öğretici, eklentinin bağımlılıklarını barındırma uygulamasından doğru bir şekilde yalıtır.</span><span class="sxs-lookup"><span data-stu-id="96859-106">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span> <span data-ttu-id="96859-107">Şunları öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="96859-107">You'll learn how to:</span></span>

- <span data-ttu-id="96859-108">Eklentileri desteklemek için bir proje yapıla.</span><span class="sxs-lookup"><span data-stu-id="96859-108">Structure a project to support plugins.</span></span>
- <span data-ttu-id="96859-109">Her eklentiyi yüklemek için özel <xref:System.Runtime.Loader.AssemblyLoadContext> bir resim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="96859-109">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="96859-110">Eklentilerin <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> bağımlılıkları olması için türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="96859-110">Use the <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="96859-111">Yapı yapılarını kopyalayarak kolayca dağıtılabilen yazar eklentileri.</span><span class="sxs-lookup"><span data-stu-id="96859-111">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96859-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="96859-112">Prerequisites</span></span>

- <span data-ttu-id="96859-113">[.NET Core 3.0 SDK'yı](https://dotnet.microsoft.com/download) veya daha yeni bir sürümü yükleyin.</span><span class="sxs-lookup"><span data-stu-id="96859-113">Install the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="96859-114">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="96859-114">Create the application</span></span>

<span data-ttu-id="96859-115">İlk adım, uygulamayı oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="96859-115">The first step is to create the application:</span></span>

1. <span data-ttu-id="96859-116">Yeni bir klasör oluşturun ve bu klasörde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="96859-116">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="96859-117">Projeyi oluşturmayı kolaylaştırmak için aynı klasörde bir Visual Studio çözüm dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="96859-117">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="96859-118">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="96859-118">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="96859-119">Uygulama projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="96859-119">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="96859-120">Şimdi başvurumuzun iskeletini doldurabiliriz.</span><span class="sxs-lookup"><span data-stu-id="96859-120">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="96859-121">*AppWithPlugin/Program.cs* dosyasındaki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="96859-121">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="96859-122">Eklenti arayüzlerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="96859-122">Create the plugin interfaces</span></span>

<span data-ttu-id="96859-123">Eklentileri ile bir uygulama oluşturmada bir sonraki adım eklentileri uygulamak için gereken arayüzü tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="96859-123">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="96859-124">Uygulamanız ve eklentileriniz arasında iletişim kurmak için kullanmayı planladığınız türleri içeren bir sınıf kitaplığı oluşturmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="96859-124">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="96859-125">Bu bölüm, tam uygulamanızı göndermenize gerek kalmadan eklenti arabiriminizi paket olarak yayımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="96859-125">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="96859-126">Projenin kök klasöründe çalıştırın. `dotnet new classlib -o PluginBase`</span><span class="sxs-lookup"><span data-stu-id="96859-126">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="96859-127">Ayrıca, `dotnet sln add PluginBase/PluginBase.csproj` projeyi çözüm dosyasına eklemek için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96859-127">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="96859-128">Dosyayı `PluginBase/Class1.cs` silin ve aşağıdaki arabirim `PluginBase` tanımıyla birlikte adlı `ICommand.cs` klasörde yeni bir dosya oluşturun:</span><span class="sxs-lookup"><span data-stu-id="96859-128">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

<span data-ttu-id="96859-129">Bu `ICommand` arabirim, tüm eklentilerin uygulayacağı arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="96859-129">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="96859-130">Artık `ICommand` arabirim tanımlandığına göre, uygulama projesi biraz daha doldurulabilir.</span><span class="sxs-lookup"><span data-stu-id="96859-130">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="96859-131">Kök klasöründen `AppWithPlugin` `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` komutla `PluginBase` projeye bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="96859-131">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="96859-132">Belirli `// Load commands from plugins` dosya yollarından eklentileri yükleyebilmek için yorumu aşağıdaki kod parçacıklarıyla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="96859-132">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="96859-133">Ardından `// Output the loaded commands` yorumu aşağıdaki kod parçacıklarıyla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="96859-133">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="96859-134">`// Execute the command with the name passed as an argument` Yorumu aşağıdaki parçacıkla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="96859-134">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="96859-135">Ve son olarak, burada `Program` gösterildiği `LoadPlugin` `CreateCommands`gibi adlı sınıfa statik yöntemler ekleyin:</span><span class="sxs-lookup"><span data-stu-id="96859-135">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="96859-136">Yük eklentileri</span><span class="sxs-lookup"><span data-stu-id="96859-136">Load plugins</span></span>

<span data-ttu-id="96859-137">Artık uygulama, yüklü eklenti montajlarından komutları doğru bir şekilde yükleyebilir ve anında atabiliyor, ancak yine de eklenti montajlarını yükleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="96859-137">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it's still unable to load the plugin assemblies.</span></span> <span data-ttu-id="96859-138">*AppWithPlugin* klasöründe aşağıdaki içerikleri içeren *PluginLoadContext.cs* adlı bir dosya oluşturun:</span><span class="sxs-lookup"><span data-stu-id="96859-138">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="96859-139">Türü `PluginLoadContext` nden <xref:System.Runtime.Loader.AssemblyLoadContext>türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="96859-139">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="96859-140">Tür, `AssemblyLoadContext` çalışma zamanında geliştiricilerin yüklü derlemeleri derleme sürümlerinin çakışmaması için farklı gruplara ayırmasına olanak tanıyan özel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="96859-140">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions don't conflict.</span></span> <span data-ttu-id="96859-141">Ayrıca, bir `AssemblyLoadContext` özel gelen derlemeleri yüklemek ve varsayılan davranışı geçersiz kılmak için farklı yollar seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96859-141">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="96859-142">Derleme `PluginLoadContext` adlarını yollara çözümlemek için .NET Core 3.0'da tanıtılan `AssemblyDependencyResolver` türün bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="96859-142">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="96859-143">Nesne `AssemblyDependencyResolver` ,NET sınıf kitaplığına giden yol ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="96859-143">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="96859-144">Derlemeleri ve yerel kitaplıkları, yolu `AssemblyDependencyResolver` oluşturucuya geçirilen sınıf kitaplığı için *.deps.json* dosyasına göre göreli yollarına giderir.</span><span class="sxs-lookup"><span data-stu-id="96859-144">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="96859-145">Özel, `AssemblyLoadContext` eklentilerin kendi bağımlılıklarına sahip olmasını sağlar `AssemblyDependencyResolver` ve bağımlılıkları doğru şekilde yüklemeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="96859-145">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="96859-146">Artık `AppWithPlugin` proje `PluginLoadContext` türüne sahip olduğuna `Program.LoadPlugin` göre, yöntemi aşağıdaki gövdeyle güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="96859-146">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="96859-147">Her eklenti `PluginLoadContext` için farklı bir örnek kullanarak, eklentileri sorun olmadan farklı ve hatta çakışan bağımlılıklar olabilir.</span><span class="sxs-lookup"><span data-stu-id="96859-147">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="simple-plugin-with-no-dependencies"></a><span data-ttu-id="96859-148">Bağımlılık olmadan basit eklenti</span><span class="sxs-lookup"><span data-stu-id="96859-148">Simple plugin with no dependencies</span></span>

<span data-ttu-id="96859-149">Kök klasöründe aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="96859-149">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="96859-150">Adlı yeni bir sınıf kitaplığı projesi `HelloPlugin`oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="96859-150">Run the following command to create a new class library project named `HelloPlugin`:</span></span>

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="96859-151">Projeyi çözüme eklemek için `AppWithPlugin` aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="96859-151">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="96859-152">*HelloPlugin/Class1.cs* dosyasını aşağıdaki içeriklerle *HelloCommand.cs* adlı bir dosyayla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="96859-152">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="96859-153">Şimdi, *HelloPlugin.csproj* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="96859-153">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="96859-154">Şunun gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="96859-154">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="96859-155">Etiketlerin `<Project>` arasına aşağıdaki öğeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="96859-155">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

<span data-ttu-id="96859-156">Öğe `<Private>false</Private>` önemlidir.</span><span class="sxs-lookup"><span data-stu-id="96859-156">The `<Private>false</Private>` element is important.</span></span> <span data-ttu-id="96859-157">Bu, MSBuild'e HelloPlugin'in çıktı dizini için *PluginBase.dll* kopyalamamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="96859-157">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="96859-158">*PluginBase.dll* derlemesi çıkış dizininde mevcutsa, `PluginLoadContext` montajı orada bulur ve *HelloPlugin.dll* derlemesini yüklerken yükler.</span><span class="sxs-lookup"><span data-stu-id="96859-158">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="96859-159">Bu noktada, `HelloPlugin.HelloCommand` tür, varsayılan `ICommand` yük bağlamına yüklenen `HelloPlugin` `ICommand` arabirimyerine, projenin çıktı dizinindeki *PluginBase.dll'deki* arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="96859-159">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="96859-160">Çalışma zamanı bu iki türü farklı derlemelerden farklı `AppWithPlugin.Program.CreateCommands` türler olarak gördüğünden, yöntem komutları bulamaz.</span><span class="sxs-lookup"><span data-stu-id="96859-160">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method won't find the commands.</span></span> <span data-ttu-id="96859-161">Sonuç olarak, `<Private>false</Private>` meta veri eklenti arabirimleri içeren derleme başvuru için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="96859-161">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="96859-162">Benzer şekilde, `<ExcludeAssets>runtime</ExcludeAssets>` diğer paketlere `PluginBase` başvuruyorsa, öğe de önemlidir.</span><span class="sxs-lookup"><span data-stu-id="96859-162">Similarly, the `<ExcludeAssets>runtime</ExcludeAssets>` element is also important if the `PluginBase` references other packages.</span></span> <span data-ttu-id="96859-163">Bu ayar, proje `<Private>false</Private>` veya bağımlılıklarından birinin `PluginBase` içerebileceği paket başvurularıyla aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="96859-163">This setting has the same effect as `<Private>false</Private>` but works on package references that the `PluginBase` project or one of its dependencies may include.</span></span>

<span data-ttu-id="96859-164">`HelloPlugin` Proje tamamlandığından, `HelloPlugin` eklentinin nerede bulunabileceğini bilmek için projeyi `AppWithPlugin` güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="96859-164">Now that the `HelloPlugin` project is complete, you should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="96859-165">Açıklamadan `// Paths to plugins to load` sonra, `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` `pluginPaths` dizinin bir öğesi olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="96859-165">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="plugin-with-library-dependencies"></a><span data-ttu-id="96859-166">Kitaplık bağımlılıkları ile eklenti</span><span class="sxs-lookup"><span data-stu-id="96859-166">Plugin with library dependencies</span></span>

<span data-ttu-id="96859-167">Hemen hemen tüm eklentileri basit bir "Hello World" daha karmaşık ve birçok eklentileri diğer kütüphaneler üzerinde bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="96859-167">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="96859-168">`JsonPlugin` Örnekteki `OldJson` ve eklenti projeleri, NuGet paket bağımlılıkları olan eklentilerin `Newtonsoft.Json`iki örneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="96859-168">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="96859-169">Proje dosyalarının proje başvuruları için özel bir bilgisi yoktur ve `pluginPaths` (diziye eklenti yollarını ekledikten sonra) eklentiler AppWithPlugin uygulamasının aynı yürütülmesinde çalıştırılsa bile mükemmel çalışır.</span><span class="sxs-lookup"><span data-stu-id="96859-169">The project files themselves don't have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="96859-170">Ancak, bu projeler başvurulan derlemeleri çıktı diziniiçin kopyalamaz, bu nedenle eklentilerin çalışması için derlemelerin kullanıcının makinesinde bulunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="96859-170">However, these projects don't copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="96859-171">Bu sorunu aşmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="96859-171">There are two ways to work around this problem.</span></span> <span data-ttu-id="96859-172">İlk seçenek, sınıf `dotnet publish` kitaplığını yayımlamak için komutu kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="96859-172">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="96859-173">Alternatif olarak, eklentiniz `dotnet build` için çıktıyı kullanabilmek istiyorsanız, özelliği eklentinin `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` proje `<PropertyGroup>` dosyasındaki etiketler arasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96859-173">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="96859-174">Örnek `XcopyablePlugin` olarak eklenti projesine bakın.</span><span class="sxs-lookup"><span data-stu-id="96859-174">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-examples-in-the-sample"></a><span data-ttu-id="96859-175">Örnekteki diğer örnekler</span><span class="sxs-lookup"><span data-stu-id="96859-175">Other examples in the sample</span></span>

<span data-ttu-id="96859-176">Bu öğretici için tam kaynak kodu [dotnet / örnek deposunda](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="96859-176">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="96859-177">Tamamlanan örnek, birkaç davranış `AssemblyDependencyResolver` örneği daha içerir.</span><span class="sxs-lookup"><span data-stu-id="96859-177">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="96859-178">Örneğin, `AssemblyDependencyResolver` nesne yerel kitaplıkları ve NuGet paketlerinde yer alan yerelleştirilmiş uydu derlemelerini de çözebilir.</span><span class="sxs-lookup"><span data-stu-id="96859-178">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="96859-179">Örnek `UVPlugin` `FrenchPlugin` deposunda ve depoda bu senaryoları gösterir.</span><span class="sxs-lookup"><span data-stu-id="96859-179">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a><span data-ttu-id="96859-180">NuGet paketinden bir eklenti arabirimine başvurun</span><span class="sxs-lookup"><span data-stu-id="96859-180">Reference a plugin interface from a NuGet package</span></span>

<span data-ttu-id="96859-181">NuGet paketinde tanımlanan bir eklenti arabirimi olan bir uygulama A `A.PluginBase`olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="96859-181">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="96859-182">Eklenti projenizde paketi nasıl doğru bir şekilde başvurursunuz?</span><span class="sxs-lookup"><span data-stu-id="96859-182">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="96859-183">Proje başvuruları için, `<Private>false</Private>` proje dosyasındaki `ProjectReference` öğedeki meta verileri kullanmak dll'nin çıktıya kopyalanmasını engelledi.</span><span class="sxs-lookup"><span data-stu-id="96859-183">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="96859-184">`A.PluginBase` Paketi doğru bir şekilde başvurmak için `<PackageReference>` proje dosyasındaki öğeyi aşağıdakiyle değiştirmek istiyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="96859-184">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="96859-185">Bu, derlemelerin eklentinizin `A.PluginBase` çıktı dizinine kopyalanmasını önler ve eklentinizin A'nın `A.PluginBase`''nin sürümünü kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="96859-185">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="96859-186">Plugin hedef çerçeve önerileri</span><span class="sxs-lookup"><span data-stu-id="96859-186">Plugin target framework recommendations</span></span>

<span data-ttu-id="96859-187">Eklenti bağımlılığı *yüklemesi .deps.json* dosyasını kullandığından, eklentinin hedef çerçevesiyle ilgili bir gotcha vardır.</span><span class="sxs-lookup"><span data-stu-id="96859-187">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="96859-188">Özellikle, eklentileriniz .NET Standard'ın bir sürümü yerine .NET Core 3.0 gibi bir çalışma süresini hedeflemelidir.</span><span class="sxs-lookup"><span data-stu-id="96859-188">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="96859-189">*.deps.json* dosyası, proje hedeflerinin hangi çerçeveye göre oluşturulduğuna göre oluşturulur ve .NET Standart uyumlu birçok paket ,NET Standard ve belirli çalışma süreleri için uygulama derlemeleri karşı oluşturmak için referans derlemeleri olduğundan, *.deps.json* uygulama derlemelerini doğru göremeyebilir veya beklediğiniz .NET Core sürümü yerine bir derlemenin .NET Standart sürümünü kapabilir.</span><span class="sxs-lookup"><span data-stu-id="96859-189">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>

## <a name="plugin-framework-references"></a><span data-ttu-id="96859-190">Eklenti çerçeve referansları</span><span class="sxs-lookup"><span data-stu-id="96859-190">Plugin framework references</span></span>

<span data-ttu-id="96859-191">Şu anda, eklentiler sürece yeni çerçeveler getiremez.</span><span class="sxs-lookup"><span data-stu-id="96859-191">Currently, plugins can't introduce new frameworks into the process.</span></span> <span data-ttu-id="96859-192">Örneğin, çerçeveyi `Microsoft.AspNetCore.App` kullanan bir eklentiyi yalnızca kök `Microsoft.NETCore.App` çerçeveyi kullanan bir uygulamaya yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="96859-192">For example, you can't load a plugin that uses the `Microsoft.AspNetCore.App` framework into an application that only uses the root `Microsoft.NETCore.App` framework.</span></span> <span data-ttu-id="96859-193">Ana bilgisayar uygulaması, eklentilerin ihtiyaç duyduğu tüm çerçevelere başvuru bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="96859-193">The host application must declare references to all frameworks needed by plugins.</span></span>
