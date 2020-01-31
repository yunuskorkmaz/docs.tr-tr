---
title: Eklentilerle .NET Core uygulaması oluşturma
description: Eklentileri destekleyen bir .NET Core uygulaması oluşturmayı öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: 32205a507bc95b2f8a2f75368aab3fde710249ee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787848"
---
# <a name="create-a-net-core-application-with-plugins"></a>Eklentilerle .NET Core uygulaması oluşturma

Bu öğreticide, eklentileri yüklemek için özel bir <xref:System.Runtime.Loader.AssemblyLoadContext> nasıl oluşturacağınız gösterilmektedir. <xref:System.Runtime.Loader.AssemblyDependencyResolver>, eklentinin bağımlılıklarını çözümlemek için kullanılır. Öğretici, eklentinin bağımlılıklarını barındırma uygulamasından doğru şekilde yalıtır. Şunları yapmayı öğreneceksiniz:

- Eklentileri desteklemek için bir proje yapısı yapın.
- Her eklentiyi yüklemek için özel bir <xref:System.Runtime.Loader.AssemblyLoadContext> oluşturun.
- Eklentilerin bağımlılıklara sahip olmasını sağlamak için <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> türünü kullanın.
- Yalnızca derleme yapıtları kopyalanarak kolayca dağıtılabilecek olan eklentileri yazar.

## <a name="prerequisites"></a>Prerequisites

- [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download) veya daha yeni bir sürümünü yükler.

## <a name="create-the-application"></a>Uygulama oluşturma

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

Projenin kök klasöründe `dotnet new classlib -o PluginBase`' yi çalıştırın. Ayrıca, projeyi çözüm dosyasına eklemek için `dotnet sln add PluginBase/PluginBase.csproj` çalıştırın. `PluginBase/Class1.cs` dosyasını silin ve aşağıdaki arabirim tanımıyla `ICommand.cs` adlı `PluginBase` klasörde yeni bir dosya oluşturun:

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

Bu `ICommand` arabirimi, tüm eklentilerin uygulayamayacağı arabirimdir.

`ICommand` arabirimi tanımlandığına göre, uygulama projesi biraz daha fazla doldurulabilir. Kök klasörden `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` komutuyla `AppWithPlugin` projesinden `PluginBase` projesine bir başvuru ekleyin.

`// Load commands from plugins` açıklamasını, belirtilen dosya yollarından eklentileri yüklemesini etkinleştirmek için aşağıdaki kod parçacığı ile değiştirin:

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

Sonra `// Output the loaded commands` açıklamasını aşağıdaki kod parçacığı ile değiştirin:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

`// Execute the command with the name passed as an argument` açıklamasını aşağıdaki kod parçacığıyla değiştirin:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

Son olarak, burada gösterildiği gibi, `LoadPlugin` ve `CreateCommands`adlı `Program` sınıfa statik yöntemler ekleyin:

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

Artık uygulama yüklenen eklenti derlemelerinden komutları doğru bir şekilde yükleyebilir ve örneklendirilecek, ancak hala eklenti derlemelerini yükleyemeyebilir. *Appwithplugin* klasöründe aşağıdaki içeriğe sahip *PluginLoadContext.cs* adlı bir dosya oluşturun:

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

`PluginLoadContext` türü <xref:System.Runtime.Loader.AssemblyLoadContext>türetilir. `AssemblyLoadContext` türü, geliştiricilerin, derleme sürümlerinin çakışmadığından emin olmak için yüklü derlemeleri farklı gruplara yalıtmalarına olanak tanıyan özel bir türdür. Ayrıca, özel bir `AssemblyLoadContext` derlemeleri yüklemek için farklı yollar seçebilir ve varsayılan davranışı geçersiz kılabilir. `PluginLoadContext`, derleme adlarını yollara çözümlemek için .NET Core 3,0 ' de tanıtılan `AssemblyDependencyResolver` türünün bir örneğini kullanır. `AssemblyDependencyResolver` nesnesi, .NET sınıf kitaplığı yoluyla oluşturulur. Yol `AssemblyDependencyResolver` oluşturucusuna geçilen sınıf kitaplığı için *. Deps. JSON* dosyasını temel alan derlemeleri ve yerel kitaplıkları göreli yollarına çözümler. Özel `AssemblyLoadContext`, eklentilerin kendi bağımlılıklarına sahip olmasını sağlar ve `AssemblyDependencyResolver` bağımlılıkları doğru şekilde yüklemeyi kolaylaştırır.

Artık `AppWithPlugin` projesi `PluginLoadContext` türüne sahip olduğuna göre `Program.LoadPlugin` yöntemini aşağıdaki gövdele güncelleştirin:

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

## <a name="simple-plugin-with-no-dependencies"></a>Bağımlılıkları olmayan basit eklenti

Kök klasöre geri döndüğünüzde şunları yapın:

1. `HelloPlugin`adlı yeni bir sınıf kitaplığı projesi oluşturmak için aşağıdaki komutu çalıştırın:
    
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

`<Project>` etiketleri arasında, aşağıdaki öğeleri ekleyin:

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

`<Private>false</Private>` öğesi önemlidir. Bu, MSBuild 'in *Pluginbase. dll dosyasını* helloplugin çıkış dizinine kopyalamamasını söyler. Eğer *Pluginbase. dll* derlemesi çıkış dizininde mevcutsa, `PluginLoadContext` derlemeyi bulur ve *Merhaba Plugin. dll* derlemesini yüklediğinde yükler. Bu noktada, `HelloPlugin.HelloCommand` türü, varsayılan yükleme bağlamına yüklenen `ICommand` arabirimini değil, `HelloPlugin` projenin çıkış dizinindeki *Pluginbase. dll* ' den `ICommand` arabirimini uygular. Çalışma zamanı bu iki türü farklı derlemelerden farklı türler olarak gördüğü için `AppWithPlugin.Program.CreateCommands` yöntemi komutları bulamaz. Sonuç olarak, eklenti arabirimlerini içeren derlemeye başvuru için `<Private>false</Private>` meta verileri gereklidir.

