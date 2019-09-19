---
title: DotNet araç listesi komutu
description: DotNet araç listesi komutu, makinenizden belirtilen .NET Core küresel aracını listeler.
ms.date: 05/29/2018
ms.openlocfilehash: 6d35b1dce0c6d57edb0c6dd5f9711f093bc804aa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117556"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet tool list`-Makinenizde varsayılan dizinde veya belirtilen yolda yüklü olan tüm [.NET Core genel araçlarını](global-tools.md) listeler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a>Açıklama

Komut `dotnet tool list` , Kullanıcı genelinde yüklü olan tüm .NET Core genel araçlarını makinenizde (geçerli kullanıcı profili) veya belirtilen yolda listeetmeniz için bir yol sağlar. Komut, paket adını, yüklü sürümü ve genel araç komutunu listeler. List komutunu kullanmak için, `--global` seçeneğini kullanarak tüm Kullanıcı genelindeki araçları görmek istediğinizi veya `--tool-path` seçeneğini kullanarak özel bir yol belirtmeyi belirtmeniz gerekir.

## <a name="options"></a>Seçenekler

`-g|--global`

Kullanıcı genelindeki genel araçları listeler. `--tool-path` Seçeneğiyle birleştirilemez. Bu seçeneği belirtmezseniz, `--tool-path` seçeneğini belirtmeniz gerekir.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--tool-path <PATH>`

Genel araçların bulunacağı bir özel konum belirtir. YOL mutlak veya göreli olabilir. `--global` Seçeneğiyle birleştirilemez. Bu seçeneği belirtmezseniz, `--global` seçeneğini belirtmeniz gerekir.

## <a name="examples"></a>Örnekler

Makinenizde Kullanıcı genelinde yüklenen tüm genel araçları listeler (geçerli kullanıcı profili):

`dotnet tool list -g`

Belirli bir Windows klasöründen genel araçları listeler:

`dotnet tool list --tool-path c:\global-tools`

Belirli bir Linux/macOS klasöründen genel araçları listeler:

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core küresel araçları](global-tools.md)
