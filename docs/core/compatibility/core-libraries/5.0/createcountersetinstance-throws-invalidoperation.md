---
title: 'Son değişiklik: örnek zaten varsa CreateCounterSetInstance InvalidOperationException oluşturur'
description: .NET 5 ' in, CounterSet. CreateCounterSetInstance, sayaç zaten varsa farklı bir özel durum oluşturan çekirdek .NET kitaplıklarında, .NET 5 ' i değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: bf59677a85538bc4992c589f8642ab4a0fce54ac
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257576"
---
# <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a>CounterSet. CreateCounterSetInstance şimdi örnek zaten varsa InvalidOperationException oluşturur

.NET 5 ' den başlayarak, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> <xref:System.InvalidOperationException> <xref:System.ArgumentException> sayaç kümesi zaten varsa bir yerine bir oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework ve .NET Core 1,0 ile 3,1 arasında, çağırarak sayaç kümesinin bir örneğini oluşturabilirsiniz <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> . Ancak, sayaç kümesi zaten varsa, yöntem bir <xref:System.ArgumentException> özel durum oluşturur.

.NET 5 ve sonraki sürümlerinde, çağırdığınızda <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> ve sayaç kümesi varsa, bir <xref:System.InvalidOperationException> özel durum oluşturulur.

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
