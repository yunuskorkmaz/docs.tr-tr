---
title: .NET Core genel aracı oluşturma
description: Genel bir aracı oluşturmayı açıklar. Genel aracı ile .NET Core CLI'yı yüklediğiniz bir konsol uygulamasıdır.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 3d0a64d0473f51d73892cd40633e2982c1130469
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647950"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>Bir .NET Core genel .NET Core CLI'yı kullanarak aracı oluşturma

Bu makalede nasıl oluşturulacağı ve bir .NET Core genel aracı paketlemeyi öğretir. .NET Core CLI bir konsol uygulaması olarak bir genel diğer kolayca yükleyip çalıştırabileceği Aracı'nı oluşturmanıza olanak sağlar. .NET core genel araçları, .NET Core CLI üzerinden yüklü olan NuGet paketlerdir. Genel araçları hakkında daha fazla bilgi için bkz. [.NET Core Araçları Genel genel bakış](global-tools.md).

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>Proje oluşturma

Bu makalede .NET Core CLI oluşturmak ve bir proje yönetmek üzere kullanılmaktadır.

Örnek aracımızı ASCII bot oluşturur ve bir ileti yazdıran bir konsol uygulaması olacaktır. İlk olarak, yeni bir .NET Core konsol uygulaması oluşturun.

```console
dotnet new console -o botsay
```

Gidin `botsay` önceki komutu tarafından oluşturulan dizin.

## <a name="add-the-code"></a>Kod ekleme

Açık `Program.cs` gibi sevdiğiniz bir metin düzenleyici ile dosya `vim` veya [Visual Studio Code](https://code.visualstudio.com/).

Aşağıdaki `using` dosyanın en üstüne yönergesi, bu uygulamanın sürüm bilgilerini görüntülemek için kod kısaltın yardımcı olur.

```csharp
using System.Reflection;
```

Ardından, Aşağı Taşı `Main` yöntemi. Yöntemi, uygulamanız için komut satırı bağımsız değişkenleri işlemek için aşağıdaki kod ile değiştirin. Hiçbir bağımsız değişken geçirildi, bir kısa Yardım iletisi görüntülenir. Aksi takdirde, tüm bu bağımsız değişken bir dizeye dönüştürülür ve ile bot yazdırılır.

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

### <a name="create-the-bot"></a>Bot oluşturma

Ardından, adlı yeni bir yöntem ekleyin `ShowBot` , bir dize parametresi alan. Bu yöntem, ileti ve ASCII bot out yazdırır. ASCII bot kodu alındığı [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) örnek.

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

### <a name="test-the-tool"></a>Aracı'nı test edin

Projeyi çalıştırın ve çıktıyı görürsünüz. Bu farklı sonuçlar görmek için komut satırı çeşitleri deneyin:

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

Tüm bağımsız değişkenlerden sonra `--` sınırlayıcı uygulamanıza geçirilir.

## <a name="setup-the-global-tool"></a>Genel aracı Kurulumu

Paketi ve uygulamanızı genel bir aracı olarak dağıtmak için önce proje dosyasını değiştirmeniz gerekir. Açık `botsay.csproj` dosya ve üç yeni XML düğüm ekleme `<Project><PropertyGroup>` düğüm:

- `<PackAsTool>`\
[GEREKLİ] Uygulama genel bir aracı olarak yüklenmesi için paketlendi olduğunu gösterir.

- `<ToolCommandName>`\
[İSTEĞE BAĞLI] Aracı için bir diğer ad, aksi takdirde sonra proje dosyası aracı için komut adı adlandırılacaktır. Benzersiz ve kolay bir ad yardımcı olan diğer araçlar aynı pakette ayırt seçerek bir pakette birden çok aracı olabilir.

- `<PackageOutputPath>`\
[İSTEĞE BAĞLI] NuGet paketini burada oluşturulur. NuGet paketini, .NET Core CLI genel araçları, aracı yüklemek için kullandığı ' dir.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

Olsa da `<PackageOutputPath>` isteğe bağlıdır, bu örnekte kullanın. Bunu ayarladığınızdan emin olun: `<PackageOutputPath>./nupkg</PackageOutputPath>`.

Ardından, uygulamanız için bir NuGet paketi oluşturun.

```console
dotnet pack
```

`botsay.1.0.0.nupkg` Dosyası tarafından tanımlanan klasöründe oluşturulur `<PackageOutputPath>` XML değerinden `botsay.csproj` olan bu örnekte dosyası `./nupkg` klasör. Bu, yükleme ve test etmek kolaylaştırır. Bir aracı genel olarak yayınlamak istediğinizde, karşıya <https://www.nuget.org>. Aracı üzerinde NuGet kullanılabilir olduğunda, geliştiricilerin aracını kullanarak bir kullanıcı genelinde yükleme gerçekleştirebilirsiniz `--global` seçeneği [dotnet aracı yükleme](dotnet-tool-install.md) komutu.

Bir paket olduğuna göre bu paketten aracını yükleyin:

```console
dotnet tool install --global --add-source ./nupkg botsay
```

`--add-source` Parametresi, geçici olarak kullanmak için .NET Core CLI bildirir `./nupkg` klasörü (bizim `<PackageOutputPath>` klasör) ek bir kaynak için NuGet paketlerini akış. Genel araçlarını yükleme hakkında daha fazla bilgi için bkz. [.NET Core Araçları Genel genel bakış](global-tools.md).

Yükleme başarılı olursa, aracı ve yüklü sürümü çağırmak için kullanılan komut aşağıdaki örneğe benzer gösteren bir ileti görüntülenir:

```
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

Artık türüne erişebileceğinizi `botsay` ve aracından bir yanıt alın.

> [!NOTE]
> Yükleme başarılı oldu ancak kullanamazsınız `botsay` komutunu yolu yenilemek için yeni bir terminal açmanız gerekebilir.

## <a name="remove-the-tool"></a>Aracı kaldırma

İşiniz bittiğinde aracı ile denemeler, aşağıdaki komutla kaldırabilirsiniz:

```console
dotnet tool uninstall -g botsay
```
