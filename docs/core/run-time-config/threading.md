---
title: Config ayarlarını iş parçacığı
description: .NET Core uygulamaları için iş parçacığı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789848"
---
# <a name="run-time-configuration-options-for-threading"></a>İş parçacığı için çalışma zamanı yapılandırma seçenekleri

## <a name="cpu-groups"></a>CPU grupları

- İş parçacıklarının CPU gruplarına otomatik olarak dağıtılıp dağıtılmayacağını yapılandırır.
- Varsayılan: Devre`0`Dışı ( ).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_Thread_UseAllCpuGroups` | `0`- engelli<br/>`1`- etkin |

## <a name="minimum-threads"></a>Minimum iş parçacıkları

- Alt iş parçacığı havuzu için en az iş parçacığı sayısını belirtir.
- Yönteme <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> karşılık gelir.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `System.Threading.ThreadPool.MinThreads` | En az iş parçacığı sayısını temsil eden bir karşıcı |
| **MSBuild özelliği** | `ThreadPoolMinThreads` | En az iş parçacığı sayısını temsil eden bir karşıcı |
| **Ortam değişkeni** | Yok | Yok |

### <a name="examples"></a>Örnekler

*runtimeconfig.json* dosyası:

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

## <a name="maximum-threads"></a>Maksimum iş parçacıkları

- Alt iş parçacığı havuzu için en fazla iş parçacığı sayısını belirtir.
- Yönteme <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> karşılık gelir.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `System.Threading.ThreadPool.MaxThreads` | En fazla iş parçacığı sayısını temsil eden bir sonsayı |
| **MSBuild özelliği** | `ThreadPoolMaxThreads` | En fazla iş parçacığı sayısını temsil eden bir sonsayı |
| **Ortam değişkeni** | Yok | Yok |

### <a name="examples"></a>Örnekler

*runtimeconfig.json* dosyası:

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
