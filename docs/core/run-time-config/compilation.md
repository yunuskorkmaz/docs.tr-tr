---
title: Derleme yapılandırması ayarları
description: JıT derleyicisinin .NET Core uygulamaları için nasıl çalıştığını yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bcc445b6edc48d9432ee614b0b19c9c25621f4a0
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802822"
---
# <a name="run-time-configuration-options-for-compilation"></a>Derleme için çalışma zamanı yapılandırma seçenekleri

## <a name="tiered-compilation"></a>Katmanlı derleme

- JıT derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.
- .NET Core 3,0 ve üzeri sürümlerde katmanlı derleme varsayılan olarak etkindir.
- .NET Core 2,1 ve 2,2 ' de katmanlı derleme varsayılan olarak devre dışıdır.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation` | `true` etkin<br/>`false`-devre dışı |
| **Ortam değişkeni** | `COMPlus_TieredCompilation` | `1` etkin<br/>`0`-devre dışı |
