---
ms.openlocfilehash: 9d0791f00db7d830fc5d327af30218a0bbfcb25f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497262"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>Zaman aşımı bağımsız değişkenlerine sahip Task. WaitAll yöntemleri için davranış değişikliği

#### <a name="details"></a>Ayrıntılar

<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> davranış, .NET Framework 4 ' te .NET Framework daha tutarlı yapıldı, bu yöntemler tutarsız şekilde davranmış. Zaman aşımı süresi dolduğunda, bir veya daha fazla görev tamamlandıysa veya yöntem çağrısından önce iptal edildiyse, yöntem bir <xref:System.AggregateException?displayProperty=fullName> özel durum oluşturdu. Zaman aşımı süresi dolduğunda, hiçbir görev tamamlanmadıysa veya yöntem çağrısından önce iptal edildiyse, ancak bir veya daha fazla görev bu durumlara yöntem çağrısından sonra girdiyse, yöntem false değerini döndürdü.<br/><br/>.NET Framework 4,5 ' de, bu yöntem aşırı yüklemeleri, zaman aşımı süresi dolduğunda herhangi bir görev hala çalışıyorsa yanlış döndürür ve <xref:System.AggregateException?displayProperty=fullName> yalnızca bir giriş görevi iptal edildiğinde (yöntem çağrısından önce veya sonra olup olmamasına bakılmaksızın) bir özel durum oluşturur.

#### <a name="suggestion"></a>Öneri

<xref:System.AggregateException?displayProperty=fullName>Çağrılan çağrıdan önce iptal edilen bir görevi tespit eden bir yol olarak yakalandıysa <xref:System.Threading.Tasks.Task.WaitAll%2A> , bu kod, özelliği aracılığıyla aynı algılamayı yapmanız gerekir <xref:System.Threading.Tasks.Task.IsCanceled%2A> (örneğin:. Herhangi biri (t = &gt; t. ısiptal)); .NET Framework 4,6, bu durumda yalnızca tüm beklenen görevler zaman aşımından önce tamamlandığında oluşturulur.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)`

-->
