---
title: DotNet paketi command - .NET Core CLI
description: Dotnet paketi komut, .NET Core projesi için NuGet paketlerini oluşturur.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 434f1c97af24d1417cd79edd52b63814fd4c6512
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231194"
---
# <a name="dotnet-pack"></a>DotNet paketi

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet pack` -Kod bir NuGet paketine paketleri.

## <a name="synopsis"></a>Özeti

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a>Açıklama

`dotnet pack` Komut projeyi derler ve NuGet paketleri oluşturur. Bu komutun sonucuna ilişkin bir NuGet paketidir. Varsa `--include-symbols` seçeneği varsa, hata ayıklama sembolleri içeren başka bir paket oluşturulur.

Paketlenmiş proje, NuGet bağımlılıklarını eklenir *.nuspec* düzgün bulunmaları dosyası, çözümlenen paketi yüklendiğinde. Projeden projeye başvurular projesi içinde paketlendi değildir. Şu anda projeden projeye bağımlılıkları varsa, her proje bir paket olmalıdır.

Varsayılan olarak, `dotnet pack` önce projeyi oluşturur. Bu davranışı engellemek istiyorsanız, geçmesi `--no-build` seçeneği. Bu seçenek genellikle kod daha önce oluşturulmuş bildiğiniz sürekli tümleştirme (CI) derleme senaryolarda yararlıdır.

MSBuild özellikleri sağlayabilir `dotnet pack` paketleme işlemi için komutu. Daha fazla bilgi için [NuGet meta veri özelliklerini](csproj.md#nuget-metadata-properties) ve [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference). [Örnekler](#examples) bölüm birkaç farklı senaryolar için MSBuild -p anahtar kullanmayı gösterir.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Arguments

`PROJECT`

Paketi için proje. Ya da bir yolu olan bir [csproj dosyasını](csproj.md) veya bir dizine. Belirtilmezse, geçerli dizin için varsayılan olarak.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`--force`

Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar. Bu bayrak belirten aynıdır silme *project.assets.json* dosya.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--include-source`

NuGet paketinin kaynak dosyaları içerir. Kaynak dosyaların dahil `src` klasördeki `nupkg`.

`--include-symbols`

Sembolleri oluşturur `nupkg`.

`--no-build`

Paketleme önce projenizi değil. Ayrıca örtülü ayarlar `--no-restore` bayrağı.

`--no-dependencies`

Projeden projeye başvurular yoksayar ve yalnızca kök proje geri yükler.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Yerleşik paketler belirtilen dizine yerleştirir.

`--runtime <RUNTIME_IDENTIFIER>`

Paketleri geri yüklemek için hedef çalışma zamanı belirtir. Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).

`-s|--serviceable`

Pakette tutulabilmesi bayrağını ayarlar. Daha fazla bilgi için [.NET Blog: .NET 4.5.1 destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıklarını](https://aka.ms/nupkgservicing).

`--version-suffix <VERSION_SUFFIX>`

Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

> [!NOTE]
> Web projeleri, varsayılan olarak packable değildir. Varsayılan davranışı geçersiz kılmak için aşağıdaki özelliği ekleyin, *.csproj* dosyası:
> ```xml
> <PropertyGroup>
>    <IsPackable>true</IsPackable>
> </PropertyGroup>
> ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--include-source`

NuGet paketinin kaynak dosyaları içerir. Kaynak dosyaların dahil `src` klasördeki `nupkg`.

`--include-symbols`

Sembolleri oluşturur `nupkg`.

`--no-build`

Paketleme önce projenizi değil.

`-o|--output <OUTPUT_DIRECTORY>`

Yerleşik paketler belirtilen dizine yerleştirir.

`-s|--serviceable`

Pakette tutulabilmesi bayrağını ayarlar. Daha fazla bilgi için [.NET Blog: .NET 4.5.1 destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıklarını](https://aka.ms/nupkgservicing).

`--version-suffix <VERSION_SUFFIX>`

Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

---

## <a name="examples"></a>Örnekler

Geçerli dizindeki proje paketi:

`dotnet pack`

Paketi `app1` proje:

`dotnet pack ~/projects/app1/project.csproj`

Geçerli dizinde proje pack ve sonuçta elde edilen paketler halinde yerleştirin `nupkgs` klasörü:

`dotnet pack --output nupkgs`

Geçerli dizinde içinde proje pack `nupkgs` klasörü ve derleme adımı atla:

`dotnet pack --no-build --output nupkgs`

Projeyle Sürüm soneki olarak yapılandırılmış `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` içinde *.csproj* dosya, geçerli proje pack ve elde edilen paket sürümü ile belirtilen sonek güncelleştirin:

`dotnet pack --version-suffix "ci-1234"`

Paket sürümü kümesine `2.1.0` ile `PackageVersion` MSBuild özelliği:

`dotnet pack -p:PackageVersion=2.1.0`

Belirli bir proje pack [hedef Framework'ü](../../standard/frameworks.md):

`dotnet pack -p:TargetFrameworks=net45`

Proje paketi ve belirli bir çalışma zamanı (Windows 10) geri yükleme işlemi için (.NET Core SDK 2.0 ve sonraki sürümler) kullanın:

`dotnet pack --runtime win10-x64`
