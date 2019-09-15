---
title: DotNet Run komutu
description: DotNet Run komutu, uygulamanızı kaynak koddan çalıştırmak için uygun bir seçenek sağlar.
ms.date: 05/29/2018
ms.openlocfilehash: b21987ef9ee4dd7d8fdb93d0853b7faa93001688
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969757"
---
# <a name="dotnet-run"></a>dotnet run

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet run`-Açık derleme veya başlatma komutları olmadan kaynak kodu çalıştırır.

## <a name="synopsis"></a>Özeti

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```console
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```console
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```console
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a>Açıklama

Komut `dotnet run` , uygulamanızı kaynak koddan tek bir komutla çalıştırmak için uygun bir seçenek sunar. Komut satırından hızlı yinelemeli geliştirme için faydalıdır. Komut, kodu oluşturmak için [`dotnet build`](dotnet-build.md) komutuna bağımlıdır. Projenin önce geri yüklenmesi gerektiği gibi, derleme için tüm gereksinimler, için `dotnet run` de geçerlidir.

Çıktı dosyaları varsayılan konuma yazılır, `bin/<configuration>/<target>`yani. Örneğin, bir uygulamanız varsa ve `netcoreapp2.1` çalıştırırsanız `dotnet run`çıkış ' a yerleştirilir `bin/Debug/netcoreapp2.1`. Dosyalar gerektiği gibi üzerine yazılır. Geçici dosyalar `obj` dizine yerleştirilir.

Proje birden çok çerçeve belirtiyorsa, çerçeveyi belirtmek `dotnet run` için `-f|--framework <FRAMEWORK>` seçeneği kullanılmadığı müddetçe sonuçları bir hata halinde yürütüyordur.

`dotnet run` Komut, oluşturulan derlemeler değil, proje bağlamında kullanılır. Bunun yerine Framework 'e bağımlı bir uygulama DLL 'sini çalıştırmaya çalışıyorsanız, bir komut olmadan [DotNet](dotnet.md) kullanmanız gerekir. Örneğin, çalıştırmak `myapp.dll`için şunu kullanın:

```console
dotnet myapp.dll
```

`dotnet` Sürücü hakkında daha fazla bilgi için bkz. [.NET Core komut satırı araçları (CLI)](index.md) konusu.

Uygulamayı çalıştırmak için `dotnet run` komut, paylaşılan çalışma zamanının dışındaki uygulamanın tüm bağımlılıklarını NuGet önbelleğinden çözer. Önbelleğe alınmış bağımlılıkları kullandığından, üretim ortamında uygulamaları çalıştırmak için kullanılması `dotnet run` önerilmez. Bunun yerine, [`dotnet publish`](dotnet-publish.md) komutunu kullanarak [bir dağıtım oluşturun](../deploying/index.md) ve yayımlanan çıktıyı dağıtın.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`--`

Çalıştırılmakta olan uygulama `dotnet run` için bağımsız değişkenlerin bağımsız değişkenlerini sınırlandırın. Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır. Çerçeve proje dosyasında belirtilmelidir.

`--force`

Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--launch-profile <NAME>`

Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa). Başlatma profilleri, *launchsettings. JSON* dosyasında tanımlanır ve genellikle, `Development` `Staging`ve `Production`olarak adlandırılır. Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).

`--no-build`

Çalıştırmadan önce projeyi oluşturmaz. `--no-restore` Bayrak de örtülü olarak ayarlanır.

`--no-dependencies`

Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.

`--no-launch-profile`

Uygulamayı yapılandırmak için *Launchsettings. JSON* kullanmaya çalışmayın.

`--no-restore`

Komutu çalıştırılırken örtük geri yükleme yürütülmez.

`-p|--project <PATH>`

Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol). Belirtilmezse, varsayılan olarak geçerli dizini alır.

`--runtime <RUNTIME_IDENTIFIER>`

Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`--`

Çalıştırılmakta olan uygulama `dotnet run` için bağımsız değişkenlerin bağımsız değişkenlerini sınırlandırın. Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır. Çerçeve proje dosyasında belirtilmelidir.

`--force`

Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--launch-profile <NAME>`

Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa). Başlatma profilleri, *launchsettings. JSON* dosyasında tanımlanır ve genellikle, `Development` `Staging`ve `Production`olarak adlandırılır. Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).

`--no-build`

Çalıştırmadan önce projeyi oluşturmaz. `--no-restore` Bayrak de örtülü olarak ayarlanır.

`--no-dependencies`

Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.

`--no-launch-profile`

Uygulamayı yapılandırmak için *Launchsettings. JSON* kullanmaya çalışmayın.

`--no-restore`

Komutu çalıştırılırken örtük geri yükleme yürütülmez.

`-p|--project <PATH>`

Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol). Belirtilmezse, varsayılan olarak geçerli dizini alır.

`--runtime <RUNTIME_IDENTIFIER>`

Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

`--`

Çalıştırılmakta olan uygulama `dotnet run` için bağımsız değişkenlerin bağımsız değişkenlerini sınırlandırın. Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır. Çerçeve proje dosyasında belirtilmelidir.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`-p|--project <PATH/PROJECT.csproj>`

Proje dosyasının yolunu ve adını belirtir. (Nota bakın.) Belirtilmezse, varsayılan olarak geçerli dizini alır.

> [!NOTE]
> `-p|--project` Seçeneğiyle proje dosyasının yolunu ve adını kullanın. CLı 'deki bir gerileme, .NET Core SDK 1. x ile bir klasör yolu sağlamaya engel olur. Bu sorun hakkında daha fazla bilgi için bkz. [DotNet Run-p, bir proje başlatılamadı (DotNet/clı #5992)](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Örnekler

Projeyi geçerli dizinde Çalıştır:

`dotnet run`

Belirtilen projeyi Çalıştır:

`dotnet run --project ./projects/proj1/proj1.csproj`

Projeyi geçerli dizinde çalıştırın ( `--help` boş `--` seçenek kullanıldığından bu örnekteki bağımsız değişken uygulamaya geçirilir):

`dotnet run --configuration Release -- --help`

Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleme yalnızca minimum çıktıyı gösterir ve ardından projeyi (.NET Core SDK 2,0 ve sonraki sürümleri) çalıştırır:

`dotnet run --verbosity m`
