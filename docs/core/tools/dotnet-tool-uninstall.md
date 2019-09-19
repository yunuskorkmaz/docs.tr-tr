---
title: DotNet Aracı kaldırma komutu
description: DotNet Aracı kaldırma komutu, belirtilen .NET Core küresel aracını makinenizden kaldırır.
ms.date: 05/29/2018
ms.openlocfilehash: 033753f44464e78b826e908e0b6cdf276da8a179
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117545"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet tool uninstall`-Belirtilen [.NET Core küresel aracını](global-tools.md) makinenizden kaldırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Açıklama

Komut `dotnet tool uninstall` , makinenizden .NET Core küresel araçlarını kaldırmanız için bir yol sağlar. Komutunu kullanmak için, `--global` seçeneğini kullanarak bir Kullanıcı genelindeki aracı kaldırmak istediğinizi belirtmeniz veya `--tool-path` seçeneği kullanılarak aracın yüklendiği konuma bir yol belirtmeniz gerekir.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Kaldırılacak .NET Core küresel aracını içeren NuGet paketinin adı/KIMLIĞI. [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak paket adını bulabilirsiniz.

## <a name="options"></a>Seçenekler

`-g|--global`

Kaldırılacak aracın Kullanıcı genelindeki bir yüklemeden olduğunu belirtir. `--tool-path` Seçeneğiyle birleştirilemez. Bu seçeneği belirtmezseniz, `--tool-path` seçeneğini belirtmeniz gerekir.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--tool-path <PATH>`

Genel aracının kaldırılacağı konumu belirtir. YOL mutlak veya göreli olabilir. `--global` Seçeneğiyle birleştirilemez. Bu seçeneği belirtmezseniz, `--global` seçeneğini belirtmeniz gerekir.

## <a name="examples"></a>Örnekler

[Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel aracını kaldırır:

`dotnet tool uninstall -g dotnetsay`

[Dotnetsöyleme](https://www.nuget.org/packages/dotnetsay/) genel aracını belirli bir Windows klasöründen kaldırır:

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

[Dotnetsöyleyin](https://www.nuget.org/packages/dotnetsay/) küresel aracını belirli bir Linux/MacOS klasöründen kaldırır:

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core küresel araçları](global-tools.md)
