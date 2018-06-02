---
title: DotNet araç Listele komutu - .NET Core CLI
description: Dotnet araç Listele komutu belirtilen .NET Core genel aracı makinenizden listeler.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5f4793cd37c3a8df06eb6930ad9f381ac70d4e67
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696731"
---
# <a name="dotnet-tool-list"></a>DotNet araç listesi

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet tool list` -Tüm listeler [.NET Core genel Araçları](global-tools.md) makinenizde varsayılan dizin veya belirtilen yol şu anda yüklü.

## <a name="synopsis"></a>Özet

```
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool list` Komutu makinenizde (geçerli kullanıcı profili) veya belirtilen yoldaki tüm .NET Core genel araçları listelemek bir yol yüklü kullanıcı genelinde sağlar. Komut, paket adı, yüklü sürümü ve genel aracı komut listeler. List komutunu kullanmak için ya da tüm kullanıcı genelinde araçları kullanarak görmek istediğiniz belirtmek zorunda `--global` seçeneği veya bir özel yolu kullanarak belirtin `--tool-path` seçeneği.

## <a name="options"></a>Seçenekler

`-g|--global`

Kullanıcı genelinde genel araçları listeler. Birleştirilemez `--tool-path` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--tool-path` seçeneği.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--tool-path <PATH>`

Özel bir konuma genel araçları nerede bulabileceğini belirtir. YOL, mutlak veya göreli olabilir. Birleştirilemez `--global` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--global` seçeneği.

## <a name="examples"></a>Örnekler

Tüm makinenizde (geçerli kullanıcı profili) genel araçlarının yüklü kullanıcı genelinde listeler:

`dotnet tool list -g`

Belirli bir Windows klasörden genel araçları listeler:

`dotnet tool list --tool-path c:\global-tools`

Belirli bir Linux/macOS klasörden genel araçları listeler:

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a>Ayrıca bkz.

[.NET core genel araçları](global-tools.md)