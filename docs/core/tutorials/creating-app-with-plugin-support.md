---
title: Eklenti ile .NET Core uygulaması oluşturma
description: Eklentileri destekleyen bir .NET Core uygulaması oluşturmayı öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: f2997c778b87ecd88c0fd2fadf491763066a4950
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55739609"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="b9480-103">Eklenti ile .NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9480-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="b9480-104">Bu öğretici, nasıl gösterir için:</span><span class="sxs-lookup"><span data-stu-id="b9480-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="b9480-105">Eklentileri desteklemek için bir proje yapısı.</span><span class="sxs-lookup"><span data-stu-id="b9480-105">Structure a project to support plugins.</span></span>
- <span data-ttu-id="b9480-106">Bir özel Oluştur <xref:System.Runtime.Loader.AssemblyLoadContext> her Eklentisi yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="b9480-106">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="b9480-107">Kullanım `System.Runtime.Loader.AssemblyDependencyResolver` bağımlılıkları eklentileri izin vermek için türü.</span><span class="sxs-lookup"><span data-stu-id="b9480-107">Use the `System.Runtime.Loader.AssemblyDependencyResolver` type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="b9480-108">Yalnızca derleme yapıtları kopyalayarak kolayca dağıtılabilir eklentileri yazar.</span><span class="sxs-lookup"><span data-stu-id="b9480-108">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b9480-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b9480-109">Prerequisites</span></span>

