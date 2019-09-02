---
title: dotnet restore komutu
description: Dotnet restore komutuyla bağımlılıkları ve projeye özel araçları nasıl geri yükleyeceğinizi öğrenin.
ms.date: 05/29/2018
ms.openlocfilehash: 56d99a4edd69246632560065c415a3f41ac3e1b5
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202812"
---
# <a name="dotnet-restore"></a>dotnet restore

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet restore`-Bir projenin bağımlılıklarını ve araçlarını geri yükler.

## <a name="synopsis"></a>Özeti

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a>Açıklama

Bu `dotnet restore` komut, bağımlılıkları geri yüklemek için NuGet kullanır ve proje dosyasında belirtilen projeye özgü araçlardır. Varsayılan olarak, bağımlılıklar ve araçların geri yüklenmesi paralel olarak yürütülür.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Bağımlılıkları geri yüklemek için, NuGet paketlerin bulunduğu akışlara ihtiyaç duyuyor. Akışlar genellikle *NuGet. config* yapılandırma dosyası aracılığıyla sağlanır. CLı araçları yüklendiğinde varsayılan bir yapılandırma dosyası sağlanır. Proje dizininde kendi *NuGet. config* dosyanızı oluşturarak ek akışlar belirlersiniz. Komut isteminde her çağrı için ek akışlar da belirtirsiniz.

Bağımlılıklar için, geri yükleme işlemi sırasında `--packages` bağımsız değişkeni kullanarak geri yüklenen paketlerin nereye yerleştirileceğini belirtirsiniz. Belirtilmezse, varsayılan NuGet paketi önbelleği kullanılır ve bu, tüm işletim sistemlerindeki kullanıcının giriş dizinindeki `.nuget/packages` dizininde bulunur. Örneğin, Linux üzerinde */home/user1* veya Windows üzerinde *c:\Users\User1* .

Projeye özgü araçlar için, `dotnet restore` önce aracın paketlenmesi gereken paketi geri yükler ve ardından, araç bağımlılıklarını proje dosyasında belirtilen şekilde geri yüklemeye devam eder.

### <a name="nugetconfig-differences"></a>NuGet. config farklılıkları

`dotnet restore` Komutun davranışı, varsa *NuGet. config* dosyasındaki ayarlardan etkilenir. Örneğin, `globalPackagesFolder` *NuGet. config* içindeki ayarı, geri yüklenen NuGet paketlerini belirtilen klasöre koyar. Bu `--packages` seçenek, `dotnet restore` komutunda seçeneğini belirtmeye yönelik bir alternatiftir. Daha fazla bilgi için bkz. [NuGet. config başvurusu](/nuget/schema/nuget-config-file).

Yok sayan `dotnet restore` üç özel ayar vardır:

- [Bindingyönlendirmeler](/nuget/schema/nuget-config-file#bindingredirects-section)

  Bağlama yeniden yönlendirmeleri `<PackageReference>` öğelerle çalışmaz ve .NET Core yalnızca NuGet paketleri `<PackageReference>` için öğeleri destekler.

- [çözümden](/nuget/schema/nuget-config-file#solution-section)

  Bu ayar Visual Studio 'ya özeldir ve .NET Core için uygulanmaz. .NET Core bir `packages.config` dosya kullanmaz ve bunun yerine NuGet `<PackageReference>` paketleri için öğeleri kullanır.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  NuGet, güvenilen paketlerin [platformlar arası doğrulanmasını henüz desteklemediğinden](https://github.com/NuGet/Home/issues/7939) , bu ayar geçerli değildir.

## <a name="implicit-dotnet-restore"></a>İndirgen`dotnet restore`

.NET Core 2,0 ' den itibaren `dotnet restore` , aşağıdaki komutları verdiğinizde, gerekirse örtülü olarak çalıştırılır:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Çoğu durumda, artık `dotnet restore` komutunu açıkça kullanmanız gerekmez.

Bazen, örtülü olarak çalıştırılması `dotnet restore` uygun olmayabilir. Örneğin, derleme sistemleri gibi bazı otomatikleştirilmiş sistemlerin, ağ kullanımını denetleyebilmeleri için geri `dotnet restore` yüklemenin ne zaman gerçekleşeceğini denetlemek için açıkça çağrılması gerekir. Örtülü geri yüklemeyi devre dışı bırakmak için bu komutlardan herhangi `--no-restore` biriyle bayrağı kullanabilirsiniz. `dotnet restore`

## <a name="arguments"></a>Arguments

`ROOT`

Geri yüklenecek proje dosyasının isteğe bağlı yolu.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

`--configfile <FILE>`

Geri yükleme işlemi için kullanılacak NuGet yapılandırma dosyası (*NuGet. config*).

`--disable-parallel`

Paralel olarak birden çok projenin geri yüklenmesini devre dışı bırakır.

`--force`

Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--ignore-failed-sources`

Yalnızca sürüm gereksinimini karşılayan paketler varsa başarısız kaynaklar hakkında uyar.

`--no-cache`

Paketlerin ve HTTP isteklerinin önbelleğe alınamadı belirtir.

`--no-dependencies`

Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.

`--packages <PACKAGES_DIRECTORY>`

Geri yüklenen paketlerin dizinini belirtir.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Paket geri yüklemesi için bir çalışma zamanı belirtir. Bu, `<RuntimeIdentifiers>` *. csproj* dosyasındaki etiketinde açıkça listelenmeyen çalışma zamanları paketlerini geri yüklemek için kullanılır. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Bu seçeneği birden çok kez belirterek birden çok grup belirtin.

`-s|--source <SOURCE>`

Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağını belirtir. Bu ayar *NuGet. config* dosyalarında belirtilen tüm kaynakları geçersiz kılar. Bu seçenek birden çok kez belirtilerek birden çok kaynak sağlanarak sağlayabilirsiniz.

`--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

`--interactive`

Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya). .NET Core 2.1.400 'dan beri.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

`--configfile <FILE>`

Geri yükleme işlemi için kullanılacak NuGet yapılandırma dosyası (*NuGet. config*).

`--disable-parallel`

Paralel olarak birden çok projenin geri yüklenmesini devre dışı bırakır.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--ignore-failed-sources`

Yalnızca sürüm gereksinimini karşılayan paketler varsa başarısız kaynaklar hakkında uyar.

`--no-cache`

Paketlerin ve HTTP isteklerinin önbelleğe alınamadı belirtir.

`--no-dependencies`

Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.

`--packages <PACKAGES_DIRECTORY>`

Geri yüklenen paketlerin dizinini belirtir.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Paket geri yüklemesi için bir çalışma zamanı belirtir. Bu, `<RuntimeIdentifiers>` *. csproj* dosyasındaki etiketinde açıkça listelenmeyen çalışma zamanları paketlerini geri yüklemek için kullanılır. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Bu seçeneği birden çok kez belirterek birden çok grup belirtin.

`-s|--source <SOURCE>`

Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağını belirtir. Bu, *NuGet. config* dosyalarında belirtilen tüm kaynakları geçersiz kılar. Bu seçenek birden çok kez belirtilerek birden çok kaynak sağlanarak sağlayabilirsiniz.

`--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

---

## <a name="examples"></a>Örnekler

Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükle:

`dotnet restore`

Verilen yolda bulunan `app1` projenin bağımlılıklarını ve araçlarını geri yükleyin:

`dotnet restore ~/projects/app1/app1.csproj`

Kaynak olarak belirtilen dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:

`dotnet restore -s c:\packages\mypackages`

Kaynak olarak girilen iki dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin ve yalnızca en az çıktıyı gösterir:

`dotnet restore --verbosity minimal`
