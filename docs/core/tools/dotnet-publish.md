---
title: dotnet publish komutu
description: Dotnet publish komutu .NET Core projenizi bir dizinde yayımlar.
ms.date: 05/29/2018
ms.openlocfilehash: 972937ac1bc32b3749d4e1b6b8874c3516f5680c
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105143"
---
# <a name="dotnet-publish"></a>dotnet publish

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet publish`-Uygulamayı ve bağımlılıklarını bir barındırma sistemine dağıtım için bir klasöre paketler.

## <a name="synopsis"></a>Özeti

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>Açıklama

`dotnet publish`uygulamayı derler, proje dosyasında belirtilen bağımlılıklarını okur ve elde edilen dosya kümesini bir dizine yayınlar. Çıktı aşağıdaki varlıkları içerir:

- *DLL* uzantılı bir derlemede ara DIL (IL) kodu.
- *. Deps. JSON* dosyası, projenin tüm bağımlılıklarını içerir.
- uygulamanın beklediği paylaşılan çalışma zamanını belirten *. runtimeconfig. JSON* dosyası, ayrıca çalışma zamanına yönelik diğer yapılandırma seçenekleri (örneğin, çöp toplama türü).
- NuGet önbelleğinden çıkış klasörüne kopyalanmış olan uygulamanın bağımlılıkları.

`dotnet publish` Komutun çıktısı, yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtıma yöneliktir. Uygulamayı dağıtıma hazırlamak için tek resmi olarak desteklenen bir yoldur. Projenin belirttiği dağıtımın türüne bağlı olarak, barındırma sisteminde .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir. Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md). Yayımlanan bir uygulamanın dizin yapısı için bkz. [Dizin yapısı](/aspnet/core/hosting/directory-structure).

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Arguments

`PROJECT`

Yayımlanacak proje. Bir [C#](csproj.md), F#veya Visual Basic proje dosyasının yolu ve dosya adı ya da C#, F#ya da Visual Basic proje dosyası içeren bir dizinin yolu. Belirtilmezse, varsayılan olarak geçerli dizini alır.

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar. Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.

`--force`

Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--manifest <PATH_TO_MANIFEST_FILE>`

Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir. Bildirim dosyası, [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır. Birden çok bildirim belirtmek için her bildirim `--manifest` için bir seçenek ekleyin. Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.

`--no-build`

Yayımlamadan önce projeyi oluşturmaz. Ayrıca `--no-restore` bayrağı örtülü olarak ayarlar.

`--no-dependencies`

Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.

`--no-restore`

Komutu çalıştırılırken örtük geri yükleme yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çıkış dizini için yolu belirtir. Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.
Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.

`--self-contained`

.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez. Bir çalışma zamanı tanımlayıcısı belirtilmişse, varsayılan değeri olur `true`. Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Uygulamayı belirli bir çalışma zamanı için yayımlar. Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd)oluşturulurken kullanılır. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)yayımlamaktır.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

`--version-suffix <VERSION_SUFFIX>`

Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek olan sürüm sonekini tanımlar.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar. Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.

`--force`

Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--manifest <PATH_TO_MANIFEST_FILE>`

Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir. Bildirim dosyası, [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır. Birden çok bildirim belirtmek için her bildirim `--manifest` için bir seçenek ekleyin. Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.

`--no-dependencies`

Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.

`--no-restore`

Komutu çalıştırılırken örtük geri yükleme yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çıkış dizini için yolu belirtir. Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.
Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.

`--self-contained`

.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez. Bir çalışma zamanı tanımlayıcısı belirtilmişse, varsayılan değeri olur `true`. Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Uygulamayı belirli bir çalışma zamanı için yayımlar. Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd)oluşturulurken kullanılır. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)yayımlamaktır.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

`--version-suffix <VERSION_SUFFIX>`

Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek olan sürüm sonekini tanımlar.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar. Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--manifest <PATH_TO_MANIFEST_FILE>`

Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir. Bildirim dosyası, [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır. Birden çok bildirim belirtmek için her bildirim `--manifest` için bir seçenek ekleyin. Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.

`-o|--output <OUTPUT_DIRECTORY>`

Çıkış dizini için yolu belirtir. Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.
Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Uygulamayı belirli bir çalışma zamanı için yayımlar. Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd)oluşturulurken kullanılır. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)yayımlamaktır.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

`--version-suffix <VERSION_SUFFIX>`

Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek olan sürüm sonekini tanımlar.

---

## <a name="examples"></a>Örnekler

Projeyi geçerli dizinde yayımlayın:

`dotnet publish`

Belirtilen proje dosyasını kullanarak uygulamayı yayımlayın:

`dotnet publish ~/projects/app1/app1.csproj`

Şu `netcoreapp1.1` Framework 'ü kullanarak projeyi geçerli dizinde yayımlayın:

`dotnet publish --framework netcoreapp1.1`

`netcoreapp1.1` Çerçevesini ve`OS X 10.10` çalışma zamanını kullanarak geçerli uygulamayı yayımlayın (Bu RID 'yi proje dosyasında listemalısınız).

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

Geçerli uygulamayı yayımlayın ancak projeden projeye (P2P) başvurularını geri yüklemeyin, ancak geri yükleme işlemi sırasında yalnızca kök proje (.NET Core SDK 2,0 ve üzeri sürümler):

`dotnet publish --no-dependencies`

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef çerçeveler](../../standard/frameworks.md)
- [Çalışma zamanı tanımlayıcı (RID) kataloğu](../rid-catalog.md)
