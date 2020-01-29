---
title: Derleme yapılandırması ayarları
description: JıT derleyicisinin .NET Core uygulamaları için nasıl çalıştığını yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0dab3b7b7726a232cf293e338308cf898b370759
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733529"
---
# <a name="run-time-configuration-options-for-compilation"></a>Derleme için çalışma zamanı yapılandırma seçenekleri

## <a name="tiered-compilation"></a>Katmanlı derleme

- Just-In-Time (JıT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır. İki katmanda katmanlı derleme geçişleri yöntemleri:
  - İlk katman kodu daha hızlı üretir ([hızlı JIT](#quick-jit)) veya önceden derlenmiş kod ([readytorun](../whats-new/dotnet-core-3-0.md#readytorun-images)) yükler.
  - İkinci katman arka planda iyileştirilmiş kod üretir ("JıT 'i iyileştirme").
- .NET Core 3,0 ve üzeri sürümlerde katmanlı derleme varsayılan olarak etkindir.
- .NET Core 2,1 ve 2,2 ' de katmanlı derleme varsayılan olarak devre dışıdır.
- Daha fazla bilgi için [katmanlı derleme Kılavuzu](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md)' na bakın.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation` | `true` etkin<br/>`false`-devre dışı |
| **MSBuild özelliği** | `TieredCompilation` | `true` etkin<br/>`false`-devre dışı |
| **Ortam değişkeni** | `COMPlus_TieredCompilation` | `1` etkin<br/>`0`-devre dışı |

### <a name="examples"></a>Örnekler

*runtimeconfig. JSON* dosyası:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a>Hızlı JıT

- JıT derleyicisinin *hızlı JIT*kullanıp kullanmadığını yapılandırır. Döngüler içermeyen ve önceden derlenmiş kodun kullanılamadığı yöntemler için, hızlı JıT bunları daha hızlı bir şekilde derler ancak iyileştirmelere gerek kalmaz.
- Hızlı JıT başlatma süresini azaltır, ancak performansı düşürülmüş performans özellikleriyle kod üretebilir. Örneğin, kod daha fazla yığın alanı kullanabilir, daha fazla bellek ayırabilir ve daha yavaş çalışabilir.
- Hızlı JıT devre dışıysa ancak [katmanlı derleme](#tiered-compilation) etkinleştirilirse, yalnızca önceden derlenmiş kod katmanlı derlemeye katılır. Bir yöntem [Readytorun](../whats-new/dotnet-core-3-0.md#readytorun-images)ile önceden DERLENMIŞSE, JIT davranışı [katmanlı derleme](#tiered-compilation) devre dışı bırakılmışsa aynı olur.
- .NET Core 3,0 ve üzeri sürümlerde, hızlı JıT varsayılan olarak etkindir.
- .NET Core 2,1 ve 2,2 ' de, hızlı JıT varsayılan olarak devre dışıdır.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJit` | `true` etkin<br/>`false`-devre dışı |
| **MSBuild özelliği** | `TieredCompilationQuickJit` | `true` etkin<br/>`false`-devre dışı |
| **Ortam değişkeni** | `COMPlus_TC_QuickJit` | `1` etkin<br/>`0`-devre dışı |

### <a name="examples"></a>Örnekler

*runtimeconfig. JSON* dosyası:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a>Döngüler için hızlı JıT

- JıT derleyicisinin döngüleri içeren yöntemlerde hızlı JıT kullanıp kullanmadığını yapılandırır.
- Döngüler için hızlı JıT 'nin etkinleştirilmesi, başlangıç performansını iyileştirebilir. Ancak uzun süreli döngüler, uzun süreler için daha az iyileştirilmiş kod ile takılmasına sahip olabilir.
- [Hızlı JIT](#quick-jit) devre dışıysa, bu ayarın etkisi yoktur.
- Varsayılan: devre dışı (`false`).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`-devre dışı<br/>`true` etkin |
| **MSBuild özelliği** | `TieredCompilationQuickJitForLoops` | `false`-devre dışı<br/>`true` etkin |
| **Ortam değişkeni** | `COMPlus_TC_QuickJitForLoops` | `0`-devre dışı<br/>`1` etkin |

### <a name="examples"></a>Örnekler

*runtimeconfig. JSON* dosyası:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```
