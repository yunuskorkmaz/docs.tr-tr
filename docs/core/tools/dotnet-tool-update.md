---
title: DotNet tool güncelleştirme komutu
description: Dotnet aracı güncelleştirme komut belirtilen .NET Core genel aracı makinenizde güncelleştirir.
ms.date: 05/29/2018
ms.openlocfilehash: 2716f7f88ffe364bebacf970d7152f5509edc888
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169748"
---
# <a name="dotnet-tool-update"></a>DotNet aracı güncelleştirme

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet tool update` -Güncelleştirmeleri belirtilen [.NET Core genel aracı](global-tools.md) makinenizde.

## <a name="synopsis"></a>Özeti

```console
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool update` Komutu, paketin en son kararlı sürüme makinenizde .NET Core genel Araçları'nı güncelleştirmek bir yol sağlar. Komut kaldırır ve etkili bir şekilde güncelleştirirken bir aracı yükler. Komutunu kullanmak için ya da bir araç kullanarak kullanıcı genelinde yükleme güncelleştirmek istediğiniz belirtmeniz gerekir `--global` nerede yolunu belirtin veya seçeneği kullanılarak yüklenen aracı `--tool-path` seçeneği.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

.NET Core genel güncelleştirme için Aracı'nı içeren NuGet paket adı/kimliği. Paket adını kullanarak bulabilirsiniz [dotnet araç listesi](dotnet-tool-list.md) komutu.

## <a name="options"></a>Seçenekler

`--add-source <SOURCE>`

Yükleme sırasında kullanmak üzere ek bir NuGet paket kaynağı ekler.

`--configfile <FILE>`

NuGet yapılandırma (*nuget.config*) dosyasını kullanın.

`--framework <FRAMEWORK>`

Belirtir [hedef Framework'ü](../../standard/frameworks.md) araç için güncelleştirilecek.

`-g|--global`

Güncelleştirme için kullanıcı genelinde aracı olduğunu belirtir. İle birleştirilemez `--tool-path` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--tool-path` seçeneği.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--tool-path <PATH>`

Genel aracı yüklendiği konum belirtir. YOL mutlak veya göreli olabilir. İle birleştirilemez `--global` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--global` seçeneği.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

## <a name="examples"></a>Örnekler

Güncelleştirmeleri [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracı:

`dotnet tool update -g dotnetsay`

Güncelleştirmeleri [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracı, belirli bir Windows klasöründe bulunur:

`dotnet tool update dotnetsay --tool-path c:\global-tools`

Güncelleştirmeleri [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracı, belirli bir Linux/macOS klasöründe bulunur:

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Ayrıca bkz.

* [.NET core Araçları Genel](global-tools.md)