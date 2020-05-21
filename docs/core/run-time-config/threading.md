---
title: İş parçacığı yapılandırma ayarları
description: .NET Core uygulamaları için iş parçacığı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761934"
---
# <a name="run-time-configuration-options-for-threading"></a>İş parçacığı için çalışma zamanı yapılandırma seçenekleri

## <a name="cpu-groups"></a>CPU grupları

- İş parçacıklarının CPU grupları arasında otomatik olarak dağıtılıp dağıtılmayacağını yapılandırır.
- Bu ayarı atlarsanız, iş parçacıkları CPU grupları arasında dağıtılır. Bu değeri değerine ayarlamaya eşdeğerdir `0` .

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_Thread_UseAllCpuGroups` | `0`-devre dışı<br/>`1`-etkin |

## <a name="minimum-threads"></a>En düşük iş parçacıkları

- Çalışan iş parçacığı havuzu için en az iş parçacığı sayısını belirtir.
- Yöntemine karşılık gelir <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> .

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MinThreads` | En az iş parçacığı sayısını temsil eden bir tamsayı |
| **MSBuild özelliği** | `ThreadPoolMinThreads` | En az iş parçacığı sayısını temsil eden bir tamsayı |
| **Ortam değişkeni** | Yok | Yok |

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
- Yöntemine karşılık gelir <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> .

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | En fazla iş parçacığı sayısını temsil eden bir tamsayı |
| **MSBuild özelliği** | `ThreadPoolMaxThreads` | En fazla iş parçacığı sayısını temsil eden bir tamsayı |
| **Ortam değişkeni** | Yok | Yok |

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
