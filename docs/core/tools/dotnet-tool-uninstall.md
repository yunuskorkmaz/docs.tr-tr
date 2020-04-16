---
title: dotnet aracı kaldırma komutu
description: Dotnet aracı kaldırma komutu, belirtilen .NET Core aracını makinenizden kaldırz.
ms.date: 02/14/2020
ms.openlocfilehash: 0416f91019a49e17f1be14a1d928ad1fafaa736c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463306"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet tool uninstall`- Belirtilen [.NET Core aracını](global-tools.md) makinenizden kaldırın.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet tool uninstall` makinenizden .NET Core araçlarını kaldırmanız için bir yol sağlar. Komutu kullanmak için aşağıdaki seçeneklerden birini belirtirsiniz:

* Varsayılan konumda yüklü olan genel bir aracı kaldırmak için `--global` seçeneği kullanın.
* Özel bir konumda yüklenen genel bir aracı kaldırmak için `--tool-path` seçeneği kullanın.
* Yerel bir aracı kaldırmak için, `--global` seçenekleri `--tool-path` ve seçenekleri atleyin.

**Yerel araçlar .NET Core SDK 3.0 ile başlayarak kullanılabilir.**

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PACKAGE_NAME`**

  Kaldırılmak için .NET Core aracını içeren NuGet paketinin adı/kimliği. Paket adını [dotnet araç listesi](dotnet-tool-list.md) komutunu kullanarak bulabilirsiniz.

## <a name="options"></a>Seçenekler

- **`-g|--global`**

  Kaldırılacak aracın kullanıcı çapındaki bir yüklemeden olduğunu belirtir. `--tool-path` Seçenekle birleştirilemeyiz. Her ikisini `--global` de `--tool-path` atlayan ve kaldırılacak aracın yerel bir araç olduğunu belirtir.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--tool-path <PATH>`**

  Aracın kaldırılabildiği yeri belirtir. PATH mutlak veya göreceli olabilir. `--global` Seçenekle birleştirilemeyiz. Her ikisini `--global` de `--tool-path` atlayan ve kaldırılacak aracın yerel bir araç olduğunu belirtir.

## <a name="examples"></a>Örnekler

- **`dotnet tool uninstall -g dotnetsay`**

  [Dotnetsay](https://www.nuget.org/packages/dotnetsay/) global aracını yükler.

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  Belirli bir Windows dizininden [noktanetsay](https://www.nuget.org/packages/dotnetsay/) global aracını kaldır.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  Belirli bir Linux/macOS dizininden [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global aracını kaldırır.

- **`dotnet tool uninstall dotnetsay`**

  Geçerli dizinden [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yerel aracını kaldır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Çekirdek araçları](global-tools.md)
- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın](global-tools-how-to-use.md)
- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın](local-tools-how-to-use.md)
