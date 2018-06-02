---
title: DotNet aracı güncelleştirme komutu - .NET Core CLI
description: Dotnet aracı güncelleştirme komut belirtilen .NET Core genel aracı makinenizde güncelleştirir.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 35a0bd0f85f0beed06d4250d8f195ce4fe4fcca4
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696695"
---
# <a name="dotnet-tool-update"></a>DotNet aracı güncelleştirmesi

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet tool update` -Güncelleştirmeleri belirtilen [.NET Core genel aracı](global-tools.md) makinenizde.

## <a name="synopsis"></a>Özet

```
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool update` Komutu, paketin en son kararlı sürümü için makinenizde .NET Core genel Araçları'nı güncelleştirmek bir yol sağlar. Komut kaldırır ve etkili bir şekilde güncelleştirme bir aracı yükler. Komutunu kullanmak için ya da bir araç kullanarak kullanıcı genelinde yükleme güncelleştirmek istediğiniz belirtmek zorunda `--global` seçeneği veya bir yol yeri belirtin aracı kullanılarak yüklenir `--tool-path` seçeneği.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

.NET Core genel güncelleştirmek için aracı içeren NuGet paketi adı/kimliği. Paket adı kullanarak bulabilirsiniz [dotnet araç listesi](dotnet-tool-list.md) komutu.

## <a name="options"></a>Seçenekler

`--add-source <SOURCE>`

Yükleme sırasında kullanmak için ek bir NuGet paketi kaynağı ekler.

`--configfile <FILE>`

NuGet yapılandırması (*nuget.config*) kullanmak üzere bir dosya.

`--framework <FRAMEWORK>`

Belirtir [hedef framework](../../standard/frameworks.md) için Aracı'nı güncelleştirmek için.

`-g|--global`

Güncelleştirme için kullanıcı genelinde aracı olduğunu belirtir. Birleştirilemez `--tool-path` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--tool-path` seçeneği.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--tool-path <PATH>`

Genel aracı yüklendiği konumunu belirtir. YOL, mutlak veya göreli olabilir. Birleştirilemez `--global` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--global` seçeneği.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

## <a name="examples"></a>Örnekler

Güncelleştirmeleri [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracı:

`dotnet tool update -g dotnetsay`

Güncelleştirmeleri [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel Aracı belirli bir Windows klasöründe bulunan:

`dotnet tool update dotnetsay --tool-path c:\global-tools`

Güncelleştirmeleri [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel Aracı belirli bir Linux/macOS klasöründe bulunan:

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Ayrıca bkz.

[.NET core genel araçları](global-tools.md)