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
ms.openlocfilehash: fe5d8321a62b67a54dc09507e8fd86ee8d5cf74d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276562"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma
.NET Framework 1,0, <xref:System.IAsyncResult> [zaman uyumsuz programlama MODELI (APM)](asynchronous-programming-model-apm.md)veya model olarak da bilinen modeli kullanıma sunmuştur `Begin/End` .  2,0 .NET Framework, [olay tabanlı zaman uyumsuz düzene (EAP)](event-based-asynchronous-pattern-eap.md)eklendi.  .NET Framework 4 ' ten başlayarak, [görev tabanlı zaman uyumsuz desen (TAP)](task-based-asynchronous-pattern-tap.md) hem APM hem de EAP 'nin yerine geçer, ancak önceki desenlerden kolayca geçiş yordamları oluşturma yeteneği sağlar.  
  
 Bu konuda:  
  
- [Görevler ve APM](#APM) ([APM 'den](#ApmToTap) , [APM 'ye](#TapToApm)dokunarak veya dokunarak)  
  
- [Görevler ve EAP](#EAP)  
  
- [Görevler ve bekleme tutamaçları](#WaitHandles) ([bekleme tanıtıcılarından](#WHToTap) dokunarak veya [dokunmada bekleyen tutamaçlar](#TapToWH))  
  
<a name="APM"></a>
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Görevler ve zaman uyumsuz programlama modeli (APM)  
  
<a name="ApmToTap"></a>
### <a name="from-apm-to-tap"></a>APM 'den dokunarak  
 [Zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md) modeli çok yapılandırılmış olduğundan, bir APM UYGULAMASıNı bir dokunma uygulama olarak göstermek için bir sarmalayıcı oluşturmak oldukça kolaydır. Aslında, .NET Framework 4 ' ü kullanmaya başlayan .NET Framework, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> Bu çeviriyi sağlamak için yöntem aşırı yüklemeleri biçiminde yardımcı yordamlar içerir.  
  
 <xref:System.IO.Stream> <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> Zaman uyumlu yöntemin APM 'sini temsil eden sınıfını ve yöntemlerini göz önünde bulundurun <xref:System.IO.Stream.Read%2A> :  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType>Bu işlem için BIR dokunma sarmalayıcısı uygulamak için yöntemini aşağıdaki şekilde kullanabilirsiniz:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Bu uygulama şuna benzer:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>
### <a name="from-tap-to-apm"></a>DOKUNARAK APM 'ye  
 Mevcut altyapınızda APM deseninin kullanılması bekleniyorsa, bir dokunarak uygulama alıp APM uygulamasının beklendiği yerde kullanılması gerekir.  Görevler oluşturulabildikleri için ve <xref:System.Threading.Tasks.Task> sınıfı <xref:System.IAsyncResult> arabirimini uyguladığı için, bunu yapmak amacıyla daha basit bir yardımcı işlev kullanabilirsiniz. Aşağıdaki kod, sınıfının bir uzantısını kullanır <xref:System.Threading.Tasks.Task%601> , ancak genel olmayan görevler için neredeyse özdeş bir işlevi kullanabilirsiniz.  
  
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
 Bir [olay tabanlı zaman uyumsuz model (EAP)](event-based-asynchronous-pattern-eap.md) uygulamasını sarmalama, bir APM deseninin sarmalanması dışında daha KARMAŞıKTıR çünkü EAP deseninin APM düzeninden daha fazla çeşitlemesi ve daha az yapısı vardır.  Göstermek için aşağıdaki kod yöntemini sarmalar `DownloadStringAsync` .  `DownloadStringAsync`bir URI 'yi kabul eder, `DownloadProgressChanged` İlerlemede birden fazla istatistik raporlamak için olayı indirme sırasında başlatır ve `DownloadStringCompleted` tamamlandığında olayı başlatır.  Nihai sonuç, belirtilen URI 'deki sayfanın içeriğini içeren bir dizedir.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>
## <a name="tasks-and-wait-handles"></a>Görevler ve bekleme tutamaçları  
  
<a name="WHToTap"></a>
### <a name="from-wait-handles-to-tap"></a>Bekleme tanıtıcılarından dokunarak  
 Wait tutamaçları zaman uyumsuz bir model uygulamasa da, gelişmiş geliştiriciler <xref:System.Threading.WaitHandle> <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> bir bekleme tutamacı ayarlandığında, zaman uyumsuz bildirimler için sınıfını ve yöntemini kullanabilir.  <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A>Bir bekleme tanıtıcısından herhangi bir zaman uyumlu bekleme için görev tabanlı bir alternatif sağlamak üzere yöntemini kaydırabilirsiniz:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Bu yöntemle, mevcut <xref:System.Threading.WaitHandle> uygulamaları zaman uyumsuz metotlarda kullanabilirsiniz.  Örneğin, belirli bir zamanda yürütülen zaman uyumsuz işlemlerin sayısını azaltmak istiyorsanız, bir semafor (bir <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> nesne) kullanabilirsiniz.  Semaforun sayısını *n*olarak başlatarak, semaforda bir işlem gerçekleştirmek istediğiniz zaman ve bir işlemle işiniz bittiğinde semaforu serbest *bırakmak için,* eş zamanlı olarak çalışan işlem sayısını ortadan kaldırabilirsiniz:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Ayrıca, bekleme tanıtıcılarını içermeyen ve bunun yerine görevlerle tamamen çalışabilen bir zaman uyumsuz semafor oluşturabilirsiniz. Bunu yapmak için, üzerine veri yapıları oluşturmak için [görev tabanlı zaman uyumsuz model tükettiği](consuming-the-task-based-asynchronous-pattern.md) gibi teknikleri kullanabilirsiniz <xref:System.Threading.Tasks.Task> .  
  
<a name="TapToWH"></a>
### <a name="from-tap-to-wait-handles"></a>DOKUNARAK bekleme tutamaçlarından  
 Daha önce belirtildiği gibi, <xref:System.Threading.Tasks.Task> sınıfı uygular <xref:System.IAsyncResult> ve bu uygulama <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> tamamlandığında ayarlanacak bir bekleme tutamacı döndüren bir özelliği kullanıma sunar <xref:System.Threading.Tasks.Task> .  Bir <xref:System.Threading.WaitHandle> için aşağıdaki şekilde bir edinebilirsiniz <xref:System.Threading.Tasks.Task> :  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](task-based-asynchronous-pattern-tap.md)
- [Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](implementing-the-task-based-asynchronous-pattern.md)
- [Görev Tabanlı Zaman Uyumsuz Desen Kullanma](consuming-the-task-based-asynchronous-pattern.md)
