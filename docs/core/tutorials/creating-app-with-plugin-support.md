---
title: Eklenti ile .NET Core uygulaması oluşturma
description: Eklentileri destekleyen bir .NET Core uygulaması oluşturmayı öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: a9431ee28c7df21a8688f845be20e062eca21887
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647237"
---
# <a name="create-a-net-core-application-with-plugins"></a>Eklenti ile .NET Core uygulaması oluşturma

Bu öğretici, nasıl gösterir için:

- Eklentileri desteklemek için bir proje yapısı.
- Bir özel Oluştur <xref:System.Runtime.Loader.AssemblyLoadContext> her Eklentisi yüklenemedi.
- Kullanım `System.Runtime.Loader.AssemblyDependencyResolver` bağımlılıkları eklentileri izin vermek için türü.
- Yalnızca derleme yapıtları kopyalayarak kolayca dağıtılabilir eklentileri yazar.

## <a name="prerequisites"></a>Önkoşullar

- Yükleme [.NET Core 3.0 Önizleme 2 SDK](https://www.microsoft.com/net/core) ya da daha yeni bir sürümü.

## <a name="create-the-application"></a>Uygulama oluşturma

İlk adım, uygulama oluşturmaktır:

1. Yeni bir klasör oluşturun ve o klasördeki çalıştırmak `dotnet new console -o AppWithPlugin`. 
2. Daha kolay proje derleme yapmak için Visual Studio çözüm dosyası oluşturun. Çalıştırma `dotnet new sln` aynı klasörde yer alan. 
3. Çalıştırma `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` uygulaması projesi çözüme eklemek için.

Şimdi biz uygulamamız çatısında önizlememiz doldurabilirsiniz. Değiştirin *AppWithPlugin/Program.cs* dosyasındaki kodu aşağıdaki kodla:

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

## <a name="create-the-plugin-interfaces"></a>Eklentisi arabirimleri oluşturun

Eklentiler ile bir uygulama oluşturmanın sonraki adımı eklentileri oluşturmanız arabirimi tanımlamaktır. Uygulama ve eklentiler arasında iletişim kurmak için kullanmayı planladığınız herhangi bir türü içeren bir sınıf kitaplığı yapmanızı öneririz. Bu bölme, tam uygulamanız göndermek zorunda kalmadan bir paket olarak, eklenti arabirimi yayımlamanızı sağlar.

Projenin kök klasöründe Çalıştır `dotnet new classlib -o PluginBase`. Ayrıca, `dotnet sln add PluginBase/PluginBase.csproj` projeyi çözüm dosyasına eklemek için. Silme `PluginBase/Class1.cs` dosya ve yeni bir dosya oluşturun `PluginBase` adlı klasöre `ICommand.cs` aşağıdaki arabirim tanımı ile:

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

Bu `ICommand` arabirimidir arabirimi tüm eklentileri uygulamanız.

Şimdi `ICommand` arabirimi tanımlanır, uygulama projesine doldurulabilir biraz daha. Başvuru ekleme `AppWithPlugin` için proje `PluginBase` ile proje `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` kök klasörden komutu.

Değiştirin `// Load commands from plugins` eklentilerini yüklemek etkinleştirmek için aşağıdaki kod parçacığı ile Açıklama gelen dosya yolu ele alalım:

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

Ardından değiştirin `// Output the loaded commands` aşağıdaki kod parçacığı ile Açıklama:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

Değiştirin `// Execute the command with the name passed as an argument` aşağıdaki kod parçacığıyla açıklaması:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

Ve son olarak, statik yöntemler ekleyin `Program` adlı sınıfı `LoadPlugin` ve `CreateCommands`, burada gösterildiği gibi:

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

## <a name="load-plugins"></a>Eklenti yükleme

Artık uygulamanın düzgün yüklenebileceği ve komutlar yüklü eklenti derlemelerden örneği, ancak Eklenti derlemeleri yüklemek hala işleyemiyor. Adlı bir dosya oluşturun *PluginLoadContext.cs* içinde *AppWithPlugin* klasöründe aşağıdaki içeriğe sahip:

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

`PluginLoadContext` Tür türetilir <xref:System.Runtime.Loader.AssemblyLoadContext>. `AssemblyLoadContext` Sayesinde geliştiriciler, yüklenen derlemeler derleme sürümlerini çakışmasını emin olmak için farklı gruplar halinde ayırmak için çalışma zamanında bir özel tür bir türdür. Ayrıca, bir özel `AssemblyLoadContext` derlemeleri yüklemek ve varsayılan davranışı geçersiz kılmak için farklı yollar seçebilirsiniz. `PluginLoadContext` Örneğini kullanan `AssemblyDependencyResolver` yolları için derleme adlarını çözümlemek için .NET Core 3.0 sürümünde türü. `AssemblyDependencyResolver` Nesnesi, bir .NET sınıf kitaplığı yoluyla oluşturulur. Temel kendi göreli yollar için derlemeler ve yerel kitaplıkları çözümler *deps.json* dosya yolu için geçirildi sınıf kitaplığı için `AssemblyDependencyResolver` Oluşturucusu. Özel `AssemblyLoadContext` kendi bağımlılıkları eklentiler sağlar ve `AssemblyDependencyResolver` bağımlılıkları doğru şekilde yük kolaylaştırır.

Şimdi `AppWithPlugin` projesinde `PluginLoadContext` yazın, güncelleştirme `Program.LoadPlugin` aşağıdaki gövdesi olan yöntemi:

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

Farklı bir kullanarak `PluginLoadContext` örneği her eklentinin, eklentiler için farklı veya hatta çakışan bağımlılıkları olmadan bir sorun olabilir.

## <a name="create-a-simple-plugin-with-no-dependencies"></a>Hiçbir bağımlılık ile basit bir eklenti oluşturun

Geri kök klasöründe aşağıdakileri yapın:

1. Çalıştırma `dotnet new classlib -o HelloPlugin` adlı yeni bir sınıf kitaplığı projesi oluşturmak için `HelloPlugin`.
2. Çalıştırma `dotnet sln add HelloPlugin/HelloPlugin.csproj` projeye eklemek için `AppWithPlugin` çözüm. 
3. Değiştirin *HelloPlugin/Class1.cs* adlı bir dosya dosyasıyla *HelloCommand.cs* aşağıdaki içeriklerle:

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

Artık, *HelloPlugin.csproj* dosya. Aşağıdakine benzer görünmelidir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

Arasında `<Project>` etiketler, aşağıdaki öğeleri ekleyin:

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

`<Private>false</Private>` Öğesi çok önemlidir. Bu MSBuild kopyalamayacak şekilde söyler *PluginBase.dll* HelloPlugin çıkış dizinine. Varsa *PluginBase.dll* derleme Çıktı dizininde mevcut `PluginLoadContext` derleme var. bulup onu yüklediğinde, yükleyebilir *HelloPlugin.dll* derleme. Bu noktada, `HelloPlugin.HelloCommand` tür tarafından uygulanır `ICommand` alanından arabirim *PluginBase.dll* Çıktı dizininde `HelloPlugin` proje değil, `ICommand` yüklendiği arabirimi Varsayılan yükleme bağlamı. Çalışma zamanı bu iki farklı türden farklı derlemeler olarak görür. bu yana `AppWithPlugin.Program.CreateCommands` yöntemi değildir komut bulun. Sonuç olarak, `<Private>false</Private>` eklentisi arabirimleri içeren derlemenin başvurusunu için meta verileri gereklidir.

Şimdi `HelloPlugin` proje tamamladığınızda, güncelleştiriyoruz `AppWithPlugin` nereden başlayacağınızı bilemiyor için proje `HelloPlugin` eklentisi bulunabilir. Sonra `// Paths to plugins to load` açıklama, Ekle `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` öğesi olarak `pluginPaths` dizisi.

## <a name="create-a-plugin-with-library-dependencies"></a>Kitaplık bağımlılıkları olan bir eklenti oluşturun

Neredeyse tüm eklentiler bir basit "Hello World" daha karmaşıktır ve birçok eklenti bağımlılıkları diğer kitaplıkları vardır. `JsonPlugin` Ve `OldJson` örnek eklentisi projeleri göster eklentileri NuGet Paket bağımlılıklarını içeren iki örnek `Newtonsoft.Json`. Proje dosyaları proje başvuruları için herhangi bir özel bilgi yok ve (eklentisi yolları ekledikten sonra `pluginPaths` dizisi) eklentileri mükemmel bir şekilde, aynı yürütme AppWithPlugin uygulamanın çalıştırılmış olsa bile çalıştırın. Ancak, bu projeleri derlemeleri çalışmak eklentileri için kullanıcının makinede mevcut olması gerekmez, çıktı dizinine başvurulan derlemeleri kopyalamayın. Bu sorunu çözmek için iki yolu vardır. İlk seçenek kullanmaktır `dotnet publish` sınıf kitaplığı yayımlamak için komutu. Alternatif olarak, çıktısını kullanabilmelerini istiyorsanız `dotnet build` , eklenti için eklediğiniz `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` arasında özellik `<PropertyGroup>` eklenti ait proje dosyasında etiketler. Bkz: `XcopyablePlugin` eklentisi projesi bir örnek.

## <a name="other-plugin-examples-in-the-sample"></a>Örneğindeki diğer eklenti örnekleri

Bu öğretici için tam kaynak kodunu bulunabilir [dotnet/samples deposuna](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin). Tamamlanan örnek diğer birkaç örnek verilmiştir `AssemblyDependencyResolver` davranışı. Örneğin, `AssemblyDependencyResolver` nesne NuGet paketlerinde yerelleştirilmiş yardımcı derlemeler yanı sıra yerel kitaplıkları da giderebilirsiniz. `UVPlugin` Ve `FrenchPlugin` örnek deposunda aşağıdaki senaryolar gösterilmektedir.

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a>Nasıl bir NuGet paketi içinde tanımlanmış bir eklenti arabirimi derleme başvurusu

Adlı NuGet paketi içinde tanımlanmış bir eklenti arabirimi olan bir uygulama bir olduğunu varsayalım `A.PluginBase`. Nasıl paket eklenti projenizde doğru başvurmuyorsa? Kullanarak proje başvuruları için `<Private>false</Private>` meta veri çubuğunda `ProjectReference` öğesi proje dosyasında çıktı kopyalanan dll engelledi.

Doğru şekilde başvurmak için `A.PluginBase` değiştirmek istediğiniz paketin `<PackageReference>` öğesi aşağıdaki proje dosyasında:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Bu engeller `A.PluginBase` , eklenti çıktı dizinine kopyalanan gelen derlemeleri ve kendi eklenti A kullanmanızı sağlar sürümünü `A.PluginBase`.

## <a name="plugin-target-framework-recommendations"></a>Eklenti hedef framework önerileri

Eklenti bağımlılık yükleniyor kullandığından *deps.json* dosyası, eklenti'nın hedef framework ile ilgili bir sorunu yok. Özellikle, eklenti, bir çalışma zamanı, .NET Core 3.0 gibi .NET Standard'ın bir sürümü yerine hedeflemelidir. `deps.json` Dosyası oluşturulur hangi framework tabanlı Proje hedefleri ve başvuru derlemelerini karşı özel çalışma zamanları, için.NETStandardveuygulamaderlemelerioluşturmakiçinbirçok.NETStandarduyumlupaketikullanımasunulduğundanbuyana`deps.json` düzgün bkz uygulama derlemelerini olabilir veya bir derleme beklediğiniz .NET Core sürümünün yerine .NET Standard sürümünü alıp.
