---
title: DotNet restore komutu - .NET Core CLI
description: "Bağımlılıklar ve projeye özgü araçları dotnet restore komutu ile geri yüklemeyi öğrenin."
keywords: DotNet-restore, CLI, CLI komutu, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 82a78dcb0cc85e2ba087b6df5ee029cbfb687358
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-restore"></a>DotNet geri yükleme

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet restore`-Bir projenin araçları ve bağımlılıklar geri yükler.

## <a name="synopsis"></a>Özet

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a>Açıklama

`dotnet restore` Komutu proje dosyasında belirtilen projeye özel araçlar yanı sıra bağımlılıkları geri yüklemek için NuGet kullanır. Varsayılan olarak, bağımlılıklar ve araçları geri paralel olarak gerçekleştirilir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Bağımlılıkları geri yüklemek için NuGet paketleri bulunduğu akışları gerekir. Akışları aracılığıyla genellikle sağlanan *NuGet.config* yapılandırma dosyası. CLI araçlarını yüklendiğinde varsayılan yapılandırma dosyası sağlanır. Kendi oluşturarak ek akışları belirttiğiniz *NuGet.config* proje dizininde dosya. Ayrıca, bir komut isteminde çağrı başına ek akışları belirtin.

Bağımlılıklar için geri yüklenen paketler geri yükleme işlemini kullanarak sırasında yerleştirildiği belirtin `--packages` bağımsız değişkeni. Belirtilmezse, varsayılan NuGet paketi önbelleği, içinde bulunan kullanılıp kullanılmadığını `.nuget/packages` tüm işletim sistemlerinde kullanıcının giriş dizini, dizin (örneğin, */home/kullanıcı1* Linux'ta veya *C:\Users\user1*  Windows'da).

Projeye özgü araçları için `dotnet restore` önce aracı paketlenmiştir ve proje dosyasında belirtildiği gibi aracın bağımlılıkları geri sürdürüleceği paketini yükler.

Davranışını `dotnet restore` komut ayarlarında bazıları tarafından etkilenir *Nuget.Config* varsa dosya. Örneğin, ayarlama `globalPackagesFolder` içinde *NuGet.Config* belirtilen klasörde geri yüklenen NuGet paketleri yerleştirir. Bu belirtme alternatiftir `--packages` seçeneği `dotnet restore` komutu. Daha fazla bilgi için bkz: [NuGet.Config başvuru](/nuget/schema/nuget-config-file).

## <a name="arguments"></a>Arguments

`ROOT`

Proje dosyasını geri yüklemek için isteğe bağlı bir yoldur.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`--configfile <FILE>`

NuGet yapılandırma dosyası (*NuGet.config*) geri yükleme işlemi için kullanılacak.

`--disable-parallel`

Paralel olarak birden çok proje geri yükleme devre dışı bırakır.

`--force`

Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar. Bu silme ile eşdeğerdir *project.assets.json* dosya.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--ignore-failed-sources`

Paket sürümü gereksinimini toplantı varsa yalnızca başarısız kaynakları hakkında uyarır.

`--no-cache`

Paketler ve HTTP isteklerini önbelleğe almaz belirtir.

`--no-dependencies`

Proje Proje (P2P) başvuruları içeren bir proje geri yüklerken, kök proje ve başvuru geri yükler.

`--packages <PACKAGES_DIRECTORY>`

Geri yüklenen paketler dizinini belirtir.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Paket geri yüklemesi için bir çalışma zamanı belirtir. Bu çalışma zamanları açıkça listelenen paketlerini geri yüklemek için kullanılan `<RuntimeIdentifiers>` içinde etiketi *.csproj* dosya. Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md). Bu seçeneği birden çok kez belirterek birden fazla RID sağlar.

`-s|--source <SOURCE>`

Geri yükleme işlemi sırasında kullanmak için NuGet paket kaynağını belirtir. Bu belirtilen kaynakları tüm geçersiz kılmaları *NuGet.config* olmalıdır. Bu seçeneği birden çok kez belirterek birden çok kaynak sağlanabilir.

`--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--configfile <FILE>`

NuGet yapılandırma dosyası (*NuGet.config*) geri yükleme işlemi için kullanılacak.

`--disable-parallel`

Paralel olarak birden çok proje geri yükleme devre dışı bırakır.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--ignore-failed-sources`

Paket sürümü gereksinimini toplantı varsa yalnızca başarısız kaynakları hakkında uyarır.

`--no-cache`

Paketler ve HTTP isteklerini önbelleğe almaz belirtir.

`--no-dependencies`

Proje Proje (P2P) başvuruları içeren bir proje geri yüklerken, kök proje ve başvuru geri yükler.

`--packages <PACKAGES_DIRECTORY>`

Geri yüklenen paketler dizinini belirtir.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Paket geri yüklemesi için bir çalışma zamanı belirtir. Bu çalışma zamanları açıkça listelenen paketlerini geri yüklemek için kullanılan `<RuntimeIdentifiers>` içinde etiketi *.csproj* dosya. Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md). Bu seçeneği birden çok kez belirterek birden fazla RID sağlar.

`-s|--source <SOURCE>`

Geri yükleme işlemi sırasında kullanmak için NuGet paket kaynağını belirtir. Bu belirtilen kaynakları tüm geçersiz kılmaları *NuGet.config* olmalıdır. Bu seçeneği birden çok kez belirterek birden çok kaynak sağlanabilir.

`--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

## <a name="examples"></a>Örnekler

Bağımlılıklar ve geçerli dizinde proje için araçları geri yükleyin:

`dotnet restore`

Bağımlılıklar ve araçları için geri `app1` proje verilen yolda bulunamadı:

`dotnet restore ~/projects/app1/app1.csproj`

Kaynak olarak sağlanan dosya yolunu kullanarak geçerli dizinde projesi için Araçlar ve bağımlılıklar geri yükleyin:

`dotnet restore -s c:\packages\mypackages`

Kaynakları olarak sağlanan iki dosya yolları kullanarak geçerli dizinde projesi için Araçlar ve bağımlılıklar geri yükleyin:

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Bağımlılıklar ve geçerli dizin ve programlarını yalnızca en az çıkış projede için araçları geri yükleyin:

`dotnet restore --verbosity minimal`
