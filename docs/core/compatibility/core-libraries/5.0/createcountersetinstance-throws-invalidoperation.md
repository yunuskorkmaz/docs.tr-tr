---
title: 'Son değişiklik: örnek zaten varsa CreateCounterSetInstance InvalidOperationException oluşturur'
description: Bir sayaç zaten mevcutsa, CounterSet. CreateCounterSetInstance 'ın farklı bir özel durum oluşturulduğu çekirdek .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 28042690b71f9b86e4e54748ec75467bbe232684
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761562"
---
# <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a>CounterSet. CreateCounterSetInstance şimdi örnek zaten varsa InvalidOperationException oluşturur

.NET 5,0 ' den başlayarak, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> <xref:System.InvalidOperationException> <xref:System.ArgumentException> sayaç kümesi zaten varsa bir yerine bir oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework ve .NET Core 1,0 ile 3,1 arasında, çağırarak sayaç kümesinin bir örneğini oluşturabilirsiniz <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> . Ancak, sayaç kümesi zaten varsa, yöntem bir <xref:System.ArgumentException> özel durum oluşturur.

.NET 5,0 ve sonraki sürümlerinde, çağırdığınızda <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> ve sayaç kümesi varsa, bir <xref:System.InvalidOperationException> özel durum oluşturulur.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

<xref:System.ArgumentException>Çağrılırken uygulamanızda özel durumları yakalarsanız <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> özel durumları da yakalamaya göz önünde bulundurun <xref:System.InvalidOperationException> .

> [!NOTE]
> Yakalama <xref:System.ArgumentException> özel durumları önerilmez.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
