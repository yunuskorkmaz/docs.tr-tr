---
title: İş parçacığı yapılandırma ayarları
description: .NET Core uygulamaları için iş parçacığı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6a920dbc301830e3f4c95bf637ff3de6d4f464ff
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802766"
---
# <a name="run-time-configuration-options-for-threading"></a>İş parçacığı için çalışma zamanı yapılandırma seçenekleri

## <a name="cpu-groups"></a>CPU grupları

- İş parçacıklarının CPU grupları arasında otomatik olarak dağıtılıp dağıtılmayacağını yapılandırır.
- Varsayılan: devre dışı (`0`).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | YOK | YOK |
| **Ortam değişkeni** | `COMPlus_Thread_UseAllCpuGroups` | `0`-devre dışı<br/>`1` etkin |

## <a name="minimum-threads"></a>En düşük iş parçacıkları

- Çalışan ThreadPool için en az iş parçacığı sayısını belirtir.
- <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> yöntemine karşılık gelir.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MinThreads` | En az iş parçacığı sayısını temsil eden bir tamsayı |
| **Ortam değişkeni** | YOK | YOK |

## <a name="maximum-threads"></a>En fazla iş parçacığı

- Çalışan ThreadPool için en fazla iş parçacığı sayısını belirtir.
- <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> yöntemine karşılık gelir.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | En fazla iş parçacığı sayısını temsil eden bir tamsayı |
| **Ortam değişkeni** | YOK | YOK |
