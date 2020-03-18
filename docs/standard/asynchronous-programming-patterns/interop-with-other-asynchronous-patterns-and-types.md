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
ms.openlocfilehash: 981c13c68eaf1eb0c19f95eb1b097935ea02a16d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159760"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma
.NET Framework 1.0, <xref:System.IAsyncResult> aksi takdirde [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)veya `Begin/End` desen olarak bilinen desen tanıttı.  .NET Framework 2.0 [Olay tabanlı Eşzamanlı Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)eklendi.  .NET Framework 4'ten başlayarak, [Görev tabanlı Eşzamanlı Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) hem APM hem de EAP'nin yerini alır, ancak önceki desenlerden geçiş yordamları oluşturma olanağı sağlar.  
  
 Bu konuda:  
  
- [Görevler ve APM](#APM) [(APM'den TAP'a](#ApmToTap) veya [TAP'ten APM'ye](#TapToApm))  
  
- [Görevler ve EAP](#EAP)  
  
- [Görevler ve bekleme tutamaçları](#WaitHandles) [(bekleme tutamaçlarından TAP'a](#WHToTap) veya [TAP'tan bekleme tutamaçlarına](#TapToWH)kadar)  
  
<a name="APM"></a>
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Görevler ve Eşzamanlı Programlama Modeli (APM)  
  
<a name="ApmToTap"></a>
### <a name="from-apm-to-tap"></a>APM'den TAP'a  
 [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) deseni çok yapılandırılmış olduğundan, bir Tap uygulaması olarak bir APM uygulamasını ortaya çıkarmak için bir sarmalayıcı oluşturmak oldukça kolaydır. Aslında,.NET Framework 4 ile başlayan .NET Framework, bu çeviriyi <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> sağlamak için aşırı yükleme yöntemi biçiminde yardımcı yordamlar içerir.  
  
 Senkron <xref:System.IO.Stream> <xref:System.IO.Stream.Read%2A> yönteme <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> APM karşıtlığını temsil eden sınıfı ve yöntemlerini göz önünde bulundurun:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Bu işlem <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> için tap sarıcıyı uygulamak için yöntemi aşağıdaki gibi kullanabilirsiniz:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Bu uygulama aşağıdakilere benzer:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>
### <a name="from-tap-to-apm"></a>TAP'tan APM'ye  
 Varolan altyapınız APM deseni bekliyorsa, bir TAP uygulamasını alıp APM uygulamasının beklendiği yerde kullanmak da istersiniz.  Görevler oluşturulabildikleri için ve <xref:System.Threading.Tasks.Task> sınıfı <xref:System.IAsyncResult> arabirimini uyguladığı için, bunu yapmak amacıyla daha basit bir yardımcı işlev kullanabilirsiniz. Aşağıdaki kod sınıfın bir <xref:System.Threading.Tasks.Task%601> uzantısı kullanır, ancak genel olmayan görevler için hemen hemen aynı işlevi kullanabilirsiniz.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Şimdi, aşağıdaki TAP uygulamasına sahip olduğunuz bir durumu düşünün:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 ve bu APM uygulamasını sağlamak istiyorsunuz:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 Aşağıdaki örnek, APM'ye bir geçişi gösterir:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Görevler ve Olay Tabanlı Eşzamanlı Desen (EAP)  
 Olay [tabanlı Bir Eşzamanlı Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) uygulamasını sarma, APM deseni sarmaktan daha fazla ilgilidir, çünkü EAP deseni APM deseninden daha fazla varyasyona ve daha az yapıya sahiptir.  Göstermek için, aşağıdaki kod `DownloadStringAsync` yöntemi sarar.  `DownloadStringAsync`bir URI kabul eder, ilerleme yle `DownloadProgressChanged` ilgili birden çok istatistik bildirmek `DownloadStringCompleted` için indirirken olayı yükseltir ve bittiğinde olayı yükseltir.  Nihai sonuç, belirtilen URI'deki sayfanın içeriğini içeren bir dizedir.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>
## <a name="tasks-and-wait-handles"></a>Görevler ve Bekleme Tutamaçları  
  
<a name="WHToTap"></a>
### <a name="from-wait-handles-to-tap"></a>Bekleme Tutamaçları'ndan TAP'a  
 Bekleme tutamaçları eşzamanlı bir desen uygulamasa da, gelişmiş <xref:System.Threading.WaitHandle> geliştiriciler bekleme <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> tutamacı ayarlandığında sınıfı ve eşzamanlı bildirimler yöntemini kullanabilir.  Bekleme tutamacında <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> herhangi bir eşzamanlı bekleme ye yönelik görev tabanlı bir alternatifi etkinleştirmek için yöntemi kaydırabilirsiniz:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Bu yöntemle, varolan <xref:System.Threading.WaitHandle> uygulamaları eşzamanlı yöntemlerde kullanabilirsiniz.  Örneğin, belirli bir zamanda yürütülen eşzamanlı işlem sayısını daraltmak istiyorsanız, bir semafor (nesne) <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> kullanabilirsiniz.  Semafor sayısını *N'ye*başlayarak aynı anda çalışan işlem sayısını *N'ye* daraltabilir, bir işlemi gerçekleştirmek istediğinizde semaforu bekleyebilir ve bir işlemle bitirdiğinizde semaforu serbest bırakabilirsiniz:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Ayrıca bekleme kolları güvenmez ve bunun yerine görevleri tamamen çalışır bir eşzamanlı semafor oluşturabilirsiniz. Bunu yapmak için, 'nin üstüne veri yapıları oluşturmak için [Görev Tabanlı Asynchronous Deseni'ni Tüketme'de](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) tartışılanlar gibi teknikler <xref:System.Threading.Tasks.Task>kullanabilirsiniz.  
  
<a name="TapToWH"></a>
### <a name="from-tap-to-wait-handles"></a>TAP'tan Bekleme Tutamaçlarına  
 Daha önce de belirtildiği <xref:System.Threading.Tasks.Task> gibi, <xref:System.IAsyncResult>sınıf uygular ve <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> bu uygulama <xref:System.Threading.Tasks.Task> tamamlandığında ayarlanacak bir bekleme tutamacı döndüren bir özellik ortaya çıkarır.  Aşağıdaki gibi <xref:System.Threading.WaitHandle> bir <xref:System.Threading.Tasks.Task> a alabilirsiniz:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Görev Tabanlı Zaman Uyumsuz Desen Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
