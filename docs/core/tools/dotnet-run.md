---
title: DotNet Run komutu
description: DotNet Run komutu, uygulamanızı kaynak koddan çalıştırmak için uygun bir seçenek sağlar.
ms.date: 10/31/2019
ms.openlocfilehash: 87e9a57e874116533951a9c5eb676be76be2c98d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454783"
---
# <a name="dotnet-run"></a>dotnet run

**Bu makale şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet run`-herhangi bir açık derleme veya başlatma komutu olmadan kaynak kodu çalıştırır.

## <a name="synopsis"></a>Özeti

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a>Açıklama

`dotnet run` komutu, uygulamanızı kaynak koddan tek bir komutla çalıştırmak için uygun bir seçenek sağlar. Komut satırından hızlı yinelemeli geliştirme için faydalıdır. Komut, kodu derlemek için [`dotnet build`](dotnet-build.md) komutuna bağımlıdır. Projenin önce geri yüklenmesi gerektiği gibi, derleme için tüm gereksinimler, `dotnet run` için de geçerlidir.

Çıktı dosyaları varsayılan konuma yazılır, bu `bin/<configuration>/<target>`. Örneğin, bir `netcoreapp2.1` uygulamanız varsa ve `dotnet run`çalıştırırsanız, çıktı `bin/Debug/netcoreapp2.1`yerleştirilir. Dosyalar gerektiği gibi üzerine yazılır. Geçici dosyalar `obj` dizinine yerleştirilir.

Proje birden çok çerçeve belirtiyorsa, Framework 'ü belirtmek için `-f|--framework <FRAMEWORK>` seçeneği kullanılmadığı müddetçe `dotnet run` yürütülerek hata oluşur.

`dotnet run` komutu, oluşturulan derlemeler değil, proje bağlamında kullanılır. Bunun yerine Framework 'e bağımlı bir uygulama DLL 'sini çalıştırmaya çalışıyorsanız, bir komut olmadan [DotNet](dotnet.md) kullanmanız gerekir. Örneğin, `myapp.dll`çalıştırmak için şunu kullanın:

```dotnetcli
dotnet myapp.dll
```

`dotnet` sürücüsü hakkında daha fazla bilgi için bkz. [.NET Core komut satırı araçları (CLI)](index.md) konusu.

Uygulamayı çalıştırmak için `dotnet run` komutu, paylaşılan çalışma zamanının dışındaki uygulamanın tüm bağımlılıklarını NuGet önbelleğinden çözer. Önbelleğe alınmış bağımlılıkları kullandığından, üretimde uygulamaları çalıştırmak için `dotnet run` kullanılması önerilmez. Bunun yerine, [`dotnet publish`](dotnet-publish.md) komutunu kullanarak [bir dağıtım oluşturun](../deploying/index.md) ve yayımlanan çıktıyı dağıtın.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Seçenekler

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

`--`

Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır. Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Çoğu projenin varsayılan değeri `Debug`.

`-f|--framework <FRAMEWORK>`

Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır. Çerçeve proje dosyasında belirtilmelidir.

`--force`

Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--interactive`

Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik).

`--launch-profile <NAME>`

Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa). Başlatma profilleri, *Launchsettings. JSON* dosyasında tanımlanır ve genellikle `Development`, `Staging`ve `Production`olarak adlandırılır. Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).

`--no-build`

Çalıştırmadan önce projeyi oluşturmaz. Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.

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

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`--`

Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır. Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Çoğu projenin varsayılan değeri `Debug`.

`-f|--framework <FRAMEWORK>`

Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır. Çerçeve proje dosyasında belirtilmelidir.

`--force`

Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--launch-profile <NAME>`

Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa). Başlatma profilleri, *Launchsettings. JSON* dosyasında tanımlanır ve genellikle `Development`, `Staging`ve `Production`olarak adlandırılır. Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).

`--no-build`

Çalıştırmadan önce projeyi oluşturmaz. Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.

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

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`--`

Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır. Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Çoğu proje değeri için varsayılan değer `Debug`.

`-f|--framework <FRAMEWORK>`

Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır. Çerçeve proje dosyasında belirtilmelidir.

`--force`

Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--launch-profile <NAME>`

Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa). Başlatma profilleri, *Launchsettings. JSON* dosyasında tanımlanır ve genellikle `Development`, `Staging`ve `Production`olarak adlandırılır. Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).

`--no-build`

Çalıştırmadan önce projeyi oluşturmaz. Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.

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

Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır. Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Çoğu projenin varsayılan değeri `Debug`.

`-f|--framework <FRAMEWORK>`

Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır. Çerçeve proje dosyasında belirtilmelidir.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`-p|--project <PATH/PROJECT.csproj>`

Proje dosyasının yolunu ve adını belirtir. (Nota bakın.) Belirtilmezse, varsayılan olarak geçerli dizini alır.

> [!NOTE]
> `-p|--project` seçeneğiyle proje dosyasının yolunu ve adını kullanın. CLı 'deki bir gerileme, .NET Core SDK 1. x ile bir klasör yolu sağlamaya engel olur. Bu sorun hakkında daha fazla bilgi için bkz. [DotNet Run-p, bir proje başlatılamadı (DotNet/clı #5992)](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Örnekler

Projeyi geçerli dizinde Çalıştır:

`dotnet run`

Belirtilen projeyi Çalıştır:

`dotnet run --project ./projects/proj1/proj1.csproj`

Projeyi geçerli dizinde çalıştırın (boş `--` seçeneği kullanıldığından bu örnekteki `--help` bağımsız değişkeni uygulamaya geçirilir):

`dotnet run --configuration Release -- --help`

Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleme yalnızca minimum çıktıyı gösterir ve ardından projeyi (.NET Core SDK 2,0 ve sonraki sürümleri) çalıştırır:

`dotnet run --verbosity m`
