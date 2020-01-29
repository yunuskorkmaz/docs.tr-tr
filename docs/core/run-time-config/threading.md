---
title: İş parçacığı yapılandırma ayarları
description: .NET Core uygulamaları için iş parçacığı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ed7688d4d8f7178440fe59afc6e2f5e0a11b2a5c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733424"
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
| **MSBuild özelliği** | `ThreadPoolMinThreads` | En az iş parçacığı sayısını temsil eden bir tamsayı |
| **Ortam değişkeni** | YOK | YOK |

### <a name="examples"></a>Örnekler

*runtimeconfig. JSON* dosyası:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a>En fazla iş parçacığı

- Çalışan ThreadPool için en fazla iş parçacığı sayısını belirtir.
- <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> yöntemine karşılık gelir.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | En fazla iş parçacığı sayısını temsil eden bir tamsayı |
| **MSBuild özelliği** | `ThreadPoolMaxThreads` | En fazla iş parçacığı sayısını temsil eden bir tamsayı |
| **Ortam değişkeni** | YOK | YOK |

### <a name="examples"></a>Örnekler

*runtimeconfig. JSON* dosyası:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
