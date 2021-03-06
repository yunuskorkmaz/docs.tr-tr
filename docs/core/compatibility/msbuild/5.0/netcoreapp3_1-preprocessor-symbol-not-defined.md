---
title: 'Son değişiklik: NETCOREAPP3_1 ön işlemci sembolü .NET 5 hedeflenirken tanımlanmaz'
description: .NET 5 ' teki son değişiklik hakkında bilgi edinin. burada, projeler artık önceki sürümler için önişlemci sembolleri tanımlamaz.
ms.date: 09/17/2020
ms.openlocfilehash: 390c8f5af97510db4652f3f42db577e6de158020
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256536"
---
# <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a>NETCOREAPP3_1 Önişlemci sembolü .NET 5 hedeflenirken tanımlanmaz

.NET 5 RC2 ve sonraki sürümlerinde, projeler artık önceki sürümler için ön işlemci sembolleri tanımlamıyor, ancak yalnızca hedeflerine ait olan sürüm için. Bu, .NET Core 1,0-3,1 ile aynı davranıştır.

## <a name="version-introduced"></a>Sunulan sürüm

5,0 RC2

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5 Preview 7 ' de RC1 ile, hedeflenen projeler `net5.0` hem hem `NETCOREAPP3_1` de `NET5_0` Önişlemci sembollerini tanımlar. Bu davranış değişikliğinin arkasındaki amaç, .NET 5 ' den itibaren Koşullu derleme [sembolleri birikimli olur](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).

.NET 5 RC2 ve üzeri sürümlerde, projeler yalnızca hedef Framework takma adları (tfd) için, daha önceki sürümler için değil, sembolleri tanımlar.

## <a name="reason-for-change"></a>Değişiklik nedeni

Preview 7 ' den değişiklik, müşteri geri bildirimi nedeniyle geri döndürüldü. Önceki sürümler için sembolleri ve karıştırılan müşterileri tanımlama ve C# derleyicisinde bir hata olduğu varsayılır.

## <a name="recommended-action"></a>Önerilen eylem

`#if`Mantığınızın `NETCOREAPP3_1` Proje `net5.0` ya da daha yüksek bir hedef olduğunda tanımlı olduğunu varsaymıyor olduğundan emin olun. Bunun yerine, `NETCOREAPP3_1` yalnızca proje açıkça hedeflediğinde tanımlı olduğunu varsayın `netcoreapp3.1` .

Örneğin, projeniz .NET Core 2,1 ve .NET Core 3,1 için çoklu hedeflerse ve .NET Core 3,1 ' de tanıtılan API 'Leri çağırırsanız, `#if` mantığınızın aşağıdaki gibi görünmesi gerekir:

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

## <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
