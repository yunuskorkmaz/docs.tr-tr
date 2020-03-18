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
# <a name="create-a-net-core-application-with-plugins"></a>Eklentilerle .NET Core uygulaması oluşturma

Bu öğretici, eklentileri yüklemek <xref:System.Runtime.Loader.AssemblyLoadContext> için özel bir oluşturmak için nasıl gösterir. A, <xref:System.Runtime.Loader.AssemblyDependencyResolver> eklentinin bağımlılıklarını gidermek için kullanılır. Öğretici, eklentinin bağımlılıklarını barındırma uygulamasından doğru bir şekilde yalıtır. Şunları öğrenirsiniz:

- Eklentileri desteklemek için bir proje yapıla.
- Her eklentiyi yüklemek için özel <xref:System.Runtime.Loader.AssemblyLoadContext> bir resim oluşturun.
- Eklentilerin <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> bağımlılıkları olması için türü kullanın.
- Yapı yapılarını kopyalayarak kolayca dağıtılabilen yazar eklentileri.

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 3.0 SDK'yı](https://dotnet.microsoft.com/download) veya daha yeni bir sürümü yükleyin.

## <a name="create-the-application"></a>Uygulama oluşturma

İlk adım, uygulamayı oluşturmaktır:

1. Yeni bir klasör oluşturun ve bu klasörde aşağıdaki komutu çalıştırın:

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. Projeyi oluşturmayı kolaylaştırmak için aynı klasörde bir Visual Studio çözüm dosyası oluşturun. Şu komutu çalıştırın:

    ```dotnetcli
    dotnet new sln
    ```

3. Uygulama projesini çözüme eklemek için aşağıdaki komutu çalıştırın:

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

Şimdi başvurumuzun iskeletini doldurabiliriz. *AppWithPlugin/Program.cs* dosyasındaki kodu aşağıdaki kodla değiştirin:

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

## <a name="create-the-plugin-interfaces"></a>Eklenti arayüzlerini oluşturma

Eklentileri ile bir uygulama oluşturmada bir sonraki adım eklentileri uygulamak için gereken arayüzü tanımlamaktır. Uygulamanız ve eklentileriniz arasında iletişim kurmak için kullanmayı planladığınız türleri içeren bir sınıf kitaplığı oluşturmanızı öneririz. Bu bölüm, tam uygulamanızı göndermenize gerek kalmadan eklenti arabiriminizi paket olarak yayımlamanızı sağlar.

Projenin kök klasöründe çalıştırın. `dotnet new classlib -o PluginBase` Ayrıca, `dotnet sln add PluginBase/PluginBase.csproj` projeyi çözüm dosyasına eklemek için çalıştırın. Dosyayı `PluginBase/Class1.cs` silin ve aşağıdaki arabirim `PluginBase` tanımıyla birlikte adlı `ICommand.cs` klasörde yeni bir dosya oluşturun:

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

Bu `ICommand` arabirim, tüm eklentilerin uygulayacağı arabirimdir.

Artık `ICommand` arabirim tanımlandığına göre, uygulama projesi biraz daha doldurulabilir. Kök klasöründen `AppWithPlugin` `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` komutla `PluginBase` projeye bir başvuru ekleyin.

Belirli `// Load commands from plugins` dosya yollarından eklentileri yükleyebilmek için yorumu aşağıdaki kod parçacıklarıyla değiştirin:

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

Ardından `// Output the loaded commands` yorumu aşağıdaki kod parçacıklarıyla değiştirin:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

`// Execute the command with the name passed as an argument` Yorumu aşağıdaki parçacıkla değiştirin:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

Ve son olarak, burada `Program` gösterildiği `LoadPlugin` `CreateCommands`gibi adlı sınıfa statik yöntemler ekleyin:

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

## <a name="load-plugins"></a>Yük eklentileri

Artık uygulama, yüklü eklenti montajlarından komutları doğru bir şekilde yükleyebilir ve anında atabiliyor, ancak yine de eklenti montajlarını yükleyemiyor. *AppWithPlugin* klasöründe aşağıdaki içerikleri içeren *PluginLoadContext.cs* adlı bir dosya oluşturun:

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

