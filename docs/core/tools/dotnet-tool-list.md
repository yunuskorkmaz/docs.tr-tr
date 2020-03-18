---
title: dotnet araç listesi komutu
description: Dotnet araç listesi komutu, makinenize yüklenen .NET Core araçlarını listeler.
ms.date: 02/14/2020
ms.openlocfilehash: def3c345a775e5a65ec3d37718d207c80ca7ceee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847878"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet tool list`- Şu anda makinenizde yüklü olan belirtilen türdeki tüm [.NET Core araçlarını](global-tools.md) listeler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet tool list <-g|--global>

dotnet tool list <--tool-path>

dotnet tool list

dotnet tool list <-h|--help>
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
