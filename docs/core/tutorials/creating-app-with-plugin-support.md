---
title: Eklentilerle .NET Core uygulaması oluşturma
description: Eklentileri destekleyen bir .NET Core uygulaması oluşturmayı öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: aef91231bd4a32937d6e3cd2cb7204777c6efe96
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873386"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="89a88-103">Eklentilerle .NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="89a88-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="89a88-104">Bu öğreticide, yükleme eklentilerini bir özel olarak nasıl oluşturacağınız gösterilmektedir <xref:System.Runtime.Loader.AssemblyLoadContext> .</span><span class="sxs-lookup"><span data-stu-id="89a88-104">This tutorial shows you how to create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load plugins.</span></span> <span data-ttu-id="89a88-105">, <xref:System.Runtime.Loader.AssemblyDependencyResolver> Eklentinin bağımlılıklarını çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89a88-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> is used to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="89a88-106">Öğretici, eklentinin bağımlılıklarını barındırma uygulamasından doğru şekilde yalıtır.</span><span class="sxs-lookup"><span data-stu-id="89a88-106">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span> <span data-ttu-id="89a88-107">Şunları öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="89a88-107">You'll learn how to:</span></span>

- <span data-ttu-id="89a88-108">Eklentileri desteklemek için bir proje yapısı yapın.</span><span class="sxs-lookup"><span data-stu-id="89a88-108">Structure a project to support plugins.</span></span>
- <span data-ttu-id="89a88-109"><xref:System.Runtime.Loader.AssemblyLoadContext>Her bir eklentiyi yüklemek için özel oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89a88-109">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="89a88-110"><xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName>Eklentilerin bağımlılıklara sahip olmasını sağlamak için türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="89a88-110">Use the <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="89a88-111">Yalnızca derleme yapıtları kopyalanarak kolayca dağıtılabilecek olan eklentileri yazar.</span><span class="sxs-lookup"><span data-stu-id="89a88-111">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89a88-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="89a88-112">Prerequisites</span></span>

