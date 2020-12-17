---
title: 'Öğretici: .NET aracı oluşturma'
description: .NET aracı oluşturmayı öğrenin. Araç, .NET CLı kullanılarak yüklenen bir konsol uygulamasıdır.
ms.topic: tutorial
ms.date: 12/14/2020
ms.openlocfilehash: dc5cf014336848ff1a3035647a386419653a083b
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633903"
---
# <a name="tutorial-create-a-net-tool-using-the-net-cli"></a>Öğretici: .NET CLı kullanarak .NET aracı oluşturma

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

Bu öğreticide bir .NET aracı oluşturma ve paketleme hakkında öğretilir. .NET CLı, diğer kullanıcıların yükleyebileceği ve çalıştırabileceği bir araç olarak konsol uygulaması oluşturmanıza imkan tanır. .NET araçları, .NET CLı 'den yüklenen NuGet paketlerdir. Araçlar hakkında daha fazla bilgi için bkz. [.net araçlarına genel bakış](global-tools.md).

Oluşturacağınız araç, girdi olarak bir ileti alıp iletiyi bir robot görüntüsünü oluşturan metin satırlarıyla birlikte görüntüleyen bir konsol uygulamasıdır.

Bu, bir dizi üç öğreticiden ilkdir. Bu öğreticide bir araç oluşturur ve paketleyin. Sonraki iki öğreticilerde [, aracı genel araç olarak kullanır](global-tools-how-to-use.md) ve [Aracı yerel bir araç olarak kullanabilirsiniz](local-tools-how-to-use.md). Bir araç oluşturma yordamları, bunu küresel bir araç olarak veya yerel bir araç olarak kullanıp kullanmayacağınızı de aynıdır.

## <a name="prerequisites"></a>Önkoşullar

