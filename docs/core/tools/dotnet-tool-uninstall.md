---
title: DotNet Aracı kaldırma komutu - .NET Core CLI
description: Dotnet Aracı kaldırma komutu belirtilen .NET Core genel aracı makinenizden kaldırır.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5cf80d1756dbf4e88bb52a8028d186d44978f440
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696948"
---
# <a name="dotnet-tool-uninstall"></a>DotNet Aracı kaldırma

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet tool uninstall` -Kaldırır belirtilen [.NET Core genel aracı](global-tools.md) makinenizden.

## <a name="synopsis"></a>Özet

```
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool uninstall` Komutu, .NET Core genel araçları, makineden kaldırmak bir yol sağlar. Komutunu kullanmak için ya da kullanıcı genelinde aracını kullanarak kaldırmak istediğinizi belirtmeniz gerekir `--global` seçeneği veya bir yol yeri belirtin aracı kullanılarak yüklenen `--tool-path` seçeneği.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

.NET Core genel kaldırmak için Aracı'nı içeren NuGet paketi adı/kimliği. Paket adı kullanarak bulabilirsiniz [dotnet araç listesi](dotnet-tool-list.md) komutu.

## <a name="options"></a>Seçenekler

`-g|--global`

Kaldırılacak Aracı kullanıcı genelinde yüklemesinden olduğunu belirtir. Birleştirilemez `--tool-path` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--tool-path` seçeneği.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--tool-path <PATH>`

Konumun genel Aracı'nı kaldırmak konumu belirtir. YOL, mutlak veya göreli olabilir. Birleştirilemez `--global` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--global` seçeneği.

## <a name="examples"></a>Örnekler

Kaldırır [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracı:

`dotnet tool uninstall -g dotnetsay`

Kaldırır [dotnetsay](https://www.nuget.org/packages/dotnetsay/) belirli bir Windows klasörü genel aracından:

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

Kaldırır [dotnetsay](https://www.nuget.org/packages/dotnetsay/) belirli bir Linux/macOS klasörden genel aracı:

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Ayrıca bkz.

[.NET core genel araçları](global-tools.md)