- <span data-ttu-id="89a88-113">[.NET 5 SDK](https://dotnet.microsoft.com/download) veya daha yeni bir sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="89a88-113">Install the [.NET 5 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

> [!NOTE]
> <span data-ttu-id="89a88-114">Örnek kod .NET 5 ' i hedefler, ancak kullandığı tüm özellikler .NET Core 3,0 ' de tanıtılmıştır ve bu tarihten sonra tüm .NET sürümlerinde mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="89a88-114">The sample code targets .NET 5, but all the features it uses were introduced in .NET Core 3.0 and are available in all .NET releases since then.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="89a88-115">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="89a88-115">Create the application</span></span>

<span data-ttu-id="89a88-116">İlk adım, uygulamayı oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="89a88-116">The first step is to create the application:</span></span>

1. <span data-ttu-id="89a88-117">Yeni bir klasör oluşturun ve bu klasörde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="89a88-117">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="89a88-118">Projeyi daha kolay hale getirmek için aynı klasörde bir Visual Studio çözüm dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89a88-118">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="89a88-119">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="89a88-119">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="89a88-120">Uygulama projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="89a88-120">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="89a88-121">Şimdi uygulamamızın iskektlerini dolduracağız.</span><span class="sxs-lookup"><span data-stu-id="89a88-121">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="89a88-122">*Appwithplugin/program. cs* dosyasındaki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="89a88-122">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="89a88-123">Eklenti arabirimlerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="89a88-123">Create the plugin interfaces</span></span>

<span data-ttu-id="89a88-124">Eklentilerle uygulama oluşturmanın bir sonraki adımı, eklentilerin uygulanması gereken arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="89a88-124">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="89a88-125">Uygulamanız ve eklentiler arasında iletişim kurmak için kullanmayı planladığınız türleri içeren bir sınıf kitaplığı almanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="89a88-125">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="89a88-126">Bu bölüm, tam uygulamanızı teslim etmek zorunda kalmadan eklenti arabiriminizi bir paket olarak yayımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="89a88-126">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="89a88-127">Projenin kök klasöründe, öğesini çalıştırın `dotnet new classlib -o PluginBase` .</span><span class="sxs-lookup"><span data-stu-id="89a88-127">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="89a88-128">Ayrıca, `dotnet sln add PluginBase/PluginBase.csproj` projeyi çözüm dosyasına eklemek için öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="89a88-128">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="89a88-129">Dosyayı silin `PluginBase/Class1.cs` ve `PluginBase` aşağıdaki arabirim tanımıyla adlı klasörde yeni bir dosya oluşturun `ICommand.cs` :</span><span class="sxs-lookup"><span data-stu-id="89a88-129">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

<span data-ttu-id="89a88-130">Bu `ICommand` arabirim, tüm eklentilerin uygulayamayacağı arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="89a88-130">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="89a88-131">`ICommand`Arabirim tanımlandığına göre, uygulama projesi biraz daha fazla doldurulabilir.</span><span class="sxs-lookup"><span data-stu-id="89a88-131">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="89a88-132">`AppWithPlugin` `PluginBase` Kök klasördeki komutla projeye bir başvuru ekleyin `dotnet add AppWithPlugin/AppWithPlugin.csproj reference PluginBase/PluginBase.csproj` .</span><span class="sxs-lookup"><span data-stu-id="89a88-132">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin/AppWithPlugin.csproj reference PluginBase/PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="89a88-133">`// Load commands from plugins`Verilen dosya yollarından eklentileri yüklemesini etkinleştirmek için yorumu aşağıdaki kod parçacığı ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="89a88-133">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="89a88-134">Sonra `// Output the loaded commands` yorumu aşağıdaki kod parçacığı ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="89a88-134">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="89a88-135">`// Execute the command with the name passed as an argument`Yorumu aşağıdaki kod parçacığıyla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="89a88-135">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="89a88-136">Son olarak, `Program` `LoadPlugin` `CreateCommands` burada gösterildiği gibi, ve adlı sınıfa statik yöntemler ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89a88-136">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="89a88-137">Eklentileri yükle</span><span class="sxs-lookup"><span data-stu-id="89a88-137">Load plugins</span></span>

<span data-ttu-id="89a88-138">Artık uygulama yüklenen eklenti derlemelerinden komutları doğru bir şekilde yükleyebilir ve örneklendirilecek, ancak hala eklenti derlemelerini yükleyemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="89a88-138">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it's still unable to load the plugin assemblies.</span></span> <span data-ttu-id="89a88-139">*Appwithplugin* klasöründe aşağıdaki Içeriğe sahip *pluginloadcontext. cs* adlı bir dosya oluşturun:</span><span class="sxs-lookup"><span data-stu-id="89a88-139">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="89a88-140">`PluginLoadContext`Tür öğesinden türetilir <xref:System.Runtime.Loader.AssemblyLoadContext> .</span><span class="sxs-lookup"><span data-stu-id="89a88-140">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="89a88-141">`AssemblyLoadContext`Tür çalışma zamanında, geliştiricilerin, derleme sürümlerinin çakışmadığından emin olmak için yüklü derlemeleri farklı gruplara yalıtmalarına olanak tanıyan özel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="89a88-141">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions don't conflict.</span></span> <span data-ttu-id="89a88-142">Ayrıca, özel, `AssemblyLoadContext` derlemeleri yüklemek için farklı yollar seçebilir ve varsayılan davranışı geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="89a88-142">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="89a88-143">, `PluginLoadContext` `AssemblyDependencyResolver` Derleme adlarını yollara çözümlemek Için .net Core 3,0 ' de tanıtılan türün bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="89a88-143">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="89a88-144">`AssemblyDependencyResolver`Nesnesi, .NET sınıf kitaplığı yoluyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="89a88-144">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="89a88-145">Derlemeleri ve yerel kitaplıkları, yolu oluşturucuya geçilen sınıf kitaplığı için dosyadaki *.deps.js* dosya temelinde göreli yollarına çözümler `AssemblyDependencyResolver` .</span><span class="sxs-lookup"><span data-stu-id="89a88-145">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="89a88-146">Özel, `AssemblyLoadContext` eklentilerin kendi bağımlılıklarına sahip olmasını sağlar ve `AssemblyDependencyResolver` bağımlılıkları doğru şekilde yüklemeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="89a88-146">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="89a88-147">`AppWithPlugin`Projenin `PluginLoadContext` türü olduğuna `Program.LoadPlugin` göre, yöntemi aşağıdaki gövdele güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="89a88-147">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="89a88-148">`PluginLoadContext`Her eklenti için farklı bir örnek kullanarak, Eklentiler, sorun olmadan farklı veya hatta çakışan bağımlılıklara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="89a88-148">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="simple-plugin-with-no-dependencies"></a><span data-ttu-id="89a88-149">Bağımlılıkları olmayan basit eklenti</span><span class="sxs-lookup"><span data-stu-id="89a88-149">Simple plugin with no dependencies</span></span>

<span data-ttu-id="89a88-150">Kök klasöre geri döndüğünüzde şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="89a88-150">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="89a88-151">Adlı yeni bir sınıf kitaplığı projesi oluşturmak için aşağıdaki komutu çalıştırın `HelloPlugin` :</span><span class="sxs-lookup"><span data-stu-id="89a88-151">Run the following command to create a new class library project named `HelloPlugin`:</span></span>

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="89a88-152">Projeyi çözüme eklemek için aşağıdaki komutu çalıştırın `AppWithPlugin` :</span><span class="sxs-lookup"><span data-stu-id="89a88-152">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="89a88-153">*Merhaba Plugin/SınıfAdı. cs* dosyasını, aşağıdaki Içeriğe sahip *Merhaba komut. cs* adlı bir dosyayla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="89a88-153">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="89a88-154">Şimdi, *Helloplugin. csproj* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="89a88-154">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="89a88-155">Şunun gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="89a88-155">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net5</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="89a88-156">`<Project>`Etiketler arasında, aşağıdaki öğeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89a88-156">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

<span data-ttu-id="89a88-157">`<Private>false</Private>`Öğesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="89a88-157">The `<Private>false</Private>` element is important.</span></span> <span data-ttu-id="89a88-158">Bu, MSBuild eklentisinin çıkış dizinine *PluginBase.dll* kopyalamamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="89a88-158">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="89a88-159">*PluginBase.dll* derlemesi çıkış dizininde varsa, `PluginLoadContext` derlemeyi bulur ve *HelloPlugin.dll* derlemesini yüklediğinde yükler.</span><span class="sxs-lookup"><span data-stu-id="89a88-159">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="89a88-160">Bu noktada, `HelloPlugin.HelloCommand` tür `ICommand` arabirimi  `HelloPlugin` `ICommand` varsayılan yükleme bağlamına yüklenen arabirimi değil, projenin çıkış dizinindekiPluginBase.dlluygular.</span><span class="sxs-lookup"><span data-stu-id="89a88-160">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="89a88-161">Çalışma zamanı bu iki türü farklı derlemelerden farklı türler olarak gördüğünden, `AppWithPlugin.Program.CreateCommands` Yöntem komutları bulamaz.</span><span class="sxs-lookup"><span data-stu-id="89a88-161">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method won't find the commands.</span></span> <span data-ttu-id="89a88-162">Sonuç olarak, `<Private>false</Private>` eklenti arabirimlerini içeren derlemeye başvuru için meta veriler gerekir.</span><span class="sxs-lookup"><span data-stu-id="89a88-162">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="89a88-163">Benzer şekilde, `<ExcludeAssets>runtime</ExcludeAssets>` diğer paketlere başvuruyorsa öğesi de önemlidir `PluginBase` .</span><span class="sxs-lookup"><span data-stu-id="89a88-163">Similarly, the `<ExcludeAssets>runtime</ExcludeAssets>` element is also important if the `PluginBase` references other packages.</span></span> <span data-ttu-id="89a88-164">Bu ayar, ile aynı etkiye sahiptir, `<Private>false</Private>` ancak `PluginBase` Proje veya bağımlılıklarından birinin dahil olabileceği paket başvuruları üzerinde de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="89a88-164">This setting has the same effect as `<Private>false</Private>` but works on package references that the `PluginBase` project or one of its dependencies may include.</span></span>

<span data-ttu-id="89a88-165">`HelloPlugin`Proje tamamlandığına göre, `AppWithPlugin` eklentinin nerede bulunabileceğinizi bilmesi için projeyi güncelleştirmeniz gerekir `HelloPlugin` .</span><span class="sxs-lookup"><span data-stu-id="89a88-165">Now that the `HelloPlugin` project is complete, you should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="89a88-166">Açıklamadan sonra `// Paths to plugins to load` , `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` Array öğesi olarak ekleyin (Bu yol, kullandığınız .NET Core sürümüne göre farklı olabilir) `pluginPaths` .</span><span class="sxs-lookup"><span data-stu-id="89a88-166">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` (this path could be different based on the .NET Core version you use) as an element of the `pluginPaths` array.</span></span>

## <a name="plugin-with-library-dependencies"></a><span data-ttu-id="89a88-167">Kitaplık bağımlılıkları olan eklenti</span><span class="sxs-lookup"><span data-stu-id="89a88-167">Plugin with library dependencies</span></span>

<span data-ttu-id="89a88-168">Neredeyse tüm eklentiler basit bir "Merhaba Dünya" öğesinden daha karmaşıktır ve birçok eklenti diğer kitaplıklara bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="89a88-168">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="89a88-169">`JsonPlugin`Örnekteki ve `OldJson` eklenti projeleri üzerinde NuGet paketi bağımlılıklarını içeren iki eklenti örneği gösterir `Newtonsoft.Json` .</span><span class="sxs-lookup"><span data-stu-id="89a88-169">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="89a88-170">Proje dosyaları, proje başvuruları için özel bilgilere sahip değildir ve (eklenti yolları diziye eklendikten sonra `pluginPaths` ) Eklentiler, AppWithPlugin uygulamasının yürütülmesi halinde çalıştırılsa bile kusursuz bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="89a88-170">The project files themselves don't have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="89a88-171">Ancak, bu projeler başvurulan derlemeleri çıkış dizinine kopyalamadıkları için, eklentilerin çalışması için kullanıcının makinesinde derlemelerin mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="89a88-171">However, these projects don't copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="89a88-172">Bu sorunu geçici olarak çözmek için iki yol vardır.</span><span class="sxs-lookup"><span data-stu-id="89a88-172">There are two ways to work around this problem.</span></span> <span data-ttu-id="89a88-173">İlk seçenek, `dotnet publish` sınıf kitaplığını yayımlamak için komutunu kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="89a88-173">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="89a88-174">Alternatif olarak, eklenti için çıkışını kullanmak istiyorsanız `dotnet build` , eklentinin `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` `<PropertyGroup>` Proje dosyasındaki Etiketler arasına özelliği ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89a88-174">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="89a88-175">`XcopyablePlugin`Örnek için bkz. eklenti projesi.</span><span class="sxs-lookup"><span data-stu-id="89a88-175">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-examples-in-the-sample"></a><span data-ttu-id="89a88-176">Örnekteki diğer örnekler</span><span class="sxs-lookup"><span data-stu-id="89a88-176">Other examples in the sample</span></span>

<span data-ttu-id="89a88-177">Bu öğreticinin tüm kaynak kodu [DotNet/Samples deposunda](https://github.com/dotnet/samples/tree/main/core/extensions/AppWithPlugin)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="89a88-177">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/main/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="89a88-178">Tamamlanan örnek, bazı davranış örneklerini içerir `AssemblyDependencyResolver` .</span><span class="sxs-lookup"><span data-stu-id="89a88-178">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="89a88-179">Örneğin, `AssemblyDependencyResolver` nesne yerel kitaplıkları ve NuGet paketlerine dahil edilen yerelleştirilmiş uydu derlemelerini de çözümleyebilir.</span><span class="sxs-lookup"><span data-stu-id="89a88-179">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="89a88-180">`UVPlugin` `FrenchPlugin` Örnekler deposunda ve bu senaryolar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="89a88-180">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a><span data-ttu-id="89a88-181">Bir NuGet paketinden eklenti arabirimine başvurma</span><span class="sxs-lookup"><span data-stu-id="89a88-181">Reference a plugin interface from a NuGet package</span></span>

<span data-ttu-id="89a88-182">Adlı bir uygulama olan, adlı NuGet paketinde tanımlanmış bir eklenti arabirimi olduğunu varsayalım `A.PluginBase` .</span><span class="sxs-lookup"><span data-stu-id="89a88-182">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="89a88-183">Eklenti projenizde pakete doğru şekilde nasıl başvurdunuz?</span><span class="sxs-lookup"><span data-stu-id="89a88-183">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="89a88-184">Proje başvuruları için, `<Private>false</Private>` `ProjectReference` Proje dosyasındaki öğesindeki meta verilerin kullanılması dll 'nin çıkışa kopyalanmasını engelledi.</span><span class="sxs-lookup"><span data-stu-id="89a88-184">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="89a88-185">Pakete doğru bir şekilde başvurmak için `A.PluginBase` `<PackageReference>` Proje dosyasındaki öğeyi şu şekilde değiştirmek istersiniz:</span><span class="sxs-lookup"><span data-stu-id="89a88-185">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="89a88-186">Bu, `A.PluginBase` derlemelerin eklentinin çıkış dizinine kopyalanmasını engeller ve eklenti 'un bir sürümünü kullanmasını sağlar `A.PluginBase` .</span><span class="sxs-lookup"><span data-stu-id="89a88-186">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="89a88-187">Eklenti hedef Framework önerileri</span><span class="sxs-lookup"><span data-stu-id="89a88-187">Plugin target framework recommendations</span></span>

<span data-ttu-id="89a88-188">Eklenti bağımlılık yüklemesi dosyadaki *.deps.js* kullandığından, eklentinin hedef çerçevesiyle ilgili bir Gotcha vardır.</span><span class="sxs-lookup"><span data-stu-id="89a88-188">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="89a88-189">Özellikle, eklentilerinizin bir .NET Standard sürümü yerine .NET 5 gibi bir çalışma zamanını hedeflemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="89a88-189">Specifically, your plugins should target a runtime, such as .NET 5, instead of a version of .NET Standard.</span></span> <span data-ttu-id="89a88-190">Dosya *.deps.js* , projenin hedeflediği çerçeveye göre oluşturulur ve birçok .NET Standard uyumlu paket, belirli çalışma zamanları için .NET Standard ve uygulama derlemelerinin oluşturulmasına yönelik başvuru derlemeleri gönderdiğinden, *üzerinde.deps.js* uygulama derlemelerini doğru şekilde göremeyebilir ya da istediğiniz .NET Core sürümü yerine bir derlemenin .NET Standard sürümünü alabilir.</span><span class="sxs-lookup"><span data-stu-id="89a88-190">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>

## <a name="plugin-framework-references"></a><span data-ttu-id="89a88-191">Eklenti çerçevesi başvuruları</span><span class="sxs-lookup"><span data-stu-id="89a88-191">Plugin framework references</span></span>

<span data-ttu-id="89a88-192">Şu anda, eklentiler işleme yeni çerçeveler sunmaz.</span><span class="sxs-lookup"><span data-stu-id="89a88-192">Currently, plugins can't introduce new frameworks into the process.</span></span> <span data-ttu-id="89a88-193">Örneğin, Framework kullanan bir eklentiyi `Microsoft.AspNetCore.App` yalnızca kök Framework kullanan bir uygulamaya yükleyebilirsiniz `Microsoft.NETCore.App` .</span><span class="sxs-lookup"><span data-stu-id="89a88-193">For example, you can't load a plugin that uses the `Microsoft.AspNetCore.App` framework into an application that only uses the root `Microsoft.NETCore.App` framework.</span></span> <span data-ttu-id="89a88-194">Konak uygulama, eklentiler tarafından ihtiyaç duyulan tüm çerçevelere başvuruları bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="89a88-194">The host application must declare references to all frameworks needed by plugins.</span></span>