- [.NET SDK 5.0.100](https://dotnet.microsoft.com/download) veya sonraki bir sürümü.

  Bu öğretici .NET SDK 5,0 kullanır, ancak küresel araçlar .NET Core SDK 2,1 ' den itibaren kullanılabilir. Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.

- Tercih ettiğiniz bir metin veya kod düzenleyicisi.

## <a name="create-a-project"></a>Proje oluşturma

1. Bir komut istemi açın ve *Depo* adlı bir klasör oluşturun.

1. *Depo* klasörüne gidin ve şu komutu girin:

   ```dotnetcli
   dotnet new console -n microsoft.botsay -f net5.0
   ```

   Komut, *Depo* klasörü altında *Microsoft. botdeyin* adlı yeni bir klasör oluşturur.

   > [!NOTE]
   > Bu öğreticide, .NET 5,0 ' i hedefleyen bir araç oluşturursunuz. Farklı bir çerçeveyi hedeflemek için `-f|--framework` seçeneğini değiştirin. Birden çok çerçeveyi hedeflemek için, `TargetFramework` `TargetFrameworks` Aşağıdaki örnekte gösterildiği gibi, öğesini proje dosyasındaki bir öğeyle değiştirin:
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFrameworks>netcoreapp3.1;net5.0</TargetFrameworks>
   >   </PropertyGroup>
   > </Project>
   > ```

1. *Microsoft. botsay* klasörüne gidin.

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a>Kod ekleme

1. `Program.cs`Dosyayı kod düzenleyicinizle açın.

1. Aşağıdaki `using` yönergeyi dosyanın en üstüne ekleyin:

   ```csharp
   using System.Reflection;
   ```

1. Yöntemi, `Main` uygulamanın komut satırı bağımsız değişkenlerini işlemek için aşağıdaki kodla değiştirin.

   ```csharp
   static void Main(string[] args)
   {
       if (args.Length == 0)
       {
           var versionString = Assembly.GetEntryAssembly()
                                   .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                   .InformationalVersion
                                   .ToString();

           Console.WriteLine($"botsay v{versionString}");
           Console.WriteLine("-------------");
           Console.WriteLine("\nUsage:");
           Console.WriteLine("  botsay <message>");
           return;
       }

       ShowBot(string.Join(' ', args));
   }
   ```

   Hiçbir bağımsız değişken geçirilmezse, kısa bir yardım iletisi görüntülenir. Aksi takdirde, tüm bağımsız değişkenler tek bir dizeye birleştirilir ve bir `ShowBot` sonraki adımda oluşturduğunuz yöntemi çağırarak yazdırılır.

1. Dize parametresi alan adlı yeni bir yöntem ekleyin `ShowBot` . Yöntemi, metin satırlarını kullanarak iletiyi ve bir robot görüntüsünü yazdırır.

   ```csharp
   static void ShowBot(string message)
   {
       string bot = $"\n        {message}";
       bot += @"
       __________________
                         \
                          \
                             ....
                             ....'
                              ....
                           ..........
                       .............'..'..
                    ................'..'.....
                  .......'..........'..'..'....
                 ........'..........'..'..'.....
                .'....'..'..........'..'.......'.
                .'..................'...   ......
                .  ......'.........         .....
                .    _            __        ......
               ..    #            ##        ......
              ....       .                 .......
              ......  .......          ............
               ................  ......................
               ........................'................
              ......................'..'......    .......
           .........................'..'.....       .......
        ........    ..'.............'..'....      ..........
      ..'..'...      ...............'.......      ..........
     ...'......     ...... ..........  ......         .......
    ...........   .......              ........        ......
   .......        '...'.'.              '.'.'.'         ....
   .......       .....'..               ..'.....
      ..       ..........               ..'........
             ............               ..............
            .............               '..............
           ...........'..              .'.'............
          ...............              .'.'.............
         .............'..               ..'..'...........
         ...............                 .'..............
          .........                        ..............
           .....
   ";
       Console.WriteLine(bot);
   }
   ```

1. Yaptığınız değişiklikleri kaydedin.

## <a name="test-the-application"></a>Uygulamayı test etme

Projeyi çalıştırın ve çıktıyı görüntüleyin. Farklı sonuçları görmek için komut satırında bu çeşitlemeleri deneyin:

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

Sınırlayıcıdan sonraki tüm bağımsız değişkenler `--` uygulamanıza geçirilir.

## <a name="package-the-tool"></a>Aracı paketleyin

Uygulamayı bir araç olarak paketleyebilir ve dağıtabilmeniz için önce proje dosyasını değiştirmeniz gerekir.

1. *Microsoft. botsöyleyin. csproj* dosyasını açın ve düğümün sonuna üç yeni XML düğümü ekleyin `<PropertyGroup>` :

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>` , yüklendikten sonra aracı çağıracağı komutu belirten isteğe bağlı bir öğedir. Bu öğe sağlanmazsa, araç için komut adı *. csproj* uzantısı olmayan proje dosyası adıdır.

   `<PackageOutputPath>` , NuGet paketinin nerede üretileceği belirleyen isteğe bağlı bir öğedir. NuGet paketi, .NET CLı 'nin aracınızı yüklemek için kullandığı şeydir.

   Proje dosyası artık aşağıdaki örneğe benzer şekilde görünür:

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>net5.0</TargetFramework>

       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>

     </PropertyGroup>

   </Project>
   ```

1. [DotNet Pack](dotnet-pack.md) komutunu çalıştırarak bir NuGet paketi oluşturun:

   ```dotnetcli
   dotnet pack
   ```

   *Microsoft. botı. 1.0.0. nupkg* dosyası, `<PackageOutputPath>` *Microsoft. botsöyleyin. csproj* dosyasındaki değeri tarafından tanımlanan klasörde oluşturulur. Bu örnekte *./nupkg* klasörüdür.

   Bir aracı herkese açık bir şekilde yayınlamak istediğinizde, ' a yükleyebilirsiniz `https://www.nuget.org` . Araç NuGet 'de kullanılabilir olduğunda, geliştiriciler [DotNet aracı install](dotnet-tool-install.md) komutunu kullanarak aracı yükleyebilir. Bu öğreticide, paketini doğrudan yerel *nupkg* klasöründen yüklersiniz, bu nedenle paketi NuGet 'e yüklemeye gerek yoktur.

## <a name="troubleshoot"></a>Sorun giderme

Öğreticiyi takip ederken bir hata mesajı alırsanız bkz. [.NET araç kullanım sorunlarını giderme](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir konsol uygulaması oluşturdunuz ve bunu bir araç olarak paketlediyseniz. Aracın genel bir araç olarak nasıl kullanılacağını öğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Genel araç yükleyip kullanma](global-tools-how-to-use.md)

İsterseniz küresel araçlar öğreticisini atlayabilir ve doğrudan yerel araçlar öğreticisine gidebilirsiniz.

> [!div class="nextstepaction"]
> [Yerel araç yükleyip kullanma](local-tools-how-to-use.md)
