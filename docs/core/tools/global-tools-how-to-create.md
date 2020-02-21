---
title: 'Öğretici: .NET Core aracı oluşturma'
description: .NET Core aracı oluşturmayı öğrenin. Araç, .NET Core CLI kullanılarak yüklenen bir konsol uygulamasıdır.
ms.date: 02/12/2020
ms.openlocfilehash: 558bf9e37efc8de68a61f1384fababe342ab7d66
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543410"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a>Öğretici: .NET Core CLI kullanarak bir .NET Core aracı oluşturma

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

Bu öğreticide bir .NET Core aracı oluşturma ve paketleme öğretilir. .NET Core CLI, diğer kullanıcıların yükleyebileceği ve çalıştırabileceği bir araç olarak konsol uygulaması oluşturmanızı sağlar. .NET Core araçları, .NET Core CLI yüklenen NuGet paketlerdir. Araçlar hakkında daha fazla bilgi için bkz. [.NET Core araçlarına genel bakış](global-tools.md).

Oluşturacağınız araç, girdi olarak bir ileti alıp iletiyi bir robot görüntüsünü oluşturan metin satırlarıyla birlikte görüntüleyen bir konsol uygulamasıdır.

Bu, bir dizi üç öğreticiden ilkdir. Bu öğreticide bir araç oluşturur ve paketleyin. Sonraki iki öğreticilerde [, aracı genel araç olarak kullanır](global-tools-how-to-use.md) ve [Aracı yerel bir araç olarak kullanabilirsiniz](local-tools-how-to-use.md).

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core SDK 3,1](https://dotnet.microsoft.com/download) veya sonraki bir sürümü.

  Bu öğreticide, genel [araçlar .NET Core SDK](global-tools-how-to-use.md) 2,1 ve üzeri sürümler için bu öğretici ve bu sürümden itibaren küresel araçlar geçerlidir. Ancak bu öğreticide, [Yerel araçlar öğreticisine](local-tools-how-to-use.md)devam etme seçeneğine sahip olmanız için 3,1 veya sonraki bir sürümü yüklemiş olduğunuz varsayılmaktadır. Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir. Bir araç oluşturma yordamları, bunu küresel bir araç olarak veya yerel bir araç olarak kullanıp kullanmayacağınızı de aynıdır.
  
- Tercih ettiğiniz bir metin veya kod düzenleyicisi.

## <a name="create-a-project"></a>Proje oluştur

1. Bir komut istemi açın ve *Depo*adlı bir klasör oluşturun.

1. *Depo* klasörüne gidin ve aşağıdaki komutu girin ve proje adının benzersiz olması için `<name>` benzersiz bir değerle değiştirin. 

   ```dotnetcli
   dotnet new console -n botsay-<name>
   ```

   Örneğin, aşağıdaki komutu çalıştırabilirsiniz:

   ```dotnetcli
   dotnet new console -n botsay-nancydavolio
   ```

   Komut, *Depo* klasörü altında *botdeyin-\<name >* adlı yeni bir klasör oluşturur.

1. *Botdeyin-\<adı >* klasörüne gidin.

   ```console
   cd botsay-<name>
   ```

## <a name="add-the-code"></a>Kod ekleme

1. `Program.cs` dosyasını kod düzenleyicinizle açın.

1. Aşağıdaki `using` yönergesini dosyanın en üstüne ekleyin:

   ```csharp
   using System.Reflection;
   ```

1. Uygulama için komut satırı bağımsız değişkenlerini işlemek üzere `Main` yöntemini aşağıdaki kodla değiştirin.

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

   Hiçbir bağımsız değişken geçirilmezse, kısa bir yardım iletisi görüntülenir. Aksi takdirde, tüm bağımsız değişkenler tek bir dizeye birleştirilir ve bir sonraki adımda oluşturduğunuz `ShowBot` yöntemi çağırarak yazdırılır.

1. Dize parametresi alan `ShowBot` adlı yeni bir yöntem ekleyin. Yöntemi, metin satırlarını kullanarak iletiyi ve bir robot görüntüsünü yazdırır.

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

`--` sınırlayıcısından sonraki tüm bağımsız değişkenler uygulamanıza geçirilir.

## <a name="package-the-tool"></a>Aracı paketleyin

Uygulamayı bir araç olarak paketleyebilir ve dağıtabilmeniz için önce proje dosyasını değiştirmeniz gerekir. 

1. *Botdeyin-\<adı >. csproj* dosyasını açın ve `<PropertyGroup>` düğümünün sonuna üç yeni XML düğümü ekleyin:

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>`, yüklendikten sonra aracı çağıracağı komutu belirten isteğe bağlı bir öğedir. Bu öğe sağlanmazsa, araç için komut adı *. csproj* uzantısı olmayan proje dosyası adıdır.

   `<PackageOutputPath>`, NuGet paketinin nerede üretileceği belirleyen isteğe bağlı bir öğedir. NuGet paketi, .NET Core CLI aracınızı yüklemek için kullandığı şeydir.

   Proje dosyası artık aşağıdaki örneğe benzer şekilde görünür:

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
  
     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>netcoreapp3.1</TargetFramework>
  
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

   *Botdeyin-\<name >. 1.0.0. nupkg* dosyası, bu örnekte *./nupkg klasörüdür./n/nDosya* olan *botsöyleyin-\<name >. csproj* dosyasındaki `<PackageOutputPath>` değeri tarafından tanımlanan klasörde oluşturulur.
  
   Bir aracı herkese açık bir şekilde yayınlamak istediğinizde, `https://www.nuget.org`yükleyebilirsiniz. Araç NuGet 'de kullanılabilir olduğunda, geliştiriciler [DotNet aracı install](dotnet-tool-install.md) komutunu kullanarak aracı yükleyebilir. Bu öğreticide, paketini doğrudan yerel *nupkg* klasöründen yüklersiniz, bu nedenle paketi NuGet 'e yüklemeye gerek yoktur.

## <a name="troubleshoot"></a>Sorunları Gider

Öğreticiyi takip ederken bir hata mesajı alırsanız bkz. [.NET Core araç kullanımı sorunlarını giderme](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir konsol uygulaması oluşturdunuz ve bunu bir araç olarak paketlediyseniz. Aracın genel bir araç olarak nasıl kullanılacağını öğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Küresel bir araç yükleyip kullanma](global-tools-how-to-use.md)

İsterseniz küresel araçlar öğreticisini atlayabilir ve doğrudan yerel araçlar öğreticisine gidebilirsiniz.

> [!div class="nextstepaction"]
> [Yerel bir araç yükleyip kullanma](local-tools-how-to-use.md)
