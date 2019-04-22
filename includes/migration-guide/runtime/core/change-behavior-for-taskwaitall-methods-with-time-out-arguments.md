---
ms.openlocfilehash: 94fad6fe910da6c528c5e13f529a6db274e07d5c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235921"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>Zaman aşımı bağımsız değişkenleri Task.WaitAll yöntemleriyle davranışını değiştir

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> davranışı Bu yöntemler tutarsız hatalı davranan .NET Framework 4 .NET Framework 4.5.In daha tutarlı olarak yapıldı. Bir veya daha fazla görev tamamlandıysa veya yöntem çağrısından önce iptal edildi, zaman aşımı süresi dolduğunda, yöntem oluşturdu bir <xref:System.AggregateException?displayProperty=name> özel durum. Hiçbir görev tamamlanmadıysa veya yöntem çağrısından önce iptal edildi, ancak bir veya daha fazla görev bu durumlara yöntem çağrısından sonra girilen zaman aşımı süresi dolduğunda, yöntem false döndürdü.<br/><br/>.NET Framework 4.5, bu yöntem aşırı yüklemeleri artık herhangi bir görev zaman aşımı aralığı sona ve oluştururlar hala çalıştırıyorsanız, return false bir <xref:System.AggregateException?displayProperty=name> (bunu önce veya sonra yöntemi olup olmadığından bağımsız olarak bir giriş görev yalnızca iptal edildiyse özel durumu Çağrı) ve diğer hiçbir görev hala çalışıyor.|
|Öneri|Varsa bir <xref:System.AggregateException?displayProperty=name> algılama öncesinde iptal edildi bir görev olarak yakalanan <xref:System.Threading.Tasks.Task.WaitAll%2A> çağrılan kodu aracılığıyla aynı algılama yerine yapmalısınız çağrı <xref:System.Threading.Tasks.Task.IsCanceled%2A> özelliği (örneğin:. Any(t =&gt; t.IsCanceled)) olduğundan tüm beklenen görev zaman aşımı önce tamamlanırsa .NET Framework 4.6 yalnızca bu durumda durum oluşturur.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|
