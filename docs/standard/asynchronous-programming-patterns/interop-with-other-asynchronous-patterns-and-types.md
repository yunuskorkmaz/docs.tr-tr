---
title: Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
ms.openlocfilehash: f9fe33bb46f0ba78756c4172032dfbaf45d6fc89
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123975"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma
.NET Framework 1,0, [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)veya `Begin/End` modeli olarak da bilinen <xref:System.IAsyncResult> deseninin tanıtıldığı durumda.  2,0 .NET Framework, [olay tabanlı zaman uyumsuz düzene (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)eklendi.  .NET Framework 4 ' ten başlayarak, [görev tabanlı zaman uyumsuz desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) hem APM hem de EAP 'nin yerine geçer, ancak önceki desenlerden kolayca geçiş yordamları oluşturma yeteneği sağlar.  
  
 Bu konuda:  
  
- [Görevler ve APM](#APM) ([APM 'den](#ApmToTap) , [APM 'ye](#TapToApm)dokunarak veya dokunarak)  
  
- [Görevler ve EAP](#EAP)  
  
- [Görevler ve bekleme tutamaçları](#WaitHandles) ([bekleme tanıtıcılarından](#WHToTap) dokunarak veya [dokunmada bekleyen tutamaçlar](#TapToWH))  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Görevler ve zaman uyumsuz programlama modeli (APM)  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a>APM 'den dokunarak  
 [Zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) modeli çok yapılandırılmış olduğundan, bir APM UYGULAMASıNı bir dokunma uygulama olarak göstermek için bir sarmalayıcı oluşturmak oldukça kolaydır. Aslında, .NET Framework 4 ' ü kullanmaya başlayan .NET Framework, bu çeviriyi sağlamak için <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemi aşırı yüklemeleri biçiminde yardımcı yordamlar içerir.  
  
 <xref:System.IO.Stream> sınıfını ve <xref:System.IO.Stream.BeginRead%2A> ve <xref:System.IO.Stream.EndRead%2A> yöntemlerini göz önünde bulundurun ve bu, zaman uyumlu <xref:System.IO.Stream.Read%2A> yöntemine ait APM 'yi temsil eder:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Bu işlem için bir dokunma sarmalayıcısı uygulamak üzere <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> yöntemini aşağıdaki şekilde kullanabilirsiniz:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Bu uygulama şuna benzer:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a>DOKUNARAK APM 'ye  
 Mevcut altyapınızda APM deseninin kullanılması bekleniyorsa, bir dokunarak uygulama alıp APM uygulamasının beklendiği yerde kullanılması gerekir.  Görevler oluşturulabildikleri için ve <xref:System.Threading.Tasks.Task> sınıfı <xref:System.IAsyncResult> arabirimini uyguladığı için, bunu yapmak amacıyla daha basit bir yardımcı işlev kullanabilirsiniz. Aşağıdaki kod <xref:System.Threading.Tasks.Task%601> sınıfının bir uzantısını kullanır, ancak genel olmayan görevler için neredeyse özdeş bir işlevi kullanabilirsiniz.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Şimdi, aşağıdaki dokunma uygulamasına sahip olduğunuz bir durumu göz önünde bulundurun:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 Bu APM uygulamasını sağlamak istiyorsanız:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 Aşağıdaki örnek, APM 'ye bir geçişi göstermektedir:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Görevler ve olay tabanlı zaman uyumsuz model (EAP)  
 Bir [olay tabanlı zaman uyumsuz model (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) uygulamasını sarmalama, bir APM deseninin sarmalanması dışında daha KARMAŞıKTıR çünkü EAP deseninin APM düzeninden daha fazla çeşitlemesi ve daha az yapısı vardır.  Göstermek için aşağıdaki kod `DownloadStringAsync` yöntemini sarmalar.  `DownloadStringAsync`, bir URI 'yi kabul eder, devam etmekte olan birden fazla istatistiği raporlamak için, indirme sırasında `DownloadProgressChanged` olayını başlatır ve tamamlandığında `DownloadStringCompleted` olayını oluşturur.  Nihai sonuç, belirtilen URI 'deki sayfanın içeriğini içeren bir dizedir.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a>Görevler ve bekleme tutamaçları  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a>Bekleme tanıtıcılarından dokunarak  
 Wait tutamaçları zaman uyumsuz bir model uygulamasa da, gelişmiş geliştiriciler, bir bekleme tutamacı ayarlandığında, zaman uyumsuz bildirimler için <xref:System.Threading.WaitHandle> sınıfını ve <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> yöntemini kullanabilir.  Bir bekleme tanıtıcısından herhangi bir zaman uyumlu bekleme için görev tabanlı bir alternatif sağlamak üzere <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> yöntemini kaydırabilirsiniz:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Bu yöntemle, mevcut <xref:System.Threading.WaitHandle> uygulamalarını zaman uyumsuz metotlarda kullanabilirsiniz.  Örneğin, belirli bir zamanda yürütülen zaman uyumsuz işlemlerin sayısını azaltmak istiyorsanız, bir semafor (<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> nesnesi) kullanabilirsiniz.  Semaforun sayısını *n*olarak başlatarak, semaforda bir işlem gerçekleştirmek istediğiniz zaman ve bir işlemle işiniz bittiğinde semaforu serbest *bırakmak için,* eş zamanlı olarak çalışan işlem sayısını ortadan kaldırabilirsiniz:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Ayrıca, bekleme tanıtıcılarını içermeyen ve bunun yerine görevlerle tamamen çalışabilen bir zaman uyumsuz semafor oluşturabilirsiniz. Bunu yapmak için, <xref:System.Threading.Tasks.Task>en üstünde veri yapıları oluşturmak için [görev tabanlı zaman uyumsuz model tükettiği](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) gibi teknikleri kullanabilirsiniz.  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a>DOKUNARAK bekleme tutamaçlarından  
 Daha önce belirtildiği gibi, <xref:System.Threading.Tasks.Task> sınıfı <xref:System.IAsyncResult>uygular ve bu uygulama, <xref:System.Threading.Tasks.Task> tamamlandığında ayarlanacak bir bekleme tutamacı döndüren <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> özelliğini kullanıma sunar.  Bir <xref:System.Threading.Tasks.Task> için aşağıdaki gibi bir <xref:System.Threading.WaitHandle> edinebilirsiniz:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Görev Tabanlı Zaman Uyumsuz Desen Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
