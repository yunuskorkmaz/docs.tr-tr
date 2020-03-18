---
title: 'Öğretici: Bir .NET Core aracı oluşturma'
description: Bir .NET Core aracını nasıl oluşturabilirsiniz öğrenin. Bir araç .NET Core CLI kullanılarak yüklenen bir konsol uygulamasıdır.
ms.date: 02/12/2020
ms.openlocfilehash: 88cc3be7b149834ace0c5f3ba8ac8c039199908f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156731"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a>Öğretici: .NET Core CLI'yi kullanarak bir .NET Core aracı oluşturun

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

Bu öğretici, bir .NET Core aracını nasıl oluşturup paketlediğinizi öğretir. .NET Core CLI, başkalarının yükleyip çalıştırabileceği bir araç olarak bir konsol uygulaması oluşturmanıza olanak tanır. .NET Core araçları, .NET Core CLI'den yüklenen NuGet paketleridir. Araçlar hakkında daha fazla bilgi için [.NET Core araçlarına genel bakış](global-tools.md)ala.

Oluşturacağınız araç, bir iletiyi girdi olarak alan ve iletiyi bir robot görüntüsünü oluşturan metin çizgileri ile birlikte görüntüleyen bir konsol uygulamasıdır.

Bu üç öğreticiler bir dizi ilkidir. Bu öğreticide, bir araç oluşturur ve paketlersiniz. Sonraki iki öğreticide [aracı genel bir araç olarak kullanırsınız](global-tools-how-to-use.md) ve [aracı yerel bir araç olarak kullanırsınız.](local-tools-how-to-use.md)

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core SDK 3.1](https://dotnet.microsoft.com/download) veya daha sonraki bir sürüm.

  Bu öğretici ve [genel araçlar için](global-tools-how-to-use.md) aşağıdaki öğretici .NET Core SDK 2.1 ve sonraki sürümlere uygulanır, çünkü bu sürümden başlayarak genel araçlar mevcuttur. Ama bu öğretici [yerel araçlar öğretici](local-tools-how-to-use.md)devam seçeneği ne var böylece 3.1 veya daha sonra yüklü varsayar. Yerel araçlar .NET Core SDK 3.0'dan başlayarak mevcuttur. Bir araç oluşturma yordamları, ister genel bir araç olarak ister yerel bir araç olarak kullanın aynıdır.
  
- Tercih ettiğiniz bir metin veya kod düzenleyicisi.

## <a name="create-a-project"></a>Proje oluşturma

1. Komut istemini açın ve *depo*adlı bir klasör oluşturun.

1. *Depo* klasörüne gidin ve aşağıdaki komutu girin:

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   Komut, *depo* klasörü altında *microsoft.botsay* adlı yeni bir klasör oluşturur.

1. *microsoft.botsay* klasörüne gidin.

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a>Kod ekleme

1. Kodu `Program.cs` düzenleyicinizle dosyayı açın.

1. Dosyanın `using` üst bölümüne aşağıdaki yönergeyi ekleyin:

   ```csharp
   using System.Reflection;
   ```

1. Uygulama `Main` için komut satırı bağımsız değişkenlerini işlemek için yöntemi aşağıdaki kodla değiştirin.

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

   Bağımsız değişken geçirilmezse, kısa bir yardım iletisi görüntülenir. Aksi takdirde, tüm bağımsız değişkenler tek bir dize içine sıkıştırılır ve bir sonraki adımda oluşturduğunuz `ShowBot` yöntem çağırArak yazdırılır.

1. Dize parametresi alan yeni bir yöntem ekleyin. `ShowBot` Yöntem, metin satırlarını kullanarak bir robotun iletisini ve görüntüsünü yazdırır.

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

Projeyi çalıştırın ve çıktıyı görün. Farklı sonuçlar görmek için komut satırında bu varyasyonları deneyin:

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

`--` Delimiter sonra tüm bağımsız değişkenler uygulamanıza geçirilir.

## <a name="package-the-tool"></a>Aracı paketle

Uygulamayı bir araç olarak paketleyip dağıtabilmeniz için proje dosyasını değiştirmeniz gerekir.

1. *microsoft.botsay.csproj* dosyasını açın ve `<PropertyGroup>` düğümün sonuna üç yeni XML düğümü ekleyin:

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>`yüklendikten sonra aracı çağıracak komutu belirten isteğe bağlı bir öğedir. Bu öğe sağlanmadıysa, aracın komut adı *.csproj* uzantısı olmayan proje dosya adıdır.

   `<PackageOutputPath>`NuGet paketinin nerede üretileceğini belirleyen isteğe bağlı bir öğedir. NuGet paketi .NET Core CLI'nin aracınızı yüklemek için kullandığı pakettir.

   Proje dosyası şimdi aşağıdaki örnek gibi görünüyor:

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

1. [dotnet paketi](dotnet-pack.md) komutunu çalıştırarak bir NuGet paketi oluşturun:

   ```dotnetcli
   dotnet pack
   ```

   *microsoft.botsay.1.0.0.nupkg* dosyası, `<PackageOutputPath>` *microsoft.botsay.csproj* dosyasından alınan değerle tanımlanan klasörde oluşturulur ve bu örnekte *./nupkg* klasörü bulunur.
  
   Bir aracı herkese açık olarak serbest bırakmak istediğinizde, aracı ' ya `https://www.nuget.org`yükleyebilirsiniz. Araç NuGet'de kullanılabilir hale getirinince, geliştiriciler [dotnet aracı yükleme](dotnet-tool-install.md) komutunu kullanarak aracı yükleyebilir. Bu öğretici için paketi doğrudan yerel *nupkg* klasöründen yüklersiniz, böylece paketi NuGet'e yüklemenize gerek yoktur.

## <a name="troubleshoot"></a>Sorun giderme

Öğreticiyi izlerken bir hata iletisi alırsanız, [Sorun Giderme .NET Core araç kullanım sorunlarına](troubleshoot-usage-issues.md)bakın.

## <a name="next-steps"></a>Sonraki adımlar

Bu eğitimde, bir konsol uygulaması oluşturdunuz ve bir araç olarak paketlediniz. Aracı genel bir araç olarak nasıl kullanacağınızı öğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Genel araç yükleyip kullanma](global-tools-how-to-use.md)

İsterseniz, genel araçlar öğretici atlayabilir ve doğrudan yerel araçlar öğretici gidin.

> [!div class="nextstepaction"]
> [Yerel araç yükleyip kullanma](local-tools-how-to-use.md)
