---
title: DotNet araç listesi komutu
description: DotNet araç listesi komutu, makinenizde yüklü olan .NET Core araçlarını listeler.
ms.date: 02/14/2020
ms.openlocfilehash: bb74cfeaf441cf8a1a030d97d16655f85d8267d1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543462"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet tool list`-makinenizde yüklü olan belirtilen türdeki tüm [.NET Core araçları](global-tools.md) listelenir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool list` komutu, makinenizde yüklü olan tüm .NET Core genel, araç yolu veya yerel araçlarını listeetmeniz için bir yol sağlar. Komut, paket adını, yüklü sürümü ve araç komutunu listeler.  Komutunu kullanmak için aşağıdakilerden birini belirtin:

* Varsayılan konumda yüklü olan küresel bir araç. `--global` seçeneğini kullanın
* Özel bir konumda yüklü olan küresel bir araç. `--tool-path` seçeneğini kullanın.
* Yerel bir araç. `--global` ve `--tool-path` seçeneklerini atlayın.

**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**

## <a name="options"></a>Seçenekler

- **`-g|--global`**

  Kullanıcı genelindeki genel araçları listeler. `--tool-path` seçeneği ile birleştirilemez. Hem `--global` hem de `--tool-path`, yerel araçları listeler. 

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--tool-path <PATH>`**

  Genel araçların bulunacağı bir özel konum belirtir. YOL mutlak veya göreli olabilir. `--global` seçeneği ile birleştirilemez. Hem `--global` hem de `--tool-path`, yerel araçları listeler. 

## <a name="examples"></a>Örnekler

- **`dotnet tool list -g`**

  Makinenizde Kullanıcı genelinde yüklenen tüm genel araçları listeler (geçerli kullanıcı profili).

- **`dotnet tool list --tool-path c:\global-tools`**

  Belirli bir Windows dizininden küresel araçları listeler.

- **`dotnet tool list --tool-path ~/bin`**

  Belirli bir Linux/macOS dizininden küresel araçları listeler.

- **`dotnet tool list`**

  Geçerli dizinde bulunan tüm yerel araçları listeler.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core araçları](global-tools.md)
