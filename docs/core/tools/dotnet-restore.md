---
title: DotNet restore komutu - .NET Core CLI
description: Bağımlılıklar ve projeye özgü araçları dotnet restore komutu ile geri yüklemeyi öğreneceksiniz.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 0eaab1aa1bc52bd5b3c51a6ed2dd7a59c35a4aa5
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960602"
---
# <a name="dotnet-restore"></a>DotNet restore

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet restore` -Bir projenin Araçlar ve bağımlılıkları yükler.

## <a name="synopsis"></a>Özeti

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
---

## <a name="description"></a>Açıklama

`dotnet restore` Komutu, proje dosyasında belirtilen projeye özgü araçları yanı sıra bağımlılıkları geri yüklemek için NuGet kullanır. Varsayılan olarak, Araçlar ile bağımlılıkları ve geri yükleme işlemi paralel olarak yürütülür.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Bağımlılıkları geri yüklemek için NuGet paketlerinin yer aldığı akışları gerekir. Akışları aracılığıyla genellikle sağlanan *NuGet.config* yapılandırma dosyası. CLI araçları yüklü olduğunda varsayılan yapılandırma dosyası sağlanır. Kendi oluşturarak ek akışları belirttiğiniz *NuGet.config* dosya proje dizininde. Bir komut isteminde çağrı başına ek akışları de belirtirsiniz.

Bağımlılıklar için geri yüklenen paketler geri yükleme kullanarak işlemi sırasında yerleştirildiği belirtin `--packages` bağımsız değişken. Belirtilmezse, varsayılan NuGet paket önbelleğini, içinde geçtiği yerin kullanılıp kullanılmadığını `.nuget/packages` dizini ile tüm işletim sistemlerinde kullanıcının ana dizini. Örneğin, */home/user1* Linux üzerinde veya *C:\Users\user1* Windows üzerinde.

Projeye özgü araçları için `dotnet restore` öncelikle hangi aracın iyileştirmesiyle doludur ve kendi proje dosyasında belirtilen Aracı'nın bağımlılıkları geri yüklemek için devam eder paket geri yükler.

Davranışını `dotnet restore` komut bazı ayarlar tarafından etkilendi *Nuget.Config* varsa, dosya. Örneğin, ayarlamak `globalPackagesFolder` içinde *NuGet.Config* belirtilen klasörde NuGet paketlerini geri yerleştirir. Bu belirten bir alternatifidir `--packages` seçeneğini `dotnet restore` komutu. Daha fazla bilgi için [NuGet.Config başvuru](/nuget/schema/nuget-config-file).

## <a name="implicit-dotnet-restore"></a>Örtük `dotnet restore`

.NET Core 2.0 ile başlayarak `dotnet restore` aşağıdaki komutları gönderdiğinizde gerekirse örtük olarak çalıştırılan:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Çoğu durumda, artık açıkça kullanmanız gerekir `dotnet restore` komutu.

Bazı durumlarda, çalıştırılacak kullanışsız olabilir `dotnet restore` örtük olarak. Örneğin, yapı sistemi gibi bazı otomatik sistemler çağırmanız gerekir `dotnet restore` açıkça ağ kullanımını kontrol edebilir, böylece geri yükleme ne zaman gerçekleştiğini denetlemek için. Önlemek için `dotnet restore` kullanabileceğiniz örtük olarak çalıştırılmasının `--no-restore` örtük geri yükleme devre dışı bırakmak için aşağıdaki komutlardan birini bayrağıyla.

## <a name="arguments"></a>Arguments

`ROOT`

İsteğe bağlı geri yüklemek için proje dosyasının yolu.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`--configfile <FILE>`

NuGet yapılandırma dosyası (*NuGet.config*) geri yükleme işlemi için kullanılacak.

`--disable-parallel`

Paralel olarak birden çok proje geri yükleme devre dışı bırakır.

`--force`

Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar. Bu bayrak belirten aynıdır silme *project.assets.json* dosya.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--ignore-failed-sources`

Yalnızca sürüm gereksinimi Karşılama paketleri varsa başarısız kaynakları hakkında uyar.

`--no-cache`

Paketler ve HTTP isteklerini önbelleğe belirtir.

`--no-dependencies`

Projeden projeye (P2P) başvurular içeren bir proje geri yüklerken, kök proje ve başvuruları geri yükler.

`--packages <PACKAGES_DIRECTORY>`

Geri yüklenen paketler için dizini belirtir.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Paket geri yükleme için bir çalışma zamanı belirtir. Bu açıkça listelenen çalışma zamanları için paketler geri yüklemek için kullanılan `<RuntimeIdentifiers>` içindeki *.csproj* dosya. Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md). Bu seçeneği birden çok kez belirterek, birden fazla RID sağlar.

`-s|--source <SOURCE>`

Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağı belirtir. Bu ayar tüm kaynakları belirtilen geçersiz kılmaları *NuGet.config* dosyaları. Bu seçeneği birden çok kez belirterek, birden çok kaynaktan sağlanabilir.

`--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--configfile <FILE>`

NuGet yapılandırma dosyası (*NuGet.config*) geri yükleme işlemi için kullanılacak.

`--disable-parallel`

Paralel olarak birden çok proje geri yükleme devre dışı bırakır.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--ignore-failed-sources`

Yalnızca sürüm gereksinimi Karşılama paketleri varsa başarısız kaynakları hakkında uyar.

`--no-cache`

Paketler ve HTTP isteklerini önbelleğe belirtir.

`--no-dependencies`

Projeden projeye (P2P) başvurular içeren bir proje geri yüklerken, kök proje ve başvuruları geri yükler.

`--packages <PACKAGES_DIRECTORY>`

Geri yüklenen paketler için dizini belirtir.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Paket geri yükleme için bir çalışma zamanı belirtir. Bu açıkça listelenen çalışma zamanları için paketler geri yüklemek için kullanılan `<RuntimeIdentifiers>` içindeki *.csproj* dosya. Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md). Bu seçeneği birden çok kez belirterek, birden fazla RID sağlar.

`-s|--source <SOURCE>`

Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağı belirtir. Bu kaynakları belirtilen tüm geçersiz kılmaları *NuGet.config* dosyaları. Bu seçeneği birden çok kez belirterek, birden çok kaynaktan sağlanabilir.

`--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

## <a name="examples"></a>Örnekler

Bağımlılıklar ve geçerli dizinde proje için araçları geri yükleme:

`dotnet restore`

Bağımlılıklar ve araçlar için geri `app1` proje verilen yolda bulunamadı:

`dotnet restore ~/projects/app1/app1.csproj`

Kaynak olarak sağlanan dosya yolunu kullanarak geçerli dizinde proje için Araçlar ve bağımlılıklar geri yükleme:

`dotnet restore -s c:\packages\mypackages`

Kaynakları olarak sağlanan iki dosya yolları kullanarak geçerli dizinde proje için Araçlar ve bağımlılıklar geri yükleme:

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Bağımlılıklar ve araçlar için geçerli dizin ve programlarını yalnızca en az çıktı projede geri yükleme:

`dotnet restore --verbosity minimal`
