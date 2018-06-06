---
title: DotNet paketi command - .NET Core CLI
description: Dotnet paketi komut .NET Core projeniz için NuGet paketleri oluşturur.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8c2569ec7598b21fe9b673176143d0e54b9eb065
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696825"
---
# <a name="dotnet-pack"></a>DotNet paketi

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet pack` -Kod bir NuGet paketi paketler.

## <a name="synopsis"></a>Özet

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

`dotnet pack` Komutu Proje oluşturulur ve NuGet paketleri oluşturur. Bu komut bir NuGet paketi sonucudur. Varsa `--include-symbols` seçeneği varsa, hata ayıklama simgeleri içeren başka bir paket oluşturulur.

Paketlenmiş projenizin NuGet bağımlılıkları eklenir *.nuspec* düzgün bulunmaları dosya çözülmüş paketi yüklendiğinde. Proje Proje başvuruları projesi içinde paketlenmiş değil. Şu anda proje proje bağımlılıkları varsa, her proje bir paket olması gerekir.

Varsayılan olarak, `dotnet pack` projeyi ilk oluşturur. Bu davranışı önlemek isterseniz, geçirmek `--no-build` seçeneği. Bu seçenek genellikle burada kodu daha önce oluşturulmuş bildiğiniz sürekli tümleştirme (CI) yapı senaryolarda kullanışlıdır.

MSBuild özellikleri sağlayabilir `dotnet pack` paketleme işleminin komutu. Daha fazla bilgi için bkz: [NuGet meta veri özelliklerini](csproj.md#nuget-metadata-properties) ve [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference). [Örnekler](#examples) bölüm nasıl MSBuild /p anahtarını birkaç farklı senaryo için kullanılacağını gösterir.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Arguments

`PROJECT`

Paketi projesi. Her iki yolu olan bir [csproj dosya](csproj.md) veya bir dizin. Belirtilmezse, geçerli dizine varsayılan olur.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug` şeklindedir.

`--force`

Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar. Bu bayrak belirten aynıdır silme *project.assets.json* dosya.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--include-source`

NuGet paketi kaynak dosyaları içerir. Kaynakları dosyaları içinde yer alan `src` klasör içinde `nupkg`.

`--include-symbols`

Simgeler oluşturur `nupkg`.

`--no-build`

Paketleme önce projeyi derleme değil. Ayrıca örtük ayarlar `--no-restore` bayrağı.

`--no-dependencies`

Proje Proje başvuruları yoksayar ve yalnızca kök proje geri yükler.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken yürütmez.

`-o|--output <OUTPUT_DIRECTORY>`

Belirtilen dizinde yerleşik paketleri yerleştirir.

`--runtime <RUNTIME_IDENTIFIER>`

Paketler için geri yüklemek için hedef çalışma zamanı belirtir. Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).

`-s|--serviceable`

Pakette hizmet verilebilen bayrağını ayarlar. Daha fazla bilgi için bkz: [.NET Blog: .NET 4.5.1'in destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıkları](https://aka.ms/nupkgservicing).

`--version-suffix <VERSION_SUFFIX>`

Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug` şeklindedir.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--include-source`

NuGet paketi kaynak dosyaları içerir. Kaynakları dosyaları içinde yer alan `src` klasör içinde `nupkg`.

`--include-symbols`

Simgeler oluşturur `nupkg`.

`--no-build`

Paketleme önce projeyi derleme değil.

`-o|--output <OUTPUT_DIRECTORY>`

Belirtilen dizinde yerleşik paketleri yerleştirir.

`-s|--serviceable`

Pakette hizmet verilebilen bayrağını ayarlar. Daha fazla bilgi için bkz: [.NET Blog: .NET 4.5.1'in destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıkları](https://aka.ms/nupkgservicing).

`--version-suffix <VERSION_SUFFIX>`

Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

---

## <a name="examples"></a>Örnekler

Proje geçerli dizinde paketi:

`dotnet pack`

Paketi `app1` proje:

`dotnet pack ~/projects/app1/project.csproj`

Geçerli dizinde projenin Paketle ve sonuçta elde edilen paketlere yerleştirin `nupkgs` klasörü:

`dotnet pack --output nupkgs`

Geçerli dizine içinde proje paketi `nupkgs` klasörü ve derleme adımı atla:

`dotnet pack --no-build --output nupkgs`

Proje ile Sürüm soneki olarak yapılandırılmış `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` içinde *.csproj* dosyası, geçerli projenin paketi ve sonuçta elde edilen paket sürümü verilen sonekiyle güncelleştirme:

`dotnet pack --version-suffix "ci-1234"`

Paket sürümü kümesine `2.1.0` ile `PackageVersion` MSBuild özelliği:

`dotnet pack /p:PackageVersion=2.1.0`

Belirli bir projenin paketi [hedef framework](../../standard/frameworks.md):

`dotnet pack /p:TargetFrameworks=net45`

Proje paketi ve geri yükleme işlemi (.NET Core SDK 2.0 ve sonraki sürümler) belirli bir çalışma zamanı (Windows 10) kullanın:

`dotnet pack --runtime win10-x64`