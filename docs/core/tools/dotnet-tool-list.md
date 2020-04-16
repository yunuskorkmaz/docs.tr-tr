---
title: dotnet araç listesi komutu
description: Dotnet araç listesi komutu, makinenize yüklenen .NET Core araçlarını listeler.
ms.date: 02/14/2020
ms.openlocfilehash: 28f9155407d1238f8b0960b69b34ea329ca0e8e6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463355"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet tool list`- Şu anda makinenizde yüklü olan belirtilen türdeki tüm [.NET Core araçlarını](global-tools.md) listeler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet tool list` makinenizde yüklü olan tüm .NET Core global, araç yolu veya yerel Araçları listele etmeniz için bir yol sağlar. Komut, paket adını, yüklenen sürümü ve araç komutunu listeler.  Komutu kullanmak için aşağıdakilerden birini belirtin:

* Varsayılan konuma yüklenen genel bir araç. `--global` Seçeneği kullanma
* Özel bir konuma yüklenen genel bir araç. `--tool-path` Seçeneği kullanın.
* Yerel bir araç. Ve `--tool-path` seçenekleri `--global` atla.

**Yerel araçlar .NET Core SDK 3.0 ile başlayarak kullanılabilir.**

## <a name="options"></a>Seçenekler

- **`-g|--global`**

  Kullanıcı çapında genel araçları listeler. `--tool-path` Seçenekle birleştirilemeyiz. Her ikisini `--global` de `--tool-path` atlayarak yerel araçları listeler.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--tool-path <PATH>`**

  Genel araçları bulabileceğiniz özel bir konum belirtir. PATH mutlak veya göreceli olabilir. `--global` Seçenekle birleştirilemeyiz. Her ikisini `--global` de `--tool-path` atlayarak yerel araçları listeler.

## <a name="examples"></a>Örnekler

- **`dotnet tool list -g`**

  Makinenizde kullanıcı çapında yüklenen tüm genel araçları listeler (geçerli kullanıcı profili).

- **`dotnet tool list --tool-path c:\global-tools`**

  Belirli bir Windows dizinindeki genel araçları listeler.

- **`dotnet tool list --tool-path ~/bin`**

  Belirli bir Linux/macOS dizinindeki genel araçları listeler.

- **`dotnet tool list`**

  Geçerli dizinde bulunan tüm yerel araçları listeler.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Çekirdek araçları](global-tools.md)
- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın](global-tools-how-to-use.md)
- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın](local-tools-how-to-use.md)
