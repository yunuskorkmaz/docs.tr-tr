---
title: DotNet araç Listele komutu
description: Belirtilen .NET Core genel aracı makinenizden dotnet araç Listele komutu listelenmektedir.
ms.date: 05/29/2018
ms.openlocfilehash: 0c17534beb80ed87a8f260342b0f82882a9e17b6
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169774"
---
# <a name="dotnet-tool-list"></a>DotNet araç listesi

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet tool list` -Tüm listeler [.NET Core Araçları Genel](global-tools.md) makinenizde varsayılan dizinde veya belirtilen yolun şu anda yüklü.

## <a name="synopsis"></a>Özeti

```console
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool list` Komut makinenizde (geçerli kullanıcı profili) veya belirtilen yolda yüklü kullanıcı genelinde tüm .NET Core genel araçları listelemek bir yol sağlar. Komut, paket adı, sürümü ve genel aracı komut listeler. LIST komutu kullanmak için ya da tüm kullanıcı genelinde araçları kullanarak görmek istediğinizi belirtmek olması `--global` kullanarak bir özel yol belirtin veya seçeneği `--tool-path` seçeneği.

## <a name="options"></a>Seçenekler

`-g|--global`

Kullanıcı genelinde genel araçları listeler. İle birleştirilemez `--tool-path` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--tool-path` seçeneği.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--tool-path <PATH>`

Özel bir konuma genel Araçlar nerede bulacağını belirtir. YOL mutlak veya göreli olabilir. İle birleştirilemez `--global` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--global` seçeneği.

## <a name="examples"></a>Örnekler

Tüm makinenizde (geçerli kullanıcı profili) genel araçları yüklü kullanıcı genelinde listeler:

`dotnet tool list -g`

Belirli bir Windows klasörü genel araçları listeler:

`dotnet tool list --tool-path c:\global-tools`

Belirli Linux/macOS klasöründe bulunan genel araçlarını listeler:

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a>Ayrıca bkz.

* [.NET core Araçları Genel](global-tools.md)