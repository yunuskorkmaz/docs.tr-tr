---
title: Eklentilerle .NET Core uygulaması oluşturma
description: Eklentileri destekleyen bir .NET Core uygulaması oluşturmayı öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: 308fd2f853261e87da71892c42e17e36984d1978
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68330984"
---
# <a name="create-a-net-core-application-with-plugins"></a>Eklentilerle .NET Core uygulaması oluşturma

Bu öğreticide nasıl yapılacağı gösterilmektedir:

- Eklentileri desteklemek için bir proje yapısı yapın.
- Her bir eklentiyi <xref:System.Runtime.Loader.AssemblyLoadContext> yüklemek için özel oluşturun.
- Eklentilerin bağımlılıklara sahip olmasını sağlamak için türükullanın.`System.Runtime.Loader.AssemblyDependencyResolver`
- Yalnızca derleme yapıtları kopyalanarak kolayca dağıtılabilecek olan eklentileri yazar.

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 3,0 Preview 2 SDK](https://www.microsoft.com/net/core) veya daha yeni bir sürümünü yükler.

## <a name="create-the-application"></a>Uygulama oluşturma

İlk adım, uygulamayı oluşturmaktır:

1. Yeni bir klasör oluşturun ve bu klasörde ' i çalıştırın `dotnet new console -o AppWithPlugin`. 
2. Projeyi daha kolay hale getirmek için bir Visual Studio çözüm dosyası oluşturun. Aynı `dotnet new sln` klasörde çalıştırın. 
3. Uygulama `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` projesini çözüme eklemek için ' i çalıştırın.

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

Projenin kök klasöründe, öğesini çalıştırın `dotnet new classlib -o PluginBase`. Ayrıca, projeyi `dotnet sln add PluginBase/PluginBase.csproj` çözüm dosyasına eklemek için öğesini çalıştırın. Dosyayı silin ve aşağıdaki arabirim tanımıyla adlı `PluginBase` `ICommand.cs` klasörde yeni bir dosya oluşturun: `PluginBase/Class1.cs`

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

Bu `ICommand` arabirim, tüm eklentilerin uygulayamayacağı arabirimdir.

`ICommand` Arabirim tanımlandığına göre, uygulama projesi biraz daha fazla doldurulabilir. Kök klasördeki `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` komutla projeye bir `AppWithPlugin` başvuru `PluginBase` ekleyin.

Verilen dosya yollarından eklentileri yüklemesini etkinleştirmek için yorumuaşağıdakikodparçacığıiledeğiştirin:`// Load commands from plugins`

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

Sonra `// Output the loaded commands` yorumu aşağıdaki kod parçacığı ile değiştirin:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

`// Execute the command with the name passed as an argument` Yorumu aşağıdaki kod parçacığıyla değiştirin:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

Son olarak, burada gösterildiği gibi, ve `Program` `CreateCommands`adlı `LoadPlugin` sınıfa statik yöntemler ekleyin:

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

`PluginLoadContext` Tür öğesinden<xref:System.Runtime.Loader.AssemblyLoadContext>türetilir. Bu `AssemblyLoadContext` tür çalışma zamanında, geliştiricilerin, derleme sürümlerinin çakışmadığından emin olmak için yüklü derlemeleri farklı gruplara yalıtmalarına olanak tanıyan özel bir türdür. Ayrıca, özel `AssemblyLoadContext` , derlemeleri yüklemek için farklı yollar seçebilir ve varsayılan davranışı geçersiz kılabilir. , `PluginLoadContext` Derleme adlarını yollara çözümlemek için `AssemblyDependencyResolver` .NET Core 3,0 ' de tanıtılan türün bir örneğini kullanır. `AssemblyDependencyResolver` Nesnesi, .NET sınıf kitaplığı yoluyla oluşturulur. Derlemeleri ve yerel kitaplıkları, yolu `AssemblyDependencyResolver` oluşturucuya geçilen sınıf kitaplığı için *. Deps. JSON* dosyasını temel alarak göreli yollarına çözümler. Özel `AssemblyLoadContext` , eklentilerin kendi bağımlılıklarına sahip olmasını sağlar `AssemblyDependencyResolver` ve bağımlılıkları doğru şekilde yüklemeyi kolaylaştırır.

`AppWithPlugin` `Program.LoadPlugin` Projenin türüolduğunagöre,yöntemiaşağıdakigövdelegüncelleştirin`PluginLoadContext` :

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

Her eklenti için farklı `PluginLoadContext` bir örnek kullanarak, Eklentiler, sorun olmadan farklı veya hatta çakışan bağımlılıklara sahip olabilir.

## <a name="create-a-simple-plugin-with-no-dependencies"></a>Bağımlılıkları olmayan basit bir eklenti oluşturma

Kök klasöre geri döndüğünüzde şunları yapın:

1. `dotnet new classlib -o HelloPlugin` Adlı`HelloPlugin`yeni bir sınıf kitaplığı projesi oluşturmak için öğesini çalıştırın.
2. `dotnet sln add HelloPlugin/HelloPlugin.csproj` Projeyi`AppWithPlugin` çözüme eklemek için ' i çalıştırın. 
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

`<Project>` Etiketler arasında, aşağıdaki öğeleri ekleyin:

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

`<Private>false</Private>` Öğesi çok önemlidir. Bu, MSBuild 'in *Pluginbase. dll dosyasını* helloplugin çıkış dizinine kopyalamamasını söyler. ' Nin çıkış dizininde *pluginbase. dll* derlemesi varsa, `PluginLoadContext` derlemeyi bulur ve *Merhaba Plugin. dll* derlemesini yüklediğinde yükler. Bu noktada, `HelloPlugin.HelloCommand` türü, varsayılan yükleme bağlamına `ICommand` yüklenen `ICommand` arabirimi değil,, `HelloPlugin` projenin çıkış dizinindeki *pluginbase. dll* ' den arabirimini uygular. Çalışma zamanı, bu iki türü farklı derlemelerden farklı türler olarak gördüğünden, `AppWithPlugin.Program.CreateCommands` bu yöntem komutları bulamaz. Sonuç olarak, `<Private>false</Private>` eklenti arabirimlerini içeren derlemeye başvuru için meta veriler gerekir.

Proje tamamlandığına göre, `HelloPlugin` eklentinin nerede bulunabileceğinizi bilmesi için `AppWithPlugin` projeyi güncelleştirmemiz gerekir. `HelloPlugin` Açıklamadan sonra, `pluginPaths` dizinin bir öğesi olarak ekleyin. `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` `// Paths to plugins to load`

## <a name="create-a-plugin-with-library-dependencies"></a>Kitaplık bağımlılıklarıyla eklenti oluşturma

Neredeyse tüm eklentiler basit bir "Merhaba Dünya" öğesinden daha karmaşıktır ve birçok eklenti diğer kitaplıklara bağımlılıkları vardır. Örnekteki `JsonPlugin` `Newtonsoft.Json`ve `OldJson` eklenti projeleri üzerinde NuGet paketi bağımlılıklarını içeren iki eklenti örneği gösterir. Proje dosyaları, proje başvuruları için özel bilgilere sahip değildir ve (eklenti yolları `pluginPaths` diziye eklendikten sonra) Eklentiler, appwithplugin uygulamasının yürütülmesi halinde çalıştırılsa bile kusursuz bir şekilde çalışır. Ancak, bu projeler başvurulan derlemeleri çıkış dizinine kopyalamadıkları için, eklentilerin çalışması için kullanıcının makinesinde derlemelerin mevcut olması gerekir. Bu sorunu geçici olarak çözmek için iki yol vardır. İlk seçenek, sınıf kitaplığını yayımlamak için `dotnet publish` komutunu kullanmaktır. Alternatif olarak, eklenti `dotnet build` için çıkışını kullanmak istiyorsanız, eklentinin proje dosyasındaki `<PropertyGroup>` Etiketler arasına `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` özelliği ekleyebilirsiniz. Örnek için bkz. eklentiprojesi.`XcopyablePlugin`

## <a name="other-plugin-examples-in-the-sample"></a>Örnekteki diğer eklenti örnekleri

Bu öğreticinin tüm kaynak kodu [DotNet/Samples deposunda](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin)bulunabilir. Tamamlanan örnek, bazı `AssemblyDependencyResolver` davranış örneklerini içerir. Örneğin, `AssemblyDependencyResolver` nesne yerel kitaplıkları ve NuGet paketlerine dahil edilen yerelleştirilmiş uydu derlemelerini de çözümleyebilir. Örnekler deposunda `FrenchPlugin` ve bu senaryolar gösterilmektedir. `UVPlugin`

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a>NuGet paketinde tanımlanan eklenti arabirimi derlemesine başvurma

Adlı bir uygulama olan, adlı `A.PluginBase`NuGet paketinde tanımlanmış bir eklenti arabirimi olduğunu varsayalım. Eklenti projenizde pakete doğru şekilde nasıl başvurdunuz? Proje başvuruları için, proje dosyasındaki `<Private>false</Private>` `ProjectReference` öğesindeki meta verilerin kullanılması dll 'nin çıkışa kopyalanmasını engelledi.

`A.PluginBase` Pakete doğru bir şekilde başvurmak için proje dosyasındaki `<PackageReference>` öğeyi şu şekilde değiştirmek istersiniz:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Bu, `A.PluginBase` derlemelerin eklentinin çıkış dizinine kopyalanmasını engeller ve eklenti 'un `A.PluginBase`bir sürümünü kullanmasını sağlar.

## <a name="plugin-target-framework-recommendations"></a>Eklenti hedef Framework önerileri

Eklenti bağımlılık yüklemesi *. Deps. JSON* dosyasını kullandığından, eklentinin hedef çerçevesiyle ilgili bir Gotcha vardır. Özellikle, eklentilerinizin bir .NET Standard sürümü yerine .NET Core 3,0 gibi bir çalışma zamanını hedeflemesi gerekir. *. Deps. JSON* dosyası, projenin hedeflediği çerçeveye göre oluşturulur ve birçok .NET Standard uyumlu paket, belirli çalışma zamanları için .NET Standard ve uygulama derlemelerinin oluşturulmasına yönelik başvuru derlemeleri sunduğundan, *. Deps. JSON* uygulama derlemelerini doğru görmeyebilir veya Istediğiniz .NET Core sürümü yerine bir derlemenin .NET Standard sürümünü alabilir.