Türü `PluginLoadContext` nden <xref:System.Runtime.Loader.AssemblyLoadContext>türetilmiştir. Tür, `AssemblyLoadContext` çalışma zamanında geliştiricilerin yüklü derlemeleri derleme sürümlerinin çakışmaması için farklı gruplara ayırmasına olanak tanıyan özel bir türdür. Ayrıca, bir `AssemblyLoadContext` özel gelen derlemeleri yüklemek ve varsayılan davranışı geçersiz kılmak için farklı yollar seçebilirsiniz. Derleme `PluginLoadContext` adlarını yollara çözümlemek için .NET Core 3.0'da tanıtılan `AssemblyDependencyResolver` türün bir örneğini kullanır. Nesne `AssemblyDependencyResolver` ,NET sınıf kitaplığına giden yol ile oluşturulur. Derlemeleri ve yerel kitaplıkları, yolu `AssemblyDependencyResolver` oluşturucuya geçirilen sınıf kitaplığı için *.deps.json* dosyasına göre göreli yollarına giderir. Özel, `AssemblyLoadContext` eklentilerin kendi bağımlılıklarına sahip olmasını sağlar `AssemblyDependencyResolver` ve bağımlılıkları doğru şekilde yüklemeyi kolaylaştırır.

Artık `AppWithPlugin` proje `PluginLoadContext` türüne sahip olduğuna `Program.LoadPlugin` göre, yöntemi aşağıdaki gövdeyle güncelleştirin:

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

Her eklenti `PluginLoadContext` için farklı bir örnek kullanarak, eklentileri sorun olmadan farklı ve hatta çakışan bağımlılıklar olabilir.

## <a name="simple-plugin-with-no-dependencies"></a>Bağımlılık olmadan basit eklenti

Kök klasöründe aşağıdakileri yapın:

1. Adlı yeni bir sınıf kitaplığı projesi `HelloPlugin`oluşturmak için aşağıdaki komutu çalıştırın:

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. Projeyi çözüme eklemek için `AppWithPlugin` aşağıdaki komutu çalıştırın:

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. *HelloPlugin/Class1.cs* dosyasını aşağıdaki içeriklerle *HelloCommand.cs* adlı bir dosyayla değiştirin:

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

Şimdi, *HelloPlugin.csproj* dosyasını açın. Şunun gibi görünmelidir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

Etiketlerin `<Project>` arasına aşağıdaki öğeleri ekleyin:

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

Öğe `<Private>false</Private>` önemlidir. Bu, MSBuild'e HelloPlugin'in çıktı dizini için *PluginBase.dll* kopyalamamasını söyler. *PluginBase.dll* derlemesi çıkış dizininde mevcutsa, `PluginLoadContext` montajı orada bulur ve *HelloPlugin.dll* derlemesini yüklerken yükler. Bu noktada, `HelloPlugin.HelloCommand` tür, varsayılan `ICommand` yük bağlamına yüklenen `HelloPlugin` `ICommand` arabirimyerine, projenin çıktı dizinindeki *PluginBase.dll'deki* arabirimi uygular. Çalışma zamanı bu iki türü farklı derlemelerden farklı `AppWithPlugin.Program.CreateCommands` türler olarak gördüğünden, yöntem komutları bulamaz. Sonuç olarak, `<Private>false</Private>` meta veri eklenti arabirimleri içeren derleme başvuru için gereklidir.

Benzer şekilde, `<ExcludeAssets>runtime</ExcludeAssets>` diğer paketlere `PluginBase` başvuruyorsa, öğe de önemlidir. Bu ayar, proje `<Private>false</Private>` veya bağımlılıklarından birinin `PluginBase` içerebileceği paket başvurularıyla aynı etkiye sahiptir.

`HelloPlugin` Proje tamamlandığından, `HelloPlugin` eklentinin nerede bulunabileceğini bilmek için projeyi `AppWithPlugin` güncelleştirmeniz gerekir. Açıklamadan `// Paths to plugins to load` sonra, `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` `pluginPaths` dizinin bir öğesi olarak ekleyin.

## <a name="plugin-with-library-dependencies"></a>Kitaplık bağımlılıkları ile eklenti

