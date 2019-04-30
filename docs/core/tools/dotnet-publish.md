---
title: DotNet yayımlama komutu
description: Dotnet yayımlama komutu, .NET Core projesi bir dizine yayımlar.
ms.date: 05/29/2018
ms.openlocfilehash: 24490bd0fbfca65692d7025b5ed2aea659c35473
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648691"
---
# <a name="dotnet-publish"></a>DotNet yayımlama

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet publish` -Bir klasöre dağıtım barındıran sistemde için uygulama ve onun bağımlılıklarını paketleri.

## <a name="synopsis"></a>Synopsis

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>Açıklama

`dotnet publish` uygulamayı derler, bağımlılıkları proje dosyasında belirtilen aracılığıyla okur ve bir dizine dosya sonuç kümesini yayımlar. Çıktı aşağıdaki varlıklar içerir:

* Ara dil (IL) kodu ile bir derlemede bir *dll* uzantısı.
* *. deps.json* tüm proje bağımlılıklarını içeren dosya.
* *. runtime.config.json* dosyası çalışma zamanı (örneğin, çöp toplama türü) için diğer yapılandırma seçenekleri yanı sıra uygulamanın beklediği paylaşılan çalışma zamanı belirtir.
* Uygulama bağımlılıklarınızın NuGet önbellekten çıktı klasörüne kopyalanır.

`dotnet publish` Komut çıkışında, bir barındırma sistemine dağıtımı için hazır (örneğin, bir sunucu, PC, Mac, dizüstü) yürütme için. Bu uygulama dağıtım için hazırlamak için yalnızca resmi olarak desteklenen yoludur. Proje belirten bir dağıtım türü, bağlı olarak .NET Core çalışma zamanı yüklü paylaşılmayan sahip veya ana bilgisayar sistemi olabilir. Daha fazla bilgi için [.NET Core uygulaması dağıtımını](../deploying/index.md). Yayımlanmış bir uygulamanın dizin yapısı için bkz. [dizin yapısı](/aspnet/core/hosting/directory-structure).

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Arguments

`PROJECT`

Yayımlanacak projeyi. Yol ve dosya adı olan bir [ C# ](csproj.md), F#, veya Visual Basic proje dosyası ya da içeren dizinin yolunu bir C#, F#, veya Visual Basic proje dosyası. Belirtilmezse, geçerli dizin için varsayılan olarak.

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Belirtilen uygulamanın yayınlar [hedef Framework'ü](../../standard/frameworks.md). Hedef Çerçeve proje dosyasında belirtmeniz gerekir.

`--force`

Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar. Bu bayrak belirten aynıdır silme *project.assets.json* dosya.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--manifest <PATH_TO_MANIFEST_FILE>`

Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla birlikte yayımlanan paketleri kümesini kırpmak için kullanılacak. Bildirim dosyası çıktısını bir parçasıdır [ `dotnet store` komut](dotnet-store.md). Birden çok bildirimleri belirtmek için bir `--manifest` her bildirimi seçeneği. Bu seçenek, .NET Core 2.0 SDK'sı ile başlayan kullanılabilir.

`--no-build`

Yayımlamadan önce projenizi değil. Ayrıca örtülü olarak ayarlar `--no-restore` bayrağı.

`--no-dependencies`

Projeden projeye başvurular yoksayar ve yalnızca kök proje geri yükler.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çıktı dizini yolunu belirtir. Belirtilmezse, varsayılan *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi başına dağıtım.
Yolun göreli olduğuna, proje dosyasının konumunu değil geçerli çalışma dizinine göre oluşturulan çıktı dizini olur.

`--self-contained`

Çalışma zamanı hedef makinede yüklü olması gerekmez .NET Core çalışma zamanı, uygulamanız ile yayımlar. Bir çalışma zamanı tanımlayıcısı belirtilmezse, varsayılan değerdir `true`. Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Belirli bir çalışma zamanı için uygulamanın yayınlar. Bu oluştururken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd). Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md). Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürümü alanında.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Belirtilen uygulamanın yayınlar [hedef Framework'ü](../../standard/frameworks.md). Hedef Çerçeve proje dosyasında belirtmeniz gerekir.

`--force`

Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar. Bu bayrak belirten aynıdır silme *project.assets.json* dosya.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--manifest <PATH_TO_MANIFEST_FILE>`

Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla birlikte yayımlanan paketleri kümesini kırpmak için kullanılacak. Bildirim dosyası çıktısını bir parçasıdır [ `dotnet store` komut](dotnet-store.md). Birden çok bildirimleri belirtmek için bir `--manifest` her bildirimi seçeneği. Bu seçenek, .NET Core 2.0 SDK'sı ile başlayan kullanılabilir.

`--no-dependencies`

Projeden projeye başvurular yoksayar ve yalnızca kök proje geri yükler.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çıktı dizini yolunu belirtir. Belirtilmezse, varsayılan *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi başına dağıtım.
Yolun göreli olduğuna, proje dosyasının konumunu değil geçerli çalışma dizinine göre oluşturulan çıktı dizini olur.

`--self-contained`

Çalışma zamanı hedef makinede yüklü olması gerekmez .NET Core çalışma zamanı, uygulamanız ile yayımlar. Bir çalışma zamanı tanımlayıcısı belirtilmezse, varsayılan değerdir `true`. Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Belirli bir çalışma zamanı için uygulamanın yayınlar. Bu oluştururken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd). Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md). Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürümü alanında.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Belirtilen uygulamanın yayınlar [hedef Framework'ü](../../standard/frameworks.md). Hedef Çerçeve proje dosyasında belirtmeniz gerekir.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--manifest <PATH_TO_MANIFEST_FILE>`

Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla birlikte yayımlanan paketleri kümesini kırpmak için kullanılacak. Bildirim dosyası çıktısını bir parçasıdır [ `dotnet store` komut](dotnet-store.md). Birden çok bildirimleri belirtmek için bir `--manifest` her bildirimi seçeneği. Bu seçenek, .NET Core 2.0 SDK'sı ile başlayan kullanılabilir.

`-o|--output <OUTPUT_DIRECTORY>`

Çıktı dizini yolunu belirtir. Belirtilmezse, varsayılan *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi başına dağıtım.
Yolun göreli olduğuna, proje dosyasının konumunu değil geçerli çalışma dizinine göre oluşturulan çıktı dizini olur.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Belirli bir çalışma zamanı için uygulamanın yayınlar. Bu oluştururken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd). Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md). Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürümü alanında.

---

## <a name="examples"></a>Örnekler

Projenin geçerli dizinde yayımlama:

`dotnet publish`

Belirtilen proje dosyasını kullanarak uygulama yayımlama:

`dotnet publish ~/projects/app1/app1.csproj`

Projenin geçerli kullanarak dizin yayımlama `netcoreapp1.1` framework:

`dotnet publish --framework netcoreapp1.1`

Geçerli kullanarak uygulama yayımlama `netcoreapp1.1` çerçevesi ve çalışma zamanı için `OS X 10.10` (proje dosyasında bu RID listelemesi gerekir).

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

Geçerli uygulama yayımlama ancak projeden projeye (P2P) başvurular, yalnızca kök projesi (.NET Core SDK 2.0 ve sonraki sürümler) geri yükleme işlemi sırasında geri yükleme:

`dotnet publish --no-dependencies`

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef çerçeveler](../../standard/frameworks.md)
- [Çalışma zamanı tanımlayıcı (RID) Kataloğu](../rid-catalog.md)
