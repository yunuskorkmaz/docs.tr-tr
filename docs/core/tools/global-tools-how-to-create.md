---
title: .NET Core küresel aracı oluşturma
description: Genel bir aracın nasıl oluşturulacağını açıklar. Genel araç, .NET Core CLI aracılığıyla yüklenen bir konsol uygulamasıdır.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: f60e26d14e89b6b7c34b32bf9a114fe4ad691981
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202769"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>.NET Core CLI kullanarak bir .NET Core genel aracı oluşturun

Bu makalede bir .NET Core küresel aracı oluşturma ve paketleme hakkında öğretilir. .NET Core CLI, bir konsol uygulamasını küresel bir araç olarak oluşturmanıza olanak tanır. Bu, başkalarının kolayca yükleyip çalıştırabilmesini sağlar. .NET Core küresel araçları, .NET Core CLI yüklenen NuGet paketlerdir. Küresel araçlar hakkında daha fazla bilgi için bkz. [.NET Core genel araçlarına genel bakış](global-tools.md).

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>Proje oluşturma

Bu makale bir proje oluşturmak ve yönetmek için .NET Core CLI kullanır.

Örnek aracımız, bir ASCII bot üreten ve bir ileti yazdıran bir konsol uygulaması olacaktır. İlk olarak, yeni bir .NET Core konsol uygulaması oluşturun.

```console
dotnet new console -o botsay
```

Önceki komutla oluşturulan dizine gidin. `botsay`

## <a name="add-the-code"></a>Kodu ekleyin

Dosyayı, `vim` veya Visual Studio Code gibi sık kullanılan metin düzenleyicinizle açın. [](https://code.visualstudio.com/) `Program.cs`

Aşağıdaki `using` yönergeyi dosyanın en üstüne ekleyin; Bu, kodun, uygulamanın sürüm bilgilerini görüntülemesi için kod kısaltmanıza yardımcı olur.

```csharp
using System.Reflection;
```

Sonra, `Main` yöntemine aşağı gidin. Yöntemi, uygulamanız için komut satırı bağımsız değişkenlerini işlemek üzere aşağıdaki kodla değiştirin. Bağımsız değişken geçirilmemişse, kısa bir yardım iletisi görüntülenir. Aksi takdirde, bu bağımsız değişkenlerin tümü bir dizeye dönüştürülür ve bot ile birlikte yazdırılır.

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

Sonra, bir dize parametresi alan adlı `ShowBot` yeni bir yöntem ekleyin. Bu yöntem, iletiyi ve ASCII bot 'ı yazdırır. Bir dotnetbot kodu [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) örneğinden alındı.

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

### <a name="test-the-tool"></a>Aracı test etme

Projeyi çalıştırın ve çıktıyı görüntüleyin. Farklı sonuçları görmek için komut satırının bu çeşitlemelerini deneyin:

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

`--` Sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulamanıza geçirilir.

## <a name="setup-the-global-tool"></a>Genel aracı kurma

Uygulamayı küresel bir araç olarak paketleyebilir ve dağıtabilmeniz için önce proje dosyasını değiştirmeniz gerekir. Dosyayı açın ve `<Project><PropertyGroup>` düğüme üç yeni XML düğümü ekleyin: `botsay.csproj`

- `<PackAsTool>`\
ISTENIR Uygulamanın genel bir araç olarak yüklenmek üzere paketleneceğine bildirir.

- `<ToolCommandName>`\
SEÇIM Araç için alternatif bir ad, aksi takdirde araç için komut adı proje dosyasından sonra adlandıralınacaktır. Pakette birden fazla araca sahip olabilirsiniz, benzersiz ve kolay bir ad seçmek aynı paketteki diğer araçlardan ayırt edilmesine yardımcı olur.

- `<PackageOutputPath>`\
SEÇIM NuGet paketinin üretileceği yer. NuGet paketi, .NET Core CLI genel araçların aracınızı yüklemek için kullandığı şeydir.

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

`<PackageOutputPath>` İsteğe bağlı olsa da, bu örnekte kullanın. Ayarladığınızdan emin olun: `<PackageOutputPath>./nupkg</PackageOutputPath>`.

Ardından, uygulamanız için bir NuGet paketi oluşturun.

```console
dotnet pack
```

Dosya, dosyadan `<PackageOutputPath>` xml değeri `botsay.csproj` tarafından tanımlanan klasörde oluşturulur, bu örnekte `./nupkg` klasörüdür. `botsay.1.0.0.nupkg` Bu, yüklemeyi ve test yapmayı kolaylaştırır. Bir aracı herkese açık bir şekilde yayınlamak istediğinizde, ' ye <https://www.nuget.org>yükleyin. Araç NuGet 'de kullanılabilir olduğunda, geliştiriciler `--global` [DotNet aracı yükleme](dotnet-tool-install.md) komutu seçeneğini kullanarak aracın Kullanıcı genelindeki bir yüklemesini gerçekleştirebilir.

Artık bir paketiniz olduğuna göre, aracı bu paketten yükleyebilirsiniz:

```console
dotnet tool install --global --add-source ./nupkg botsay
```

Parametresi, .NET Core CLI NuGet paketleri için ek bir kaynak `./nupkg` akışı olarak klasörü `<PackageOutputPath>` (klasör) geçici olarak kullanmasını söyler. `--add-source` Genel araçları yükleme hakkında daha fazla bilgi için bkz. [.NET Core genel araçlarına genel bakış](global-tools.md).

Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

Artık araçtan bir yanıt yazabilir `botsay` ve yanıt alabilirsiniz.

> [!NOTE]
> Yüklemenin başarılı olması, ancak `botsay` komutunu kullanmanızın ardından, yolu yenilemek için yeni bir Terminal açmanız gerekebilir.

## <a name="remove-the-tool"></a>Aracı kaldır

Araç ile deneme tamamladıktan sonra, aşağıdaki komutla kaldırabilirsiniz:

```console
dotnet tool uninstall -g botsay
```
