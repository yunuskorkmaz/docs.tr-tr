---
title: DotNet Aracı kaldırma komutu
description: DotNet Aracı kaldırma komutu, belirtilen .NET Core aracını makinenizden kaldırır.
ms.date: 02/14/2020
ms.openlocfilehash: 82dad0206d9c3e2ef0f41c353f4a608f10e4f127
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543449"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet tool uninstall`-belirtilen [.NET Core aracını](global-tools.md) makinenizden kaldırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool uninstall` komutu, makinenizden .NET Core araçlarını kaldırmanız için bir yol sağlar. Komutunu kullanmak için aşağıdaki seçeneklerden birini belirtin:

* Varsayılan konumda yüklü olan küresel bir aracı kaldırmak için `--global` seçeneğini kullanın.
* Özel bir konuma yüklenmiş olan küresel bir aracı kaldırmak için `--tool-path` seçeneğini kullanın.
* Yerel bir aracı kaldırmak için `--global` ve `--tool-path` seçeneklerini atlayın.

**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PACKAGE_NAME`**

  Kaldırılacak .NET Core aracını içeren NuGet paketinin adı/KIMLIĞI. [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak paket adını bulabilirsiniz.

## <a name="options"></a>Seçenekler

- **`-g|--global`**

  Kaldırılacak aracın Kullanıcı genelindeki bir yüklemeden olduğunu belirtir. `--tool-path` seçeneği ile birleştirilemez. `--global` ve `--tool-path` her ikisi de kullanılmazsa, kaldırılacak aracın yerel bir araç olduğunu belirtir. 

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--tool-path <PATH>`**

  Aracının kaldırılacağı konumu belirtir. YOL mutlak veya göreli olabilir. `--global` seçeneği ile birleştirilemez. `--global` ve `--tool-path` her ikisi de kullanılmazsa, kaldırılacak aracın yerel bir araç olduğunu belirtir. 

## <a name="examples"></a>Örnekler

- **`dotnet tool uninstall -g dotnetsay`**

  [Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracını kaldırır.

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  [Dotnetsöyleme](https://www.nuget.org/packages/dotnetsay/) genel aracını belirli bir Windows dizininden kaldırır.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  Belirli bir Linux/macOS dizininden [dotnetsöyleyin](https://www.nuget.org/packages/dotnetsay/) genel aracını kaldırır.

- **`dotnet tool uninstall dotnetsay`**

  Geçerli dizinden [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) yerel aracını kaldırır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core araçları](global-tools.md)
