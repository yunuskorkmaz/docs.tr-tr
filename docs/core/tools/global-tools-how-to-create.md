---
title: .NET Core küresel aracı oluşturma
description: Genel bir aracın nasıl oluşturulacağını açıklar. Genel araç, .NET Core CLI aracılığıyla yüklenen bir konsol uygulamasıdır.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 1daecf7234f02a5fe0dcf25cf7edbb0af327b8c1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343518"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>.NET Core CLI kullanarak bir .NET Core genel aracı oluşturun

Bu makalede bir .NET Core küresel aracı oluşturma ve paketleme hakkında öğretilir. .NET Core CLI, bir konsol uygulamasını küresel bir araç olarak oluşturmanıza olanak tanır. Bu, başkalarının kolayca yükleyip çalıştırabilmesini sağlar. .NET Core küresel araçları, .NET Core CLI yüklenen NuGet paketlerdir. Küresel araçlar hakkında daha fazla bilgi için bkz. [.NET Core genel araçlarına genel bakış](global-tools.md).

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>Proje oluştur

Bu makale bir proje oluşturmak ve yönetmek için .NET Core CLI kullanır.

Örnek aracımız, bir ASCII bot üreten ve bir ileti yazdıran bir konsol uygulaması olacaktır. İlk olarak, yeni bir .NET Core konsol uygulaması oluşturun.

```dotnetcli
dotnet new console -o botsay
```

Önceki komut tarafından oluşturulan `botsay` dizinine gidin.

## <a name="add-the-code"></a>Kod ekleme

`Program.cs` dosyasını `vim` veya [Visual Studio Code](https://code.visualstudio.com/)gibi en sevdiğiniz metin düzenleyicinizle açın.

Aşağıdaki `using` yönergesini dosyanın en üstüne ekleyin, bu, uygulamanın sürüm bilgilerini göstermek için kodu kısaltmanıza yardımcı olur.

```csharp
using System.Reflection;
```

Sonra `Main` yöntemine gidin. Yöntemi, uygulamanız için komut satırı bağımsız değişkenlerini işlemek üzere aşağıdaki kodla değiştirin. Bağımsız değişken geçirilmemişse, kısa bir yardım iletisi görüntülenir. Aksi takdirde, bu bağımsız değişkenlerin tümü bir dizeye dönüştürülür ve bot ile birlikte yazdırılır.

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

Sonra, bir dize parametresi alan `ShowBot` adlı yeni bir yöntem ekleyin. Bu yöntem, iletiyi ve ASCII bot 'ı yazdırır. Bir [dotnetbot kodu dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) örneğinden alındı.

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

Projeyi çalıştırın ve çıktıyı görüntüleyin. Farklı sonuçları görmek için komut satırında bu çeşitlemeleri deneyin:

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

`--` sınırlayıcısından sonraki tüm bağımsız değişkenler uygulamanıza geçirilir.

## <a name="set-up-the-global-tool"></a>Genel aracı ayarlama

Uygulamayı küresel bir araç olarak paketleyebilir ve dağıtabilmeniz için önce proje dosyasını değiştirmeniz gerekir. `botsay.csproj` dosyasını açın ve `<Project><PropertyGroup>` düğümüne üç yeni XML düğümü ekleyin:

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

`<PackageOutputPath>`, isteğe bağlı olsa da, bu örnekte kullanın. Ayarladığınızdan emin olun: `<PackageOutputPath>./nupkg</PackageOutputPath>`.

Ardından, uygulamanız için bir NuGet paketi oluşturun.

```dotnetcli
dotnet pack
```

`botsay.1.0.0.nupkg` dosyası, bu örnekte `./nupkg` klasörü olan `botsay.csproj` dosyasından `<PackageOutputPath>` XML değeri tarafından tanımlanan klasörde oluşturulur. Bu, yüklemeyi ve test yapmayı kolaylaştırır. Bir aracı herkese açık bir şekilde yayınlamak istediğinizde, <https://www.nuget.org>' ye yükleyin. Araç NuGet 'de kullanılabilir olduğunda, geliştiriciler [DotNet aracı install](dotnet-tool-install.md) komutunun `--global` seçeneğini kullanarak aracın Kullanıcı genelindeki bir yüklemesini gerçekleştirebilir.

Artık bir paketiniz olduğuna göre, aracı bu paketten yükleyebilirsiniz:

```dotnetcli
dotnet tool install --global --add-source ./nupkg botsay
```

`--add-source` parametresi, .NET Core CLI, NuGet paketleri için ek bir kaynak akışı olarak `./nupkg` klasörünü (`<PackageOutputPath>` klasörü) geçici olarak kullanmasını söyler. Genel araçları yükleme hakkında daha fazla bilgi için bkz. [.NET Core genel araçlarına genel bakış](global-tools.md).

Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

Artık `botsay` yazabilir ve araçtan bir yanıt alabilirsiniz.

> [!NOTE]
> Yüklemesi başarılı olduysa, ancak `botsay` komutunu kullanamazsınız, yolu yenilemek için yeni bir Terminal açmanız gerekebilir.

## <a name="remove-the-tool"></a>Aracı kaldır

Araç ile deneme tamamladıktan sonra, aşağıdaki komutla kaldırabilirsiniz:

```dotnetcli
dotnet tool uninstall -g botsay
```
