---
title: İş parçacığı yapılandırma ayarları
description: .NET Core uygulamaları için iş parçacığı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789848"
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

- Çalışan iş parçacığı havuzu için en az iş parçacığı sayısını belirtir.
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

- Çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını belirtir.
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
