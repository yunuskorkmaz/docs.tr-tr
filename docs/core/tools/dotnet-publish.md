---
title: dotnet publish komutu
description: Dotnet publish komutu .NET Core projenizi bir dizinde yayımlar.
ms.date: 05/29/2018
ms.openlocfilehash: 88dc53d6c45bc18f630d8a7137704e813ad4f0e3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626079"
---
# <a name="dotnet-publish"></a>dotnet publish

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Adı

uygulama ve bağımlılıklarını bir barındırma sistemine dağıtım için bir klasöre `dotnet publish` paketler.

## <a name="synopsis"></a>Özeti

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[.NET Core 2,1](#tab/netcore21)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20"></a>[.NET Core 2,0](#tab/netcore20)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1x"></a>[.NET Core 1. x](#tab/netcore1x)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>Açıklama

`dotnet publish` uygulamayı derler, proje dosyasında belirtilen bağımlılıklarını okur ve elde edilen dosya kümesini bir dizine yayınlar. Çıktı aşağıdaki varlıkları içerir:

- *DLL* uzantılı bir derlemede ara DIL (IL) kodu.
- *. Deps. JSON* dosyası, projenin tüm bağımlılıklarını içerir.
- uygulamanın beklediği paylaşılan çalışma zamanını belirten *. runtimeconfig. JSON* dosyası, ayrıca çalışma zamanına yönelik diğer yapılandırma seçenekleri (örneğin, çöp toplama türü).
- NuGet önbelleğinden çıkış klasörüne kopyalanmış olan uygulamanın bağımlılıkları.

`dotnet publish` komutun çıktısı, yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtıma yöneliktir. Uygulamayı dağıtıma hazırlamak için tek resmi olarak desteklenen bir yoldur. Projenin belirttiği dağıtımın türüne bağlı olarak, barındırma sisteminde .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir. Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md). Yayımlanan bir uygulamanın dizin yapısı için bkz. [Dizin yapısı](/aspnet/core/hosting/directory-structure).

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT`

Yayımlanacak proje. Bir [C#](csproj.md), F#veya Visual Basic proje dosyasının yolu ve dosya adı ya da C#, F#ya da Visual Basic proje dosyası içeren bir dizinin yolu. Belirtilmezse, varsayılan olarak geçerli dizini alır.

## <a name="options"></a>Seçenekler

# <a name="net-core-21"></a>[.NET Core 2,1](#tab/netcore21)

`-c|--configuration <CONFIGURATION>`

Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.

`-f|--framework <FRAMEWORK>`

Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar. Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.

`--force`

Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--manifest <PATH_TO_MANIFEST_FILE>`

Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir. Bildirim dosyası [`dotnet store` komutunun](dotnet-store.md)çıktısının bir parçasıdır. Birden çok bildirim belirtmek için her bildirim için bir `--manifest` seçeneği ekleyin. Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.

`--no-build`

Yayımlamadan önce projeyi oluşturmaz. Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.

`--no-dependencies`

Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.

`--no-restore`

Komutu çalıştırılırken örtük geri yükleme yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çıkış dizini için yolu belirtir. Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.
Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.

`--self-contained`

.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez. Bir çalışma zamanı tanımlayıcısı belirtilmişse, varsayılan değeri `true`. Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Uygulamayı belirli bir çalışma zamanı için yayımlar. Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#publish-self-contained)oluşturulurken kullanılır. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#publish-runtime-dependent)yayımlamaktır.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek sürüm sonekini tanımlar.

# <a name="net-core-20"></a>[.NET Core 2,0](#tab/netcore20)

`-c|--configuration <CONFIGURATION>`

Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.

`-f|--framework <FRAMEWORK>`

Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar. Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.

`--force`

Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--manifest <PATH_TO_MANIFEST_FILE>`

Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir. Bildirim dosyası [`dotnet store` komutunun](dotnet-store.md)çıktısının bir parçasıdır. Birden çok bildirim belirtmek için her bildirim için bir `--manifest` seçeneği ekleyin. Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.

`--no-dependencies`

Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.

`--no-restore`

Komutu çalıştırılırken örtük geri yükleme yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çıkış dizini için yolu belirtir. Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.
Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.

`--self-contained`

.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez. Bir çalışma zamanı tanımlayıcısı belirtilmişse, varsayılan değeri `true`. Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Uygulamayı belirli bir çalışma zamanı için yayımlar. Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#publish-self-contained)oluşturulurken kullanılır. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#publish-runtime-dependent)yayımlamaktır.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek sürüm sonekini tanımlar.

# <a name="net-core-1x"></a>[.NET Core 1. x](#tab/netcore1x)

`-c|--configuration <CONFIGURATION>`

Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.

`-f|--framework <FRAMEWORK>`

Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar. Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--manifest <PATH_TO_MANIFEST_FILE>`

Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir. Bildirim dosyası [`dotnet store` komutunun](dotnet-store.md)çıktısının bir parçasıdır. Birden çok bildirim belirtmek için her bildirim için bir `--manifest` seçeneği ekleyin. Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.

`-o|--output <OUTPUT_DIRECTORY>`

Çıkış dizini için yolu belirtir. Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.
Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Uygulamayı belirli bir çalışma zamanı için yayımlar. Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#publish-self-contained)oluşturulurken kullanılır. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#publish-runtime-dependent)yayımlamaktır.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek sürüm sonekini tanımlar.

---

## <a name="examples"></a>Örnekler

Projeyi geçerli dizinde yayımlayın:

`dotnet publish`

Belirtilen proje dosyasını kullanarak uygulamayı yayımlayın:

`dotnet publish ~/projects/app1/app1.csproj`

`netcoreapp1.1` çerçevesini kullanarak projeyi geçerli dizinde yayımlayın:

`dotnet publish --framework netcoreapp1.1`

`netcoreapp1.1` çerçevesini ve `OS X 10.10` çalışma zamanını kullanarak geçerli uygulamayı yayımlayın (Bu RID 'yi proje dosyasında listemalısınız).

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

Geçerli uygulamayı yayımlayın ancak projeden projeye (P2P) başvurularını geri yüklemeyin, ancak geri yükleme işlemi sırasında yalnızca kök proje (.NET Core SDK 2,0 ve üzeri sürümler):

`dotnet publish --no-dependencies`

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef çerçeveler](../../standard/frameworks.md)
- [Çalışma zamanı tanımlayıcı (RID) kataloğu](../rid-catalog.md)
