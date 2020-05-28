---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144493"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a>CounterSet. CreateCounterSetInstance şimdi örnek zaten varsa InvalidOperationException oluşturur

.NET 5,0 ' den başlayarak, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> <xref:System.InvalidOperationException> <xref:System.ArgumentException> sayaç kümesi zaten varsa bir yerine bir oluşturur.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework ve .NET Core 1,0 ile 3,1 arasında, çağırarak sayaç kümesinin bir örneğini oluşturabilirsiniz <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> . Ancak, sayaç kümesi zaten varsa, yöntem bir <xref:System.ArgumentException> özel durum oluşturur.

.NET 5,0 ve sonraki sürümlerinde, çağırdığınızda <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> ve sayaç kümesi varsa, bir <xref:System.InvalidOperationException> özel durum oluşturulur.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 5

#### <a name="recommended-action"></a>Önerilen eylem

<xref:System.ArgumentException>Çağrılırken uygulamanızda özel durumları yakalarsanız <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> özel durumları da yakalamaya göz önünde bulundurun <xref:System.InvalidOperationException> .

> [!NOTE]
> Yakalama <xref:System.ArgumentException> özel durumları önerilmez.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