- <span data-ttu-id="b9480-110">Yükleme [.NET Core 3.0 Önizleme 2 SDK](https://www.microsoft.com/net/core) ya da daha yeni bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="b9480-110">Install the [.NET Core 3.0 Preview 2 SDK](https://www.microsoft.com/net/core) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="b9480-111">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9480-111">Create the application</span></span>

<span data-ttu-id="b9480-112">İlk adım, uygulama oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="b9480-112">The first step is to create the application:</span></span>

1. <span data-ttu-id="b9480-113">Yeni bir klasör oluşturun ve o klasördeki çalıştırmak `dotnet new console -o AppWithPlugin`.</span><span class="sxs-lookup"><span data-stu-id="b9480-113">Create a new folder, and in that folder run `dotnet new console -o AppWithPlugin`.</span></span> 
2. <span data-ttu-id="b9480-114">Daha kolay proje derleme yapmak için Visual Studio çözüm dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b9480-114">To make building the project easier, create a Visual Studio solution file.</span></span> <span data-ttu-id="b9480-115">Çalıştırma `dotnet new sln` aynı klasörde yer alan.</span><span class="sxs-lookup"><span data-stu-id="b9480-115">Run `dotnet new sln` in the same folder.</span></span> 
3. <span data-ttu-id="b9480-116">Çalıştırma `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` uygulaması projesi çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="b9480-116">Run `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` to add the app project to the solution.</span></span>

<span data-ttu-id="b9480-117">Şimdi biz uygulamamız çatısında önizlememiz doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9480-117">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="b9480-118">Değiştirin *AppWithPlugin/Program.cs* dosyasındaki kodu aşağıdaki kodla:</span><span class="sxs-lookup"><span data-stu-id="b9480-118">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="b9480-119">Eklentisi arabirimleri oluşturun</span><span class="sxs-lookup"><span data-stu-id="b9480-119">Create the plugin interfaces</span></span>

<span data-ttu-id="b9480-120">Eklentiler ile bir uygulama oluşturmanın sonraki adımı eklentileri oluşturmanız arabirimi tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="b9480-120">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="b9480-121">Uygulama ve eklentiler arasında iletişim kurmak için kullanmayı planladığınız herhangi bir türü içeren bir sınıf kitaplığı yapmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="b9480-121">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="b9480-122">Bu bölme, tam uygulamanız göndermek zorunda kalmadan bir paket olarak, eklenti arabirimi yayımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9480-122">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="b9480-123">Projenin kök klasöründe Çalıştır `dotnet new classlib -o PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="b9480-123">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="b9480-124">Ayrıca, `dotnet sln add PluginBase/PluginBase.csproj` projeyi çözüm dosyasına eklemek için.</span><span class="sxs-lookup"><span data-stu-id="b9480-124">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="b9480-125">Silme `PluginBase/Class1.cs` dosya ve yeni bir dosya oluşturun `PluginBase` adlı klasöre `ICommand.cs` aşağıdaki arabirim tanımı ile:</span><span class="sxs-lookup"><span data-stu-id="b9480-125">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="b9480-126">Bu `ICommand` arabirimidir arabirimi tüm eklentileri uygulamanız.</span><span class="sxs-lookup"><span data-stu-id="b9480-126">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="b9480-127">Şimdi `ICommand` arabirimi tanımlanır, uygulama projesine doldurulabilir biraz daha.</span><span class="sxs-lookup"><span data-stu-id="b9480-127">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="b9480-128">Başvuru ekleme `AppWithPlugin` için proje `PluginBase` ile proje `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` kök klasörden komutu.</span><span class="sxs-lookup"><span data-stu-id="b9480-128">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="b9480-129">Değiştirin `// Load commands from plugins` eklentilerini yüklemek etkinleştirmek için aşağıdaki kod parçacığı ile Açıklama gelen dosya yolu ele alalım:</span><span class="sxs-lookup"><span data-stu-id="b9480-129">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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



<span data-ttu-id="b9480-130">Ardından değiştirin `// Output the loaded commands` aşağıdaki kod parçacığı ile Açıklama:</span><span class="sxs-lookup"><span data-stu-id="b9480-130">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="b9480-131">Değiştirin `// Execute the command with the name passed as an argument` aşağıdaki kod parçacığıyla açıklaması:</span><span class="sxs-lookup"><span data-stu-id="b9480-131">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="b9480-132">Ve son olarak, statik yöntemler ekleyin `Program` adlı sınıfı `LoadPlugin` ve `CreateCommands`, burada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="b9480-132">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="b9480-133">Eklenti yükleme</span><span class="sxs-lookup"><span data-stu-id="b9480-133">Load plugins</span></span>

<span data-ttu-id="b9480-134">Artık uygulamanın düzgün yüklenebileceği ve komutlar yüklü eklenti derlemelerden örneği, ancak Eklenti derlemeleri yüklemek hala işleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="b9480-134">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it is still unable to load the plugin assemblies.</span></span> <span data-ttu-id="b9480-135">Adlı bir dosya oluşturun *PluginLoadContext.cs* içinde *AppWithPlugin* klasöründe aşağıdaki içeriğe sahip:</span><span class="sxs-lookup"><span data-stu-id="b9480-135">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="b9480-136">`PluginLoadContext` Tür türetilir <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="b9480-136">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="b9480-137">`AssemblyLoadContext` Sayesinde geliştiriciler, yüklenen derlemeler derleme sürümlerini çakışmasını emin olmak için farklı gruplar halinde ayırmak için çalışma zamanında bir özel tür bir türdür.</span><span class="sxs-lookup"><span data-stu-id="b9480-137">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions do not conflict.</span></span> <span data-ttu-id="b9480-138">Ayrıca, bir özel `AssemblyLoadContext` derlemeleri yüklemek ve varsayılan davranışı geçersiz kılmak için farklı yollar seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9480-138">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="b9480-139">`PluginLoadContext` Örneğini kullanan `AssemblyDependencyResolver` yolları için derleme adlarını çözümlemek için .NET Core 3.0 sürümünde türü.</span><span class="sxs-lookup"><span data-stu-id="b9480-139">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="b9480-140">`AssemblyDependencyResolver` Nesnesi, bir .NET sınıf kitaplığı yoluyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b9480-140">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="b9480-141">Temel kendi göreli yollar için derlemeler ve yerel kitaplıkları çözümler *deps.json* dosya yolu için geçirildi sınıf kitaplığı için `AssemblyDependencyResolver` Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="b9480-141">It resolves assemblies and native libraries to their relative paths based on the *deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="b9480-142">Özel `AssemblyLoadContext` kendi bağımlılıkları eklentiler sağlar ve `AssemblyDependencyResolver` bağımlılıkları doğru şekilde yük kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b9480-142">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="b9480-143">Şimdi `AppWithPlugin` projesinde `PluginLoadContext` yazın, güncelleştirme `Program.LoadPlugin` aşağıdaki gövdesi olan yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b9480-143">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="b9480-144">Farklı bir kullanarak `PluginLoadContext` örneği her eklentinin, eklentiler için farklı veya hatta çakışan bağımlılıkları olmadan bir sorun olabilir.</span><span class="sxs-lookup"><span data-stu-id="b9480-144">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="create-a-simple-plugin-with-no-dependencies"></a><span data-ttu-id="b9480-145">Hiçbir bağımlılık ile basit bir eklenti oluşturun</span><span class="sxs-lookup"><span data-stu-id="b9480-145">Create a simple plugin with no dependencies</span></span>

<span data-ttu-id="b9480-146">Geri kök klasöründe aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="b9480-146">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="b9480-147">Çalıştırma `dotnet new classlib -o HelloPlugin` adlı yeni bir sınıf kitaplığı projesi oluşturmak için `HelloPlugin`.</span><span class="sxs-lookup"><span data-stu-id="b9480-147">Run `dotnet new classlib -o HelloPlugin` to create a new class library project named `HelloPlugin`.</span></span>
2. <span data-ttu-id="b9480-148">Çalıştırma `dotnet sln add HelloPlugin/HelloPlugin.csproj` projeye eklemek için `AppWithPlugin` çözüm.</span><span class="sxs-lookup"><span data-stu-id="b9480-148">Run `dotnet sln add HelloPlugin/HelloPlugin.csproj` to add the project to the `AppWithPlugin` solution.</span></span> 
3. <span data-ttu-id="b9480-149">Değiştirin *HelloPlugin/Class1.cs* adlı bir dosya dosyasıyla *HelloCommand.cs* aşağıdaki içeriklerle:</span><span class="sxs-lookup"><span data-stu-id="b9480-149">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="b9480-150">Artık, *HelloPlugin.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="b9480-150">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="b9480-151">Aşağıdakine benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="b9480-151">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="b9480-152">Arasında `<Project>` etiketler, aşağıdaki öğeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b9480-152">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

<span data-ttu-id="b9480-153">`<Private>false</Private>` Öğesi çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b9480-153">The `<Private>false</Private>` element is very important.</span></span> <span data-ttu-id="b9480-154">Bu MSBuild kopyalamayacak şekilde söyler *PluginBase.dll* HelloPlugin çıkış dizinine.</span><span class="sxs-lookup"><span data-stu-id="b9480-154">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="b9480-155">Varsa *PluginBase.dll* derleme Çıktı dizininde mevcut `PluginLoadContext` derleme var. bulup onu yüklediğinde, yükleyebilir *HelloPlugin.dll* derleme.</span><span class="sxs-lookup"><span data-stu-id="b9480-155">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="b9480-156">Bu noktada, `HelloPlugin.HelloCommand` tür tarafından uygulanır `ICommand` alanından arabirim *PluginBase.dll* Çıktı dizininde `HelloPlugin` proje değil, `ICommand` yüklendiği arabirimi Varsayılan yükleme bağlamı.</span><span class="sxs-lookup"><span data-stu-id="b9480-156">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="b9480-157">Çalışma zamanı bu iki farklı türden farklı derlemeler olarak görür. bu yana `AppWithPlugin.Program.CreateCommands` yöntemi değildir komut bulun.</span><span class="sxs-lookup"><span data-stu-id="b9480-157">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method will not find the commands.</span></span> <span data-ttu-id="b9480-158">Sonuç olarak, `<Private>false</Private>` eklentisi arabirimleri içeren derlemenin başvurusunu için meta verileri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b9480-158">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="b9480-159">Şimdi `HelloPlugin` proje tamamladığınızda, güncelleştiriyoruz `AppWithPlugin` nereden başlayacağınızı bilemiyor için proje `HelloPlugin` eklentisi bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b9480-159">Now that the `HelloPlugin` project is complete, we should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="b9480-160">Sonra `// Paths to plugins to load` açıklama, Ekle `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` öğesi olarak `pluginPaths` dizisi.</span><span class="sxs-lookup"><span data-stu-id="b9480-160">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="create-a-plugin-with-library-dependencies"></a><span data-ttu-id="b9480-161">Kitaplık bağımlılıkları olan bir eklenti oluşturun</span><span class="sxs-lookup"><span data-stu-id="b9480-161">Create a plugin with library dependencies</span></span>

<span data-ttu-id="b9480-162">Neredeyse tüm eklentiler bir basit "Hello World" daha karmaşıktır ve birçok eklenti bağımlılıkları diğer kitaplıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="b9480-162">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="b9480-163">`JsonPlugin` Ve `OldJson` örnek eklentisi projeleri göster eklentileri NuGet Paket bağımlılıklarını içeren iki örnek `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="b9480-163">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="b9480-164">Proje dosyaları proje başvuruları için herhangi bir özel bilgi yok ve (eklentisi yolları ekledikten sonra `pluginPaths` dizisi) eklentileri mükemmel bir şekilde, aynı yürütme AppWithPlugin uygulamanın çalıştırılmış olsa bile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b9480-164">The project files themselves do not have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="b9480-165">Ancak, bu projeleri derlemeleri çalışmak eklentileri için kullanıcının makinede mevcut olması gerekmez, çıktı dizinine başvurulan derlemeleri kopyalamayın.</span><span class="sxs-lookup"><span data-stu-id="b9480-165">However, these projects do not copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="b9480-166">Bu sorunu çözmek için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="b9480-166">There are two ways to work around this problem.</span></span> <span data-ttu-id="b9480-167">İlk seçenek kullanmaktır `dotnet publish` sınıf kitaplığı yayımlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="b9480-167">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="b9480-168">Alternatif olarak, çıktısını kullanabilmelerini istiyorsanız `dotnet build` , eklenti için eklediğiniz `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` arasında özellik `<PropertyGroup>` eklenti ait proje dosyasında etiketler.</span><span class="sxs-lookup"><span data-stu-id="b9480-168">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="b9480-169">Bkz: `XcopyablePlugin` eklentisi projesi bir örnek.</span><span class="sxs-lookup"><span data-stu-id="b9480-169">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-plugin-examples-in-the-sample"></a><span data-ttu-id="b9480-170">Örneğindeki diğer eklenti örnekleri</span><span class="sxs-lookup"><span data-stu-id="b9480-170">Other plugin examples in the sample</span></span>

<span data-ttu-id="b9480-171">`AssemblyDependencyResolver` Nesne yerel kitaplıkları NuGet paketlerinde yanı sıra yerelleştirilmiş yardımcı derlemeler de giderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9480-171">The `AssemblyDependencyResolver` object can also resolve native libraries included in NuGet packages as well as localized satellite assemblies.</span></span> <span data-ttu-id="b9480-172">`UVPlugin` Ve `FrenchPlugin` bu senaryolar sırasıyla gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b9480-172">The `UVPlugin` and `FrenchPlugin` demonstrate these scenarios respectively.</span></span>

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a><span data-ttu-id="b9480-173">Nasıl bir NuGet paketi içinde tanımlanmış bir eklenti arabirimi derleme başvurusu</span><span class="sxs-lookup"><span data-stu-id="b9480-173">How to reference a plugin interface assembly defined in a NuGet package</span></span>

<span data-ttu-id="b9480-174">Adlı NuGet paketi içinde tanımlanmış bir eklenti arabirimi olan bir uygulama bir olduğunu varsayalım `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="b9480-174">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="b9480-175">Nasıl paket eklenti projenizde doğru başvurmuyorsa?</span><span class="sxs-lookup"><span data-stu-id="b9480-175">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="b9480-176">Kullanarak proje başvuruları için `<Private>false</Private>` meta veri çubuğunda `ProjectReference` öğesi proje dosyasında çıktı kopyalanan dll engelledi.</span><span class="sxs-lookup"><span data-stu-id="b9480-176">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="b9480-177">Doğru şekilde başvurmak için `A.PluginBase` değiştirmek istediğiniz paketin `<PackageReference>` öğesi aşağıdaki proje dosyasında:</span><span class="sxs-lookup"><span data-stu-id="b9480-177">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="b9480-178">Bu engeller `A.PluginBase` , eklenti çıktı dizinine kopyalanan gelen derlemeleri ve kendi eklenti A kullanmanızı sağlar sürümünü `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="b9480-178">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="b9480-179">Eklenti hedef framework önerileri</span><span class="sxs-lookup"><span data-stu-id="b9480-179">Plugin target framework recommendations</span></span>

<span data-ttu-id="b9480-180">Eklenti bağımlılık yükleniyor kullandığından *deps.json* dosyası, eklenti'nın hedef framework ile ilgili bir sorunu yok.</span><span class="sxs-lookup"><span data-stu-id="b9480-180">Because plugin dependency loading uses the *deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="b9480-181">Özellikle, eklenti, bir çalışma zamanı, .NET Core 3.0 gibi .NET Standard'ın bir sürümü yerine hedeflemelidir.</span><span class="sxs-lookup"><span data-stu-id="b9480-181">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="b9480-182">`deps.json` Dosyası oluşturulur hangi framework tabanlı Proje hedefleri ve başvuru derlemelerini karşı özel çalışma zamanları, için.NETStandardveuygulamaderlemelerioluşturmakiçinbirçok.NETStandarduyumlupaketikullanımasunulduğundanbuyana`deps.json` düzgün bkz uygulama derlemelerini olabilir veya bir derleme beklediğiniz .NET Core sürümünün yerine .NET Standard sürümünü alıp.</span><span class="sxs-lookup"><span data-stu-id="b9480-182">The `deps.json` file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the `deps.json` may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>