Benzer şekilde, `PluginBase` başka paketlere başvuruyorsa `<ExcludeAssets>runtime</ExcludeAssets>` öğesi de önemlidir. Bu ayar `<Private>false</Private>` ile aynı etkiye sahiptir, ancak paket başvuruları üzerinde, `PluginBase` projesi veya bağımlılıklarından biri dahil olabilir.

`HelloPlugin` proje tamamlandığına göre, `HelloPlugin` eklentisinin nerede bulunabileceğinizi bildirmek için `AppWithPlugin` projesini güncelleştirmeniz gerekir. `// Paths to plugins to load` açıklamasıyla sonra, `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` `pluginPaths` dizisinin bir öğesi olarak ekleyin.

## <a name="plugin-with-library-dependencies"></a>Kitaplık bağımlılıkları olan eklenti

Neredeyse tüm eklentiler basit bir "Merhaba Dünya" öğesinden daha karmaşıktır ve birçok eklenti diğer kitaplıklara bağımlılıkları vardır. Örnekteki `JsonPlugin` ve `OldJson` eklenti projeleri, `Newtonsoft.Json`NuGet paketi bağımlılıklarını içeren eklentilerin iki örneğini gösterir. Proje dosyaları, proje başvuruları için özel bilgilere sahip değildir ve (`pluginPaths` dizisine eklenti yolları eklendikten sonra), Eklentiler, AppWithPlugin uygulamasının yürütülmesi halinde çalıştırılsa bile kusursuz bir şekilde çalışır. Ancak, bu projeler başvurulan derlemeleri çıkış dizinine kopyalamadıkları için, eklentilerin çalışması için kullanıcının makinesinde derlemelerin mevcut olması gerekir. Bu sorunu geçici olarak çözmek için iki yol vardır. İlk seçenek, sınıf kitaplığını yayımlamak için `dotnet publish` komutunu kullanmaktır. Alternatif olarak, eklenti için `dotnet build` çıkışını kullanmak istiyorsanız, eklentinin proje dosyasındaki `<PropertyGroup>` etiketleri arasına `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` özelliğini ekleyebilirsiniz. Örnek için `XcopyablePlugin` eklentisi projesine bakın.

## <a name="other-examples-in-the-sample"></a>Örnekteki diğer örnekler

Bu öğreticinin tüm kaynak kodu [DotNet/Samples deposunda](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin)bulunabilir. Tamamlanan örnek `AssemblyDependencyResolver` davranışın diğer birkaç örneğini içerir. Örneğin, `AssemblyDependencyResolver` nesnesi yerel kitaplıkların yanı sıra NuGet paketlerine dahil edilen yerelleştirilmiş uydu derlemelerini de çözümleyebilir. Örnekler deposundaki `UVPlugin` ve `FrenchPlugin` bu senaryoları gösterir.

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a>Bir NuGet paketinden eklenti arabirimine başvurma

`A.PluginBase`adlı NuGet paketinde tanımlanmış bir eklenti arabirimine sahip bir uygulama olduğunu varsayalım. Eklenti projenizde pakete doğru şekilde nasıl başvurdunuz? Proje başvuruları için, proje dosyasındaki `ProjectReference` öğesindeki `<Private>false</Private>` meta verilerini kullanmak dll 'nin çıkışa kopyalanmasını engelledi.

`A.PluginBase` paketine doğru bir şekilde başvurmak için, proje dosyasındaki `<PackageReference>` öğesini şu şekilde değiştirmek istersiniz:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Bu, `A.PluginBase` derlemelerin eklentinin çıkış dizinine kopyalanmasını önler ve bu eklentinin `A.PluginBase`bir sürümünü kullanmasını sağlar.

## <a name="plugin-target-framework-recommendations"></a>Eklenti hedef Framework önerileri

Eklenti bağımlılık yüklemesi *. Deps. JSON* dosyasını kullandığından, eklentinin hedef çerçevesiyle ilgili bir Gotcha vardır. Özellikle, eklentilerinizin bir .NET Standard sürümü yerine .NET Core 3,0 gibi bir çalışma zamanını hedeflemesi gerekir. *. Deps. JSON* dosyası, projenin hedeflediği çerçeveye göre oluşturulur ve birçok .NET Standard uyumlu paket, belirli çalışma zamanları için .NET Standard ve uygulama derlemelerinin oluşturulmasına yönelik başvuru derlemeleri sunduğundan, *. Deps. JSON* uygulama derlemelerini doğru şekilde göremez veya istediğiniz .NET Core sürümü yerine bir derlemenin .NET Standard sürümünü alabilir.

## <a name="plugin-framework-references"></a>Eklenti çerçevesi başvuruları

Şu anda, eklentiler işleme yeni çerçeveler sunmaz. Örneğin, `Microsoft.AspNetCore.App` çerçevesini kullanan bir eklentiyi yalnızca kök `Microsoft.NETCore.App` çerçevesini kullanan bir uygulamaya yükleyebilirsiniz. Konak uygulama, eklentiler tarafından ihtiyaç duyulan tüm çerçevelere başvuruları bildirmelidir.
