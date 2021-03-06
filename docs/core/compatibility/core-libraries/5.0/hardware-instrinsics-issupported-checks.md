---
title: 'Son değişiklik: donanım içi IsSupported denetimleri iç içe türler için farklılık gösterebilir'
description: X64 'Ün kontrol edildiği çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin. Donanım iç öğeleri için desteklenen ısbıg, artık farklı bir sonuç verebilir.
ms.date: 11/01/2020
ms.openlocfilehash: 5c6049ad5881c0389870cfd5e1550f8358c67599
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257459"
---
# <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a>Donanım iç tarafından desteklenen denetimler iç içe türler için farklılık gösterebilir

`<Isa>.X64.IsSupported`' Nin, `<Isa>` <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> ad alanındaki sınıfların başvurduğu, artık önceki .net sürümlerine farklı bir sonuç üretebileceği denetleniyor.

> [!TIP]
> *ISA* , sektör standardı mimarisi için temsil eder.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 'in önceki sürümlerinde, bazı <xref:System.Runtime.Intrinsics.X86> donanım içi türler, örneğin, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType> iç içe geçmiş bir `X64` sınıf sunmaz. Bu türler için, bir `<Isa>.X64.IsSupported` `IsSupported` üst sınıfının iç içe sınıfındaki bir özelliğe çözüldü `X64` `<Isa>` . Bu, özelliği `true` döndüğünde bile döndürebilse anlamına gelir `<Isa>.IsSupported` `false` .

.NET 5 ve sonraki sürümlerinde tüm <xref:System.Runtime.Intrinsics.X86> türler, `X64` desteği uygun şekilde raporlayan iç içe bir sınıf kullanıma sunar. Bu, genel hiyerarşinin doğru kalmasını sağlar ve bu durumda olduğu gibi `<Isa>.X64.IsSupported` `true` `<Isa>.IsSupported` kabul edilebilir `true` .

## <a name="reason-for-change"></a>Değişiklik nedeni

Varsa `<Isa>.X64.IsSupported` `true` , `<Isa>.IsSupported` aynı zamanda olarak da ima edilir `true` . Ancak, üye çözümlemenin C# ' ta çalışmasına bağlı olarak, iç içe yerleştirilmiş bir sınıfı olmayan sınıflar `X64` her zaman durum olmadığı ve Kullanıcı kodundaki hatalara işaret eden bir durum ortaya çıkardı.

## <a name="recommended-action"></a>Önerilen eylem

Gerekirse, uygun ISA 'yı denetlemeyi denetleyen kodu ayarlayın `IsSupported` .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->
