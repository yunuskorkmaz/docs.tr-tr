---
title: dotnet .NET Core CLI komutu çalıştırın
description: Dotnet komutu çalıştırın, kaynak koddan uygulamanızı çalıştırmak için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f560e6f795f00488818647a4b5c711dcf9d59dcd
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367750"
---
# <a name="dotnet-run"></a>dotnet çalıştırın

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet run` -Çalıştırmalar kaynak kodu olmadan herhangi bir özel derleme veya başlatma komutu.

## <a name="synopsis"></a>Özeti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```
---

## <a name="description"></a>Açıklama

`dotnet run` Komutu bir komut ile kaynak koddan uygulamanızı çalıştırmak için uygun bir seçenek sağlar. Komut satırından hızlı yinelemeli geliştirme için kullanışlıdır. Komut bağımlı [ `dotnet build` ](dotnet-build.md) Kodu derlemek için komutu. Derleme için tüm gereksinimleri, gibi proje gerekir geri ilk olarak, geçerli `dotnet run` de.

Çıktı dosyaları olan varsayılan konumuna yazılır `bin/<configuration>/<target>`. Örneğin, varsa bir `netcoreapp2.1` ve uygulama çalıştırma `dotnet run`, çıkış yerleştirilir `bin/Debug/netcoreapp2.1`. Dosyaları gerektiği şekilde üzerine yazılır. Geçici dosyalar yerleştirildiğinde `obj` dizin.

Birden çok çerçeve proje belirtiyorsa, yürütme `dotnet run` sürece hatayla sonuçlanır `-f|--framework <FRAMEWORK>` seçeneği framework belirtmek için kullanılır.

`dotnet run` Komut, projeler, derlenen bütünleştirilmiş kodlarda değil bağlamında kullanılır. Framework bağımlı uygulama DLL yerine çalıştırılacak çalışıyorsanız, kullanmalısınız [dotnet](dotnet.md) olmadan bir komutu. Örneğin, çalıştırılacak `myapp.dll`, kullanın:

```console
dotnet myapp.dll
```

Daha fazla bilgi için `dotnet` sürücüsü bkz [.NET Core komut satırı araçları (CLI)](index.md) konu.

Uygulamayı çalıştırmak için `dotnet run` komut paylaşılan çalışma zamanını şuradan NuGet önbelleğini dışında olan uygulama bağımlılıklarını çözümler. Önbelleğe alınan bağımlılıkları kullandığından, onu kullanmak için önermedi `dotnet run` üretim uygulamaları çalıştırmak için. Bunun yerine, [bir dağıtım yaratmanız](../deploying/index.md) kullanarak [ `dotnet publish` ](dotnet-publish.md) komut ve yayımlanan çıkış dağıtın.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--`

Bağımsız değişkenleri sınırlandırır `dotnet run` gelen çalıştırılan uygulama için bağımsız değişkenler. Uygulamayı çalıştırmak için bu sınırlandırıcıdan sonra gelen tüm bağımsız değişkenler geçirilir.

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Oluşturur ve belirtilen kullanarak uygulama çalışır [framework](../../standard/frameworks.md). Çerçeve proje dosyasında belirtilmesi gerekir.

`--force`

Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar. Bu bayrak belirten aynıdır silme *project.assets.json* dosya.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--launch-profile <NAME>`

Başlatma adı profilini (varsa) uygulamayı başlatırken kullanılacak. Başlatma profili tanımlanmış *launchSettings.json* dosya ve genellikle çağrıldığında `Development`, `Staging`, ve `Production`. Daha fazla bilgi için [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).

`--no-build`

Çalıştırmadan önce projeyi derle değil. Ayrıca örtülü ayarlar `--no-restore` bayrağı.

`--no-dependencies`

Projeden projeye (P2P) başvurular içeren bir proje geri yüklerken, kök proje ve başvuruları geri yükler.

`--no-launch-profile`

Kullanılacak çalışmaz *launchSettings.json* uygulamayı yapılandırmak için.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken yürütülmez.

`-p|--project <PATH>`

(Klasör adı veya tam yolu) çalıştırmak için proje dosyasının yolunu belirtir. Belirtilmezse, geçerli dizin için varsayılan olarak.

`--runtime <RUNTIME_IDENTIFIER>`

Paketleri geri yüklemek için hedef çalışma zamanı belirtir. Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--`

Bağımsız değişkenleri sınırlandırır `dotnet run` gelen çalıştırılan uygulama için bağımsız değişkenler. Uygulamayı çalıştırmak için bu sınırlandırıcıdan sonra gelen tüm bağımsız değişkenler geçirilir.

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Oluşturur ve belirtilen kullanarak uygulama çalışır [framework](../../standard/frameworks.md). Çerçeve proje dosyasında belirtilmesi gerekir.

`--force`

Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar. Bu bayrak belirten aynıdır silme *project.assets.json* dosya.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--launch-profile <NAME>`

Başlatma adı profilini (varsa) uygulamayı başlatırken kullanılacak. Başlatma profili tanımlanmış *launchSettings.json* dosya ve genellikle çağrıldığında `Development`, `Staging`, ve `Production`. Daha fazla bilgi için [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).

`--no-build`

Çalıştırmadan önce projeyi derle değil. Ayrıca örtülü ayarlar `--no-restore` bayrağı.

`--no-dependencies`

Projeden projeye (P2P) başvurular içeren bir proje geri yüklerken, kök proje ve başvuruları geri yükler.

`--no-launch-profile`

Kullanılacak çalışmaz *launchSettings.json* uygulamayı yapılandırmak için.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken yürütülmez.

`-p|--project <PATH>`

(Klasör adı veya tam yolu) çalıştırmak için proje dosyasının yolunu belirtir. Belirtilmezse, geçerli dizin için varsayılan olarak.

`--runtime <RUNTIME_IDENTIFIER>`

Paketleri geri yüklemek için hedef çalışma zamanı belirtir. Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--`

Bağımsız değişkenleri sınırlandırır `dotnet run` gelen çalıştırılan uygulama için bağımsız değişkenler. Uygulamayı çalıştırmak için bu sınırlandırıcıdan sonra gelen tüm bağımsız değişkenler geçirilir.

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Oluşturur ve belirtilen kullanarak uygulama çalışır [framework](../../standard/frameworks.md). Çerçeve proje dosyasında belirtilmesi gerekir.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-p|--project <PATH/PROJECT.csproj>`

Proje dosyasının adını ve yolunu belirtir. (NOTA bakın.) Belirtilmezse, geçerli dizin için varsayılan olarak.

> [!NOTE]
> İle proje dosyasının adını ve yolunu kullanın `-p|--project` seçeneği. CLI'teki bir gerileme, .NET Core SDK'sı ile bir klasör yolu sağlama engeller 1.x. Bu sorun hakkında daha fazla bilgi için bkz. [dotnet -p çalıştırın (#5992 dotnet/CLI) bir proje başlayamaz](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Örnekler

Projenin geçerli dizinde çalıştırın:

`dotnet run`

Belirtilen projeyi çalıştır:

`dotnet run --project ./projects/proj1/proj1.csproj`

Geçerli dizinde projeyi çalıştırın ( `--help` Bu örnekte bağımsız değişken boş beri uygulamaya geçirilir `--` seçeneği kullanıldığında):

`dotnet run --configuration Release -- --help`

Bağımlılıklar ve geçerli dizinde proje için araçları çıkışını alır ve ardından projeyi çalıştırın, en az gösteren yalnızca geri yükleme: (.NET Core SDK 2.0 ve sonraki sürümler):

`dotnet run --verbosity m`