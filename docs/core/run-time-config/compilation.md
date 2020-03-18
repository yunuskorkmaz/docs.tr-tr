---
title: Derleme config ayarları
description: JIT derleyicisinin .NET Core uygulamaları için nasıl çalıştığını yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092895"
---
# <a name="run-time-configuration-options-for-compilation"></a>Derleme için çalışma zamanı yapılandırma seçenekleri

## <a name="tiered-compilation"></a>Katmanlı derleme

- Tam zamanında (JIT) derleyicinin [katmanlı derleme](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır. Katmanlı derleme yöntemlerini iki katman dan geçirir:
  - Birinci katman kodu daha hızlı[(hızlı JIT)](#quick-jit)oluşturur veya önceden derlenmiş kodu[(ReadyToRun)](#readytorun)yükler.
  - İkinci katman arka planda en iyi duruma getirilmiş kod oluşturur ("JIT'yi optimize etme").
- .NET Core 3.0 ve sonraki durumlarda, katmanlı derleme varsayılan olarak etkinleştirilir.
- .NET Core 2.1 ve 2.2'de katmanlı derleme varsayılan olarak devre dışı bırakılır.
- Daha fazla bilgi için [Katmanlı derleme kılavuzuna](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md)bakın.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation` | `true`- etkin<br/>`false`- engelli |
| **MSBuild özelliği** | `TieredCompilation` | `true`- etkin<br/>`false`- engelli |
| **Ortam değişkeni** | `COMPlus_TieredCompilation` | `1`- etkin<br/>`0`- engelli |

### <a name="examples"></a>Örnekler

*runtimeconfig.json* dosyası:

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

## <a name="quick-jit"></a>Hızlı JIT

- JIT derleyicisinin hızlı *JIT*kullanıp kullanmayacağını yapılandırır. Döngü içermeyen ve önceden derlenmiş kodun kullanılamadığı yöntemler için, hızlı JIT bunları daha hızlı ancak optimizasyonlar olmadan derler.
- Hızlı JIT etkinleştirme başlangıç süresini azaltır, ancak bozulmuş performans özellikleri ile kod üretebilir. Örneğin, kod daha fazla yığın alanı kullanabilir, daha fazla bellek tahsis edebilir ve daha yavaş çalışabilir.
- Hızlı JIT devre dışı bırakılır, ancak [katmanlı derleme](#tiered-compilation) etkinse, yalnızca önceden derlenmiş kod katmanlı derlemeye katılır. Bir yöntem [ReadyToRun](#readytorun)ile önceden derlenmiyorsa, JIT davranışı [katmanlı derleme](#tiered-compilation) devre dışı bırakılmış gibi aynıdır.
- .NET Core 3.0 ve sonraki durumlarda, hızlı JIT varsayılan olarak etkinleştirilir.
- .NET Core 2.1 ve 2.2'de, hızlı JIT varsayılan olarak devre dışı bırakılır.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJit` | `true`- etkin<br/>`false`- engelli |
| **MSBuild özelliği** | `TieredCompilationQuickJit` | `true`- etkin<br/>`false`- engelli |
| **Ortam değişkeni** | `COMPlus_TC_QuickJit` | `1`- etkin<br/>`0`- engelli |

### <a name="examples"></a>Örnekler

*runtimeconfig.json* dosyası:

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

## <a name="quick-jit-for-loops"></a>Döngüler için hızlı JIT

- JIT derleyicisinin döngü içeren yöntemlerde hızlı JIT kullanıp kullanmayacağını yapılandırır.
- Döngüler için hızlı JIT'yi etkinleştirmek başlangıç performansını artırabilir. Ancak, uzun süren döngüler uzun süreler için daha az optimize edilmiş kodda sıkışıp kalabilir.
- [Hızlı JIT](#quick-jit) devre dışı bırakılırsa, bu ayarın hiçbir etkisi yoktur.
- Varsayılan: Devre`false`Dışı ( ).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`- engelli<br/>`true`- etkin |
| **MSBuild özelliği** | `TieredCompilationQuickJitForLoops` | `false`- engelli<br/>`true`- etkin |
| **Ortam değişkeni** | `COMPlus_TC_QuickJitForLoops` | `0`- engelli<br/>`1`- etkin |

### <a name="examples"></a>Örnekler

*runtimeconfig.json* dosyası:

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

## <a name="readytorun"></a>Readytorun

- .NET Core çalışma zamanının ready ReadyToRun verileriyle görüntüler için önceden derlenmiş kod kullanıp kullanmayacağını yapılandırır. Bu seçeneğin devre dışı bırakılması çalışma zamanını JIT-derleme çerçeve koduna zorlar.
- Daha fazla bilgi için [ReadyToRun'a](../whats-new/dotnet-core-3-0.md#readytorun-images)bakın.
- Varsayılan: Etkin`1`( ).

| | Ayar adı | Değerler |
| - | - | - |
| **Ortam değişkeni** | `COMPlus_ReadyToRun` | `1`- etkin<br/>`0`- engelli |
