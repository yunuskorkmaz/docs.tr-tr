---
title: "dotnet .NET Core CLI komutu çalıştırın"
description: "Komutu çalıştırın dotnet uygulamanızın kaynak kodunu çalıştırmak için uygun bir seçenek sağlar."
author: mairaw
ms.author: mairaw
ms.date: 09/24/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 7670934199d7d4b8a7c5e598142366ef1eb3ef1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-run"></a>dotnet çalıştırın

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet run`-Kaynak kodu herhangi bir açık derleme veya başlatma komutları olmadan çalıştırır.

## <a name="synopsis"></a>Özet

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a>Açıklama

`dotnet run` Komutu bir komut ile kaynak koddan uygulamanızı çalıştırmak için uygun bir seçenek sağlar. Komut satırından hızlı yinelemeli geliştirme için kullanışlıdır. Komut bağlıdır [ `dotnet build` ](dotnet-build.md) kodu oluşturmak için komutu. Derleme için tüm gereksinimleri, gibi proje geri yüklenmelidir ilk olarak, geçerli `dotnet run` de. 

Çıkış dosyaları olan varsayılan konumuna yazılır `bin/<configuration>/<target>`. Örneğin, varsa bir `netcoreapp1.0` uygulama ve Çalıştır `dotnet run`, çıktı yerleştirilir `bin/Debug/netcoreapp1.0`. Gerektiğinde dosyalarının üzerine yazılır. Geçici dosyalar yerleştirilir `obj` dizin. 

Projenin birden çok çerçeveyi belirtiyorsa, yürütme `dotnet run` sürece hatayla sonuçlanır `-f|--framework <FRAMEWORK>` seçeneği framework belirtmek için kullanılır.

`dotnet run` Komutu derlemeler oluşturulan değil projeler bağlamında kullanılır. Bunun yerine bir framework bağımlı uygulamayı DLL çalıştırmak çalışıyorsanız, kullanmalısınız [dotnet](dotnet.md) olmadan bir komutu. Örneğin, çalıştırmak için `myapp.dll`, kullanın:

```
dotnet myapp.dll
```

Daha fazla bilgi için `dotnet` sürücüsü bkz [.NET Core komut satırı araçları (CLI)](index.md) konu.

Uygulamayı çalıştırmak için `dotnet run` komutu NuGet önbelleğinden paylaşılan çalışma zamanı dışında Uygulama bağımlılıklarını giderir. Önbelleğe alınan bağımlılıkları kullandığından, onu kullanmak önerilmez `dotnet run` üretimde uygulamaları çalıştırmak için. Bunun yerine, [bir dağıtım oluşturmak](../deploying/index.md) kullanarak [ `dotnet publish` ](dotnet-publish.md) komut ve yayımlanan çıkış dağıtın.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`--`

Bağımsız değişkenleri sınırlandırır `dotnet run` gelen çalıştırılan uygulama için bağımsız değişkenler. Bu bir sonra tüm bağımsız değişkenler Çalıştırma uygulaması geçirilir.

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Derlemeler ve belirtilen kullanarak uygulamayı çalıştıran [framework](../../standard/frameworks.md). Proje dosyasında framework belirtilmesi gerekir.

`--force`

Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar. Bu silme ile eşdeğerdir *project.assets.json*.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--launch-profile <NAME>`

Başlatma adını profil (varsa) uygulama başlatılırken kullanılacak. Başlatma profilleri tanımlanmış *launchSettings.json* dosya ve genellikle adlı `Development`, `Staging` ve `Production`. Daha fazla bilgi için bkz: [birden çok ortamlarıyla çalışma](/aspnet/core/fundamentals/environments).

`--no-build`

Çalıştırmadan önce projeyi derlemek değil.

`--no-dependencies`

Proje Proje (P2P) başvuruları içeren bir proje geri yüklerken, kök proje ve başvuru geri yükler.

`--no-launch-profile`

Kullanma girişimi değil *launchSettings.json* uygulamayı yapılandırmak için.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken gerçekleştirmez.

`-p|--project <PATH>`

(Klasör adı veya tam yolu) çalıştırmak için proje dosyasının yolunu belirtir. Belirtilmezse, geçerli dizine varsayar.

`--runtime <RUNTIME_IDENTIFIER>`

Paketler için geri yüklemek için hedef çalışma zamanı belirtir. Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--`

Bağımsız değişkenleri sınırlandırır `dotnet run` gelen çalıştırılan uygulama için bağımsız değişkenler. Bu bir sonra tüm bağımsız değişkenler Çalıştırma uygulaması geçirilir.

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Derlemeler ve belirtilen kullanarak uygulamayı çalıştıran [framework](../../standard/frameworks.md). Proje dosyasında framework belirtilmesi gerekir.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-p|--project <PATH/PROJECT.csproj>`

Proje dosyasının adını ve yolunu belirtir. (NOTA bakın.) Belirtilmezse, geçerli dizine varsayar.

> [!NOTE]
> Proje dosyası ile adını ve yolunu kullanın `-p|--project` seçeneği. .NET Core ile bir klasör yolu sağlayan CLI'teki bir gerileme engeller 1.x SDK. Bu sorun hakkında daha fazla bilgi için bkz: [-p, çalıştırmak dotnet değil (dotnet/CLI #5992) proje Başlat](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Örnekler

Proje geçerli dizinde çalıştırın:

`dotnet run`

Belirtilen proje çalıştırın:

`dotnet run --project /projects/proj1/proj1.csproj`

Geçerli dizinde projeyi çalıştırın ( `--help` bağımsız değişkeni Bu örnekte geçirilir uygulamaya beri `--` bağımsız değişkeninin değeri kullanılır):

`dotnet run --configuration Release -- --help`
