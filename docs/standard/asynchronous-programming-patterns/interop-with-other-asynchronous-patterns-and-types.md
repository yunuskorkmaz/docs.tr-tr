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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05b53016712f75e45636979d77bfd27116ce8e14
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44510070"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma
.NET Framework 1.0 sunulan <xref:System.IAsyncResult> deseni, aksi takdirde olarak bilinen [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), veya `Begin/End` deseni.  .NET Framework 2.0 eklenen [olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  .NET Framework 4 ile başlayarak [görev tabanlı zaman uyumsuz desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) APM hem de EAP yerini alır, ancak kolayca geçiş rutinleri önceki desenleri oluşturma imkanı sağlar.  
  
 Bu konuda:  
  
-   [Görevler ve APM](#APM) ([DOKUNUN için APM gelen](#ApmToTap) veya [APM için DOKUNUN gelen](#TapToApm))  
  
-   [Görevler ve EAP](#EAP)  
  
-   [Görevler ve bekleme tanıtıcıları](#WaitHandles) ([DOKUNUN bekleme tanıtıcıları gelen](#WHToTap) veya [bekleme tanıtıcıları için DOKUNUN gelen](#TapToWH))  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Görevler ve zaman uyumsuz programlama modeli (APM)  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a>Bir APM için DOKUNUN  
 Çünkü [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) desen çok yapılandırılmış, APM uygulaması bir TAP uygulaması olarak kullanıma sunmak için bir sarmalayıcı oluşturmak oldukça kolaydır. İle başlayarak .NET Framework, aslında [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Yardımcısı biçiminde içerir <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> bu çeviri sağlamak için yöntem aşırı yüklemeleri.  
  
 Göz önünde bulundurun <xref:System.IO.Stream> sınıf ve onun <xref:System.IO.Stream.BeginRead%2A> ve <xref:System.IO.Stream.EndRead%2A> APM karşılığı temsil etmek için zaman uyumlu yöntemleri <xref:System.IO.Stream.Read%2A> yöntemi:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Kullanabileceğiniz <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> yöntemi bu işlem için DOKUNUN sarmalayıcı gibi uygulamak için:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Bu uygulama, aşağıdakine benzer:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a>APM için DOKUNUN  
 Var olan altyapınızın APM desenini bekliyorsa bir TAP uygulaması alıp APM uygulaması beklenirken kullanmak isteyeceksiniz.  Görevler oluşturulabildikleri için ve <xref:System.Threading.Tasks.Task> sınıfı <xref:System.IAsyncResult> arabirimini uyguladığı için, bunu yapmak amacıyla daha basit bir yardımcı işlev kullanabilirsiniz. Aşağıdaki kod uzantısı kullanır <xref:System.Threading.Tasks.Task%601> sınıfı, ancak kullanabileceğiniz bir neredeyse aynı işlevi için genel olmayan görevleri.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Şimdi aşağıdaki TAP uygulaması sahip olduğu bir durum düşünün:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 ve bu APM uygulaması sağlamak istiyorsanız:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 Aşağıdaki örnek, bir geçiş APM gösterir:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Görevleri ve olay-tabanlı zaman uyumsuz desen (EAP)  
 Sarmalama bir [olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) uygulamasıdır bir APM desenini sarmalama değerinden daha karmaşık EAP düzeni daha fazla çeşitleme ve APM desenini daha az yapısı olduğundan.  Göstermek için aşağıdaki kodu sarmalar `DownloadStringAsync` yöntemi.  `DownloadStringAsync` bir URI kabul eder, başlatır `DownloadProgressChanged` ilerleme ve harekete geçirirse birden çok istatistiği raporlamak için indirme sırasında olay `DownloadStringCompleted` bittiğinde olay.  Nihai sonucu belirtilen URI'de bir sayfanın içeriğini içeren bir dizedir.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a>Görevler ve bekleme tanıtıcıları  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a>Bekleme işleyicilerine DOKUNUN  
 Bekleme tanıtıcıları zaman uyumsuz bir desenin uygulamayıp olsa da, İleri düzey geliştiriciler kullanabilir <xref:System.Threading.WaitHandle> sınıfı ve <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> bekleme tanıtıcısı ayarlandığında zaman uyumsuz bildirimler için yöntemi.  Sarmalamadan <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> yöntemi herhangi bir bekleme tanıtıcısı eşzamanlı bekleme görev tabanlı bir alternatif etkinleştirmek için:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Bu yöntemi, mevcut kullanabileceğiniz <xref:System.Threading.WaitHandle> uygulamalarında zaman uyumsuz yöntemler.  Örneğin, belirli bir zamanda yürütülen zaman uyumsuz işlemlerin sayısını azaltma istiyorsanız semafor kullanabilir (bir <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> nesne).  Kısıtlayabilir miyim *N* , aynı anda çalışan işlemlerin sayısı için semafor'ın sayısı başlatma tarafından *N*, istediğiniz zaman, istediğiniz bir işlemi gerçekleştirmek için semafor üzerinde bekleyen ve serbest bırakma bir işlem ile işiniz bittiğinde semafor:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Ayrıca, bekleme tanıtıcıları üzerinde kullanmayan ve bunun yerine görevleriyle tamamen çalışır bir zaman uyumsuz semafor oluşturabilirsiniz. Bunu yapmak için bu anlatıldığı gibi teknikler kullanabilirsiniz [görev tabanlı zaman uyumsuz desen kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) üst kısmındaki veri yapıları oluşturmaya yönelik <xref:System.Threading.Tasks.Task>.  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a>Bekleme tanıtıcıları için DOKUNUN  
 Daha önce belirtildiği gibi <xref:System.Threading.Tasks.Task> sınıfının uygular <xref:System.IAsyncResult>, ve bu uygulamayı kullanıma sunan bir <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> ne zaman ayarlayacak bir bekleme tanıtıcısı döndüren özellik <xref:System.Threading.Tasks.Task> tamamlar.  Alabileceğiniz bir <xref:System.Threading.WaitHandle> için bir <xref:System.Threading.Tasks.Task> şu şekilde:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
- [Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
- [Görev Tabanlı Zaman Uyumsuz Desen Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
