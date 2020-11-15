---
title: DotNet Aracı kaldırma komutu
description: DotNet Aracı kaldırma komutu, belirtilen .NET aracını makinenizden kaldırır.
ms.date: 02/14/2020
ms.openlocfilehash: 34dffde8f9c930327c6b42d1d89bb4f511959fb2
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634096"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet tool uninstall` -Belirtilen [.NET aracını](global-tools.md) makinenizden kaldırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a>Açıklama

`dotnet tool uninstall`Komut, makinenizden .net araçlarını kaldırmanız için bir yol sağlar. Komutunu kullanmak için aşağıdaki seçeneklerden birini belirtin:

* Varsayılan konumda yüklü olan küresel bir aracı kaldırmak için `--global` seçeneğini kullanın.
* Özel bir konuma yüklenmiş olan küresel bir aracı kaldırmak için `--tool-path` seçeneğini kullanın.
* Yerel bir aracı kaldırmak için `--global` ve `--tool-path` seçeneklerini atlayın.

**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**

## <a name="arguments"></a>Arguments

- **`PACKAGE_NAME`**

  Kaldırılacak .NET aracını içeren NuGet paketinin adı/KIMLIĞI. [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak paket adını bulabilirsiniz.

## <a name="options"></a>Seçenekler

- **`-g|--global`**

  Kaldırılacak aracın Kullanıcı genelindeki bir yüklemeden olduğunu belirtir. `--tool-path`Seçeneğiyle birleştirilemez. Her ikisini de atlama `--global` ve `--tool-path` kaldırılacak aracın yerel bir araç olduğunu belirtir.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--tool-path <PATH>`**

  Aracının kaldırılacağı konumu belirtir. YOL mutlak veya göreli olabilir. `--global`Seçeneğiyle birleştirilemez. Her ikisini de atlama `--global` ve `--tool-path` kaldırılacak aracın yerel bir araç olduğunu belirtir.

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

- [.NET araçları](global-tools.md)
- [Öğretici: .NET CLı kullanarak .NET genel aracını yükleyip kullanma](global-tools-how-to-use.md)
- [Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma](local-tools-how-to-use.md)
