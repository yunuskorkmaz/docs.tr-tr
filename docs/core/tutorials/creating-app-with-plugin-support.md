---
title: Eklentilerle .NET Core uygulaması oluşturma
description: Eklentileri destekleyen bir .NET Core uygulaması oluşturmayı öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: 54f616a7b2b20b7682963e9f5d503878bb512c90
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250169"
---
# <a name="create-a-net-core-application-with-plugins"></a>Eklentilerle .NET Core uygulaması oluşturma

Bu öğreticide nasıl yapılacağı gösterilmektedir:

- Eklentileri desteklemek için bir proje yapısı yapın.
- Her bir eklentiyi yüklemek için özel bir @no__t oluşturun-0.
- Eklentilerin bağımlılıklara sahip olmasını sağlamak için `System.Runtime.Loader.AssemblyDependencyResolver` türünü kullanın.
- Yalnızca derleme yapıtları kopyalanarak kolayca dağıtılabilecek olan eklentileri yazar.

## <a name="prerequisites"></a>Prerequisites

- [.NET Core 3,0](https://dotnet.microsoft.com/download) veya daha yeni bir sürümünü yükler.

## <a name="create-the-application"></a>Uygulamayı oluşturma

İlk adım, uygulamayı oluşturmaktır:

1. Yeni bir klasör oluşturun ve bu klasörde aşağıdaki komutu çalıştırın:

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. Projeyi daha kolay hale getirmek için aynı klasörde bir Visual Studio çözüm dosyası oluşturun. Şu komutu çalıştırın:

    ```dotnetcli
    dotnet new sln
    ```

3. Uygulama projesini çözüme eklemek için aşağıdaki komutu çalıştırın:

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

Şimdi uygulamamızın iskektlerini dolduracağız. *Appwithplugin/program. cs* dosyasındaki kodu aşağıdaki kodla değiştirin:

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

## <a name="create-the-plugin-interfaces"></a>Eklenti arabirimlerini oluşturma

Eklentilerle uygulama oluşturmanın bir sonraki adımı, eklentilerin uygulanması gereken arabirimi tanımlar. Uygulamanız ve eklentiler arasında iletişim kurmak için kullanmayı planladığınız türleri içeren bir sınıf kitaplığı almanızı öneririz. Bu bölüm, tam uygulamanızı teslim etmek zorunda kalmadan eklenti arabiriminizi bir paket olarak yayımlamanıza olanak sağlar.

Projenin kök klasöründe `dotnet new classlib -o PluginBase` ' ı çalıştırın. Ayrıca, projeyi çözüm dosyasına eklemek için `dotnet sln add PluginBase/PluginBase.csproj` ' ı çalıştırın. @No__t-0 dosyasını silin ve aşağıdaki arabirim tanımıyla `ICommand.cs` adlı `PluginBase` klasöründe yeni bir dosya oluşturun:

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

Bu `ICommand` arabirimi, tüm eklentilerin uygulayamayacağı arabirimdir.

@No__t-0 arabirimi tanımlandığına göre, uygulama projesi biraz daha fazla doldurulabilir. Kök klasördeki `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` komutuyla `AppWithPlugin` projesinden `PluginBase` projesine bir başvuru ekleyin.

@No__t-0 yorumunu, belirtilen dosya yollarından eklentileri yüklemesini etkinleştirmek için aşağıdaki kod parçacığı ile değiştirin:

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

Sonra `// Output the loaded commands` yorumunu aşağıdaki kod parçacığı ile değiştirin:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

@No__t-0 yorumunu aşağıdaki kod parçacığıyla değiştirin:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

Son olarak, burada gösterildiği gibi, `LoadPlugin` ve `CreateCommands` adlı `Program` sınıfına statik yöntemler ekleyin:

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

## <a name="load-plugins"></a>Eklentileri yükle

Artık uygulama, yüklenen eklenti derlemelerinden komutları doğru bir şekilde yükleyebilir ve örneklendirilecek, ancak hala eklenti derlemelerini yükleyemeyebilir. *Appwithplugin* klasöründe aşağıdaki içeriğe sahip *PluginLoadContext.cs* adlı bir dosya oluşturun:

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

@No__t-0 türü <xref:System.Runtime.Loader.AssemblyLoadContext> ' den türetilir. @No__t-0 türü, geliştiricilerin, derleme sürümlerinin çakışmadığından emin olmak için yüklü derlemeleri farklı gruplara yalıtmalarına olanak tanıyan özel bir türdür. Ayrıca, özel bir `AssemblyLoadContext` ' dan derlemeleri yüklemek için farklı yollar seçebilir ve varsayılan davranışı geçersiz kılabilir. @No__t-0, derleme adlarını yollara çözümlemek için .NET Core 3,0 ' de tanıtılan `AssemblyDependencyResolver` türünün bir örneğini kullanır. @No__t-0 nesnesi, .NET sınıf kitaplığı yoluyla oluşturulur. @No__t-1 oluşturucusuna geçirilen sınıf kitaplığı için *. Deps. JSON* dosyasını temel alan derlemeleri ve yerel kitaplıkları göreli yollarına çözümler. Özel `AssemblyLoadContext`, eklentilerin kendi bağımlılıklarına sahip olmasını sağlar ve `AssemblyDependencyResolver` bağımlılıkları doğru şekilde yüklemeyi kolaylaştırır.

@No__t-0 projesinde `PluginLoadContext` türü olduğuna göre, `Program.LoadPlugin` yöntemini aşağıdaki gövdele güncelleştirin:

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

Her eklenti için farklı bir `PluginLoadContext` örneği kullanarak, Eklentiler, sorun olmadan farklı veya hatta çakışan bağımlılıklara sahip olabilir.

## <a name="create-a-simple-plugin-with-no-dependencies"></a>Bağımlılıkları olmayan basit bir eklenti oluşturma

Kök klasöre geri döndüğünüzde şunları yapın:

1. @No__t-0 adlı yeni bir sınıf kitaplığı projesi oluşturmak için aşağıdaki komutu çalıştırın:
    
    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. Projeyi `AppWithPlugin` çözümüne eklemek için aşağıdaki komutu çalıştırın:

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. *Merhaba Plugin/Class1. cs* dosyasını aşağıdaki içeriklerle *HelloCommand.cs* adlı bir dosyayla değiştirin:

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

Şimdi, *Helloplugin. csproj* dosyasını açın. Şuna benzer olmalıdır:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

@No__t-0 etiketleri arasında, aşağıdaki öğeleri ekleyin:

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

@No__t-0 öğesi çok önemlidir. Bu, MSBuild 'in *Pluginbase. dll dosyasını* helloplugin çıkış dizinine kopyalamamasını söyler. Eğer *Pluginbase. dll* derlemesi çıkış dizininde mevcutsa, `PluginLoadContext` derlemeyi bulur ve *helloplugin. dll* derlemesini yüklediğinde yükler. Bu noktada `HelloPlugin.HelloCommand` türü, varsayılan yükleme bağlamına yüklenen `ICommand` arabirimine değil, `HelloPlugin` projesinin çıkış dizinindeki *Pluginbase. dll* ' den `ICommand` arabirimini uygular. Çalışma zamanı bu iki türü farklı derlemelerden farklı türler olarak gördüğü için `AppWithPlugin.Program.CreateCommands` yöntemi komutları bulamaz. Sonuç olarak, eklenti arabirimlerini içeren derlemeye başvuru için `<Private>false</Private>` meta verisi gereklidir.

@No__t-0 projesi tamamlandığına göre, @no__t 2 eklentisinin nerede bulunabileceğinizi bildirmek için `AppWithPlugin` projesini güncelleştirdik. @No__t-0 açıklamasıyla sonra, `pluginPaths` dizisinin bir öğesi olarak `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` ekleyin.

## <a name="create-a-plugin-with-library-dependencies"></a>Kitaplık bağımlılıklarıyla eklenti oluşturma

Neredeyse tüm eklentiler basit bir "Merhaba Dünya" öğesinden daha karmaşıktır ve birçok eklenti diğer kitaplıklara bağımlılıkları vardır. Örnekteki `JsonPlugin` ve `OldJson` eklenti projeleri, `Newtonsoft.Json` ' de NuGet paketi bağımlılıkları olan eklentilerin iki örneğini gösterir. Proje dosyaları, proje başvuruları için özel bilgilere sahip değildir ve (`pluginPaths` dizisine eklenti yolları eklendikten sonra) Eklentiler, AppWithPlugin uygulamasının yürütmesinde çalıştırılsa bile kusursuz bir şekilde çalışır. Ancak, bu projeler başvurulan derlemeleri çıkış dizinine kopyalamadıkları için, eklentilerin çalışması için kullanıcının makinesinde derlemelerin mevcut olması gerekir. Bu sorunu geçici olarak çözmek için iki yol vardır. İlk seçenek, sınıf kitaplığını yayımlamak için `dotnet publish` komutunu kullanmaktır. Alternatif olarak, eklenti için `dotnet build` çıktısını kullanmak istiyorsanız, eklentinin proje dosyasındaki `<PropertyGroup>` etiketleri arasına `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` özelliğini ekleyebilirsiniz. Örnek için `XcopyablePlugin` eklenti projesine bakın.

## <a name="other-plugin-examples-in-the-sample"></a>Örnekteki diğer eklenti örnekleri

Bu öğreticinin tüm kaynak kodu [DotNet/Samples deposunda](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin)bulunabilir. Tamamlanan örnek, `AssemblyDependencyResolver` davranışından oluşan diğer örnekleri içerir. Örneğin, `AssemblyDependencyResolver` nesnesi yerel kitaplıkları ve NuGet paketlerine dahil edilen yerelleştirilmiş uydu derlemelerini de çözümleyebilir. Örnek deposundaki `UVPlugin` ve `FrenchPlugin` bu senaryoları gösterir.

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a>NuGet paketinde tanımlanan eklenti arabirimi derlemesine başvurma

@No__t-0 adlı NuGet paketinde tanımlanmış bir eklenti arabirimine sahip bir uygulama olduğunu varsayalım. Eklenti projenizde pakete doğru şekilde nasıl başvurdunuz? Proje başvuruları için proje dosyasındaki `ProjectReference` öğesindeki `<Private>false</Private>` meta verisinin kullanılması dll 'nin çıkışa kopyalanmasını engelledi.

@No__t-0 paketine doğru bir şekilde başvurmak için, proje dosyasındaki `<PackageReference>` öğesini şu şekilde değiştirmek istersiniz:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Bu, `A.PluginBase` derlemelerinin, eklentinin çıkış dizinine kopyalanmasını önler ve bu eklentinin `A.PluginBase` ' in bir sürümünü kullanmasını sağlar.

## <a name="plugin-target-framework-recommendations"></a>Eklenti hedef Framework önerileri

Eklenti bağımlılık yüklemesi *. Deps. JSON* dosyasını kullandığından, eklentinin hedef çerçevesiyle ilgili bir Gotcha vardır. Özellikle, eklentilerinizin bir .NET Standard sürümü yerine .NET Core 3,0 gibi bir çalışma zamanını hedeflemesi gerekir. *. Deps. JSON* dosyası, projenin hedeflediği çerçeveye göre oluşturulur ve birçok .NET Standard uyumlu paket, belirli çalışma zamanları için .NET Standard ve uygulama derlemelerinin oluşturulmasına yönelik başvuru derlemeleri sunduğundan, *. Deps. JSON* uygulama derlemelerini doğru görmeyebilir veya Istediğiniz .NET Core sürümü yerine bir derlemenin .NET Standard sürümünü alabilir.
