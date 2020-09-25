---
title: Eklentilerle .NET Core uygulaması oluşturma
description: Eklentileri destekleyen bir .NET Core uygulaması oluşturmayı öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: ce7ac826feaf4542307abefde6d40a319d78e423
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247598"
---
# <a name="create-a-net-core-application-with-plugins"></a>Eklentilerle .NET Core uygulaması oluşturma

Bu öğreticide, yükleme eklentilerini bir özel olarak nasıl oluşturacağınız gösterilmektedir <xref:System.Runtime.Loader.AssemblyLoadContext> . , <xref:System.Runtime.Loader.AssemblyDependencyResolver> Eklentinin bağımlılıklarını çözümlemek için kullanılır. Öğretici, eklentinin bağımlılıklarını barındırma uygulamasından doğru şekilde yalıtır. Şunları öğrenirsiniz:

- Eklentileri desteklemek için bir proje yapısı yapın.
- <xref:System.Runtime.Loader.AssemblyLoadContext>Her bir eklentiyi yüklemek için özel oluşturun.
- <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName>Eklentilerin bağımlılıklara sahip olmasını sağlamak için türü kullanın.
- Yalnızca derleme yapıtları kopyalanarak kolayca dağıtılabilecek olan eklentileri yazar.

## <a name="prerequisites"></a>Önkoşullar

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

Projenin kök klasöründe, öğesini çalıştırın `dotnet new classlib -o PluginBase` . Ayrıca, `dotnet sln add PluginBase/PluginBase.csproj` projeyi çözüm dosyasına eklemek için öğesini çalıştırın. Dosyayı silin `PluginBase/Class1.cs` ve `PluginBase` aşağıdaki arabirim tanımıyla adlı klasörde yeni bir dosya oluşturun `ICommand.cs` :

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

Bu `ICommand` arabirim, tüm eklentilerin uygulayamayacağı arabirimdir.

`ICommand`Arabirim tanımlandığına göre, uygulama projesi biraz daha fazla doldurulabilir. `AppWithPlugin` `PluginBase` Kök klasördeki komutla projeye bir başvuru ekleyin `dotnet add AppWithPlugin/AppWithPlugin.csproj reference PluginBase/PluginBase.csproj` .

`// Load commands from plugins`Verilen dosya yollarından eklentileri yüklemesini etkinleştirmek için yorumu aşağıdaki kod parçacığı ile değiştirin:

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

`// Execute the command with the name passed as an argument`Yorumu aşağıdaki kod parçacığıyla değiştirin:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

Son olarak, `Program` `LoadPlugin` `CreateCommands` burada gösterildiği gibi, ve adlı sınıfa statik yöntemler ekleyin:

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

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

`PluginLoadContext`Tür öğesinden türetilir <xref:System.Runtime.Loader.AssemblyLoadContext> . `AssemblyLoadContext`Tür çalışma zamanında, geliştiricilerin, derleme sürümlerinin çakışmadığından emin olmak için yüklü derlemeleri farklı gruplara yalıtmalarına olanak tanıyan özel bir türdür. Ayrıca, özel, `AssemblyLoadContext` derlemeleri yüklemek için farklı yollar seçebilir ve varsayılan davranışı geçersiz kılabilir. , `PluginLoadContext` `AssemblyDependencyResolver` Derleme adlarını yollara çözümlemek Için .net Core 3,0 ' de tanıtılan türün bir örneğini kullanır. `AssemblyDependencyResolver`Nesnesi, .NET sınıf kitaplığı yoluyla oluşturulur. Derlemeleri ve yerel kitaplıkları, yolu oluşturucuya geçilen sınıf kitaplığı için dosyadaki *.deps.js* dosya temelinde göreli yollarına çözümler `AssemblyDependencyResolver` . Özel, `AssemblyLoadContext` eklentilerin kendi bağımlılıklarına sahip olmasını sağlar ve `AssemblyDependencyResolver` bağımlılıkları doğru şekilde yüklemeyi kolaylaştırır.

`AppWithPlugin`Projenin `PluginLoadContext` türü olduğuna `Program.LoadPlugin` göre, yöntemi aşağıdaki gövdele güncelleştirin:

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

`PluginLoadContext`Her eklenti için farklı bir örnek kullanarak, Eklentiler, sorun olmadan farklı veya hatta çakışan bağımlılıklara sahip olabilir.

## <a name="simple-plugin-with-no-dependencies"></a>Bağımlılıkları olmayan basit eklenti

Kök klasöre geri döndüğünüzde şunları yapın:

1. Adlı yeni bir sınıf kitaplığı projesi oluşturmak için aşağıdaki komutu çalıştırın `HelloPlugin` :

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. Projeyi çözüme eklemek için aşağıdaki komutu çalıştırın `AppWithPlugin` :

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. *Merhaba Plugin/Class1. cs* dosyasını aşağıdaki içeriklerle *HelloCommand.cs* adlı bir dosyayla değiştirin:

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

Şimdi, *Helloplugin. csproj* dosyasını açın. Şunun gibi görünmelidir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

`<Project>`Etiketler arasında, aşağıdaki öğeleri ekleyin:

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

`<Private>false</Private>`Öğesi önemlidir. Bu, MSBuild eklentisinin çıkış dizinine *PluginBase.dll* kopyalamamasını söyler. *PluginBase.dll* derlemesi çıkış dizininde varsa, `PluginLoadContext` derlemeyi bulur ve *HelloPlugin.dll* derlemesini yüklediğinde yükler. Bu noktada, `HelloPlugin.HelloCommand` tür `ICommand` arabirimi *PluginBase.dll* `HelloPlugin` `ICommand` varsayılan yükleme bağlamına yüklenen arabirimi değil, projenin çıkış dizinindekiPluginBase.dlluygular. Çalışma zamanı bu iki türü farklı derlemelerden farklı türler olarak gördüğünden, `AppWithPlugin.Program.CreateCommands` Yöntem komutları bulamaz. Sonuç olarak, `<Private>false</Private>` eklenti arabirimlerini içeren derlemeye başvuru için meta veriler gerekir.

Benzer şekilde, `<ExcludeAssets>runtime</ExcludeAssets>` diğer paketlere başvuruyorsa öğesi de önemlidir `PluginBase` . Bu ayar, ile aynı etkiye sahiptir, `<Private>false</Private>` ancak `PluginBase` Proje veya bağımlılıklarından birinin dahil olabileceği paket başvuruları üzerinde de geçerlidir.

`HelloPlugin`Proje tamamlandığına göre, `AppWithPlugin` eklentinin nerede bulunabileceğinizi bilmesi için projeyi güncelleştirmeniz gerekir `HelloPlugin` . Açıklamadan sonra `// Paths to plugins to load` , `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` Array öğesi olarak ekleyin (Bu yol, kullandığınız .NET Core sürümüne göre farklı olabilir) `pluginPaths` .

## <a name="plugin-with-library-dependencies"></a>Kitaplık bağımlılıkları olan eklenti

Neredeyse tüm eklentiler basit bir "Merhaba Dünya" öğesinden daha karmaşıktır ve birçok eklenti diğer kitaplıklara bağımlılıkları vardır. `JsonPlugin`Örnekteki ve `OldJson` eklenti projeleri üzerinde NuGet paketi bağımlılıklarını içeren iki eklenti örneği gösterir `Newtonsoft.Json` . Proje dosyaları, proje başvuruları için özel bilgilere sahip değildir ve (eklenti yolları diziye eklendikten sonra `pluginPaths` ) Eklentiler, AppWithPlugin uygulamasının yürütülmesi halinde çalıştırılsa bile kusursuz bir şekilde çalışır. Ancak, bu projeler başvurulan derlemeleri çıkış dizinine kopyalamadıkları için, eklentilerin çalışması için kullanıcının makinesinde derlemelerin mevcut olması gerekir. Bu sorunu geçici olarak çözmek için iki yol vardır. İlk seçenek, `dotnet publish` sınıf kitaplığını yayımlamak için komutunu kullanmaktır. Alternatif olarak, eklenti için çıkışını kullanmak istiyorsanız `dotnet build` , eklentinin `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` `<PropertyGroup>` Proje dosyasındaki Etiketler arasına özelliği ekleyebilirsiniz. `XcopyablePlugin`Örnek için bkz. eklenti projesi.

## <a name="other-examples-in-the-sample"></a>Örnekteki diğer örnekler

Bu öğreticinin tüm kaynak kodu [DotNet/Samples deposunda](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin)bulunabilir. Tamamlanan örnek, bazı davranış örneklerini içerir `AssemblyDependencyResolver` . Örneğin, `AssemblyDependencyResolver` nesne yerel kitaplıkları ve NuGet paketlerine dahil edilen yerelleştirilmiş uydu derlemelerini de çözümleyebilir. `UVPlugin` `FrenchPlugin` Örnekler deposunda ve bu senaryolar gösterilmektedir.

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a>Bir NuGet paketinden eklenti arabirimine başvurma

Adlı bir uygulama olan, adlı NuGet paketinde tanımlanmış bir eklenti arabirimi olduğunu varsayalım `A.PluginBase` . Eklenti projenizde pakete doğru şekilde nasıl başvurdunuz? Proje başvuruları için, `<Private>false</Private>` `ProjectReference` Proje dosyasındaki öğesindeki meta verilerin kullanılması dll 'nin çıkışa kopyalanmasını engelledi.

Pakete doğru bir şekilde başvurmak için `A.PluginBase` `<PackageReference>` Proje dosyasındaki öğeyi şu şekilde değiştirmek istersiniz:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Bu, `A.PluginBase` derlemelerin eklentinin çıkış dizinine kopyalanmasını engeller ve eklenti 'un bir sürümünü kullanmasını sağlar `A.PluginBase` .

## <a name="plugin-target-framework-recommendations"></a>Eklenti hedef Framework önerileri

Eklenti bağımlılık yüklemesi dosyadaki *.deps.js* kullandığından, eklentinin hedef çerçevesiyle ilgili bir Gotcha vardır. Özellikle, eklentilerinizin bir .NET Standard sürümü yerine .NET Core 3,0 gibi bir çalışma zamanını hedeflemesi gerekir. Dosya *.deps.js* , projenin hedeflediği çerçeveye göre oluşturulur ve birçok .NET Standard uyumlu paket, belirli çalışma zamanları için .NET Standard ve uygulama derlemelerinin oluşturulmasına yönelik başvuru derlemeleri gönderdiğinden, * üzerinde.deps.js* uygulama derlemelerini doğru şekilde göremeyebilir ya da istediğiniz .NET Core sürümü yerine bir derlemenin .NET Standard sürümünü alabilir.

## <a name="plugin-framework-references"></a>Eklenti çerçevesi başvuruları

Şu anda, eklentiler işleme yeni çerçeveler sunmaz. Örneğin, Framework kullanan bir eklentiyi `Microsoft.AspNetCore.App` yalnızca kök Framework kullanan bir uygulamaya yükleyebilirsiniz `Microsoft.NETCore.App` . Konak uygulama, eklentiler tarafından ihtiyaç duyulan tüm çerçevelere başvuruları bildirmelidir.