Hemen hemen tüm eklentileri basit bir "Hello World" daha karmaşık ve birçok eklentileri diğer kütüphaneler üzerinde bağımlılıkları vardır. `JsonPlugin` Örnekteki `OldJson` ve eklenti projeleri, NuGet paket bağımlılıkları olan eklentilerin `Newtonsoft.Json`iki örneğini gösterir. Proje dosyalarının proje başvuruları için özel bir bilgisi yoktur ve `pluginPaths` (diziye eklenti yollarını ekledikten sonra) eklentiler AppWithPlugin uygulamasının aynı yürütülmesinde çalıştırılsa bile mükemmel çalışır. Ancak, bu projeler başvurulan derlemeleri çıktı diziniiçin kopyalamaz, bu nedenle eklentilerin çalışması için derlemelerin kullanıcının makinesinde bulunması gerekir. Bu sorunu aşmanın iki yolu vardır. İlk seçenek, sınıf `dotnet publish` kitaplığını yayımlamak için komutu kullanmaktır. Alternatif olarak, eklentiniz `dotnet build` için çıktıyı kullanabilmek istiyorsanız, özelliği eklentinin `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` proje `<PropertyGroup>` dosyasındaki etiketler arasına ekleyebilirsiniz. Örnek `XcopyablePlugin` olarak eklenti projesine bakın.

## <a name="other-examples-in-the-sample"></a>Örnekteki diğer örnekler

Bu öğretici için tam kaynak kodu [dotnet / örnek deposunda](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin)bulunabilir. Tamamlanan örnek, birkaç davranış `AssemblyDependencyResolver` örneği daha içerir. Örneğin, `AssemblyDependencyResolver` nesne yerel kitaplıkları ve NuGet paketlerinde yer alan yerelleştirilmiş uydu derlemelerini de çözebilir. Örnek `UVPlugin` `FrenchPlugin` deposunda ve depoda bu senaryoları gösterir.

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a>NuGet paketinden bir eklenti arabirimine başvurun

NuGet paketinde tanımlanan bir eklenti arabirimi olan bir uygulama A `A.PluginBase`olduğunu varsayalım. Eklenti projenizde paketi nasıl doğru bir şekilde başvurursunuz? Proje başvuruları için, `<Private>false</Private>` proje dosyasındaki `ProjectReference` öğedeki meta verileri kullanmak dll'nin çıktıya kopyalanmasını engelledi.

`A.PluginBase` Paketi doğru bir şekilde başvurmak için `<PackageReference>` proje dosyasındaki öğeyi aşağıdakiyle değiştirmek istiyorsunuz:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Bu, derlemelerin eklentinizin `A.PluginBase` çıktı dizinine kopyalanmasını önler ve eklentinizin A'nın `A.PluginBase`''nin sürümünü kullanmasını sağlar.

## <a name="plugin-target-framework-recommendations"></a>Plugin hedef çerçeve önerileri

Eklenti bağımlılığı *yüklemesi .deps.json* dosyasını kullandığından, eklentinin hedef çerçevesiyle ilgili bir gotcha vardır. Özellikle, eklentileriniz .NET Standard'ın bir sürümü yerine .NET Core 3.0 gibi bir çalışma süresini hedeflemelidir. *.deps.json* dosyası, proje hedeflerinin hangi çerçeveye göre oluşturulduğuna göre oluşturulur ve .NET Standart uyumlu birçok paket ,NET Standard ve belirli çalışma süreleri için uygulama derlemeleri karşı oluşturmak için referans derlemeleri olduğundan, *.deps.json* uygulama derlemelerini doğru göremeyebilir veya beklediğiniz .NET Core sürümü yerine bir derlemenin .NET Standart sürümünü kapabilir.

## <a name="plugin-framework-references"></a>Eklenti çerçeve referansları

Şu anda, eklentiler sürece yeni çerçeveler getiremez. Örneğin, çerçeveyi `Microsoft.AspNetCore.App` kullanan bir eklentiyi yalnızca kök `Microsoft.NETCore.App` çerçeveyi kullanan bir uygulamaya yükleyemezsiniz. Ana bilgisayar uygulaması, eklentilerin ihtiyaç duyduğu tüm çerçevelere başvuru bildirmelidir.
