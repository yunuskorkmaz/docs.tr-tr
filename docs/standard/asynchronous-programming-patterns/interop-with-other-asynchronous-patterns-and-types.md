---
title: "Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a46358052eb93662408f9c01592f917eee4540b9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma
.NET Framework 1.0 sunulan <xref:System.IAsyncResult> düzeni, aksi takdirde olarak bilinen [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), veya `Begin/End` düzeni.  .NET Framework 2.0 eklenen [olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  .NET Framework 4'ile başlayan [görev tabanlı zaman uyumsuz desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) APM ve EAP yerini alır, ancak kolayca geçiş yordamları önceki model oluşturma yeteneği sağlar.  
  
 Bu konuda:  
  
-   [Görevler ve APM](#APM) ([DOKUNUN APM gelen](#ApmToTap) veya [APM DOKUNUN gelen](#TapToApm))  
  
-   [Görevleri ve EAP](#EAP)  
  
-   [Görevler ve bekleme tanıtıcıları](#WaitHandles) ([DOKUNUN bekleme tanıtıcıları gelen](#WHToTap) veya [bekleme tanıtıcıları için DOKUNUN gelen](#TapToWH))  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Görevler ve zaman uyumsuz programlama modeli (APM)  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a>APM için DOKUNUN  
 Çünkü [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) düzeni çok yapılandırılmış, APM uygulaması DOKUNUN uygulaması olarak kullanıma sunmak için bir kapsayıcı oluşturmak oldukça kolaydır. Aslında .NET Framework ile başlayarak, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], biçiminde Yardımcısı yordamları içerir <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemi aşırı bu çeviri sağlamak için.  
  
 Göz önünde bulundurun <xref:System.IO.Stream> sınıfı ve onun <xref:System.IO.Stream.BeginRead%2A> ve <xref:System.IO.Stream.EndRead%2A> APM karşılık gelen göstermek için zaman uyumlu yöntemleri <xref:System.IO.Stream.Read%2A> yöntemi:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Kullanabileceğiniz <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> yöntemi bu işlem için DOKUNUN sarmalayıcı aşağıdaki gibi gerçekleştirin:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Bu uygulama aşağıdakine benzer:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a>APM için DOKUNUN  
 Mevcut altyapınızı APM düzeni görüyorsa de DOKUNUN uygulama alabilir ve APM uygulaması beklenirken kullanmak istersiniz.  Görevler oluşturulabildikleri için ve <xref:System.Threading.Tasks.Task> sınıfı <xref:System.IAsyncResult> arabirimini uyguladığı için, bunu yapmak amacıyla daha basit bir yardımcı işlev kullanabilirsiniz. Aşağıdaki kod uzantısı kullanır <xref:System.Threading.Tasks.Task%601> sınıfı, ancak kullanabileceğiniz neredeyse aynı işlevi için genel olmayan görevleri.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Şimdi, aşağıdaki DOKUNUN uygulamaya sahip olduğu bir durum düşünün:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 ve bu APM uygulamasını sağlamak istiyorsanız:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 Aşağıdaki örnek, bir geçiş APM gösterir:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Görevleri ve olay tabanlı zaman uyumsuz desen (EAP)  
 Kaydırma bir [olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) uygulamasıdır bir APM desen kaydırma değerinden daha karmaşık olduğu EAP düzeni daha fazla değişim ve APM düzeni daha az yapısı.  Göstermek için aşağıdaki kodu sarmalar `DownloadStringAsync` yöntemi.  `DownloadStringAsync`bir URI kabul eder, başlatır `DownloadProgressChanged` ilerleme ve başlatır birden çok istatistikleri rapor için indirilirken olay `DownloadStringCompleted` doldurduktan olay.  Nihai sonucu belirtilen URI sayfanın içeriğini içeren bir dizedir.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a>Görevleri ve bekleme tanıtıcıları  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a>Bekleme işleyicilerine DOKUNUN  
 Bekleme tanıtıcıları bir zaman uyumsuz desen uygulamayan rağmen Gelişmiş geliştiriciler kullanabilir <xref:System.Threading.WaitHandle> sınıfı ve <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> bekleme tanıtıcısı ayarlandığında zaman uyumsuz bildirimleri için yöntem.  Kayabilir <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> yöntemi zaman uyumlu herhangi bir bekleme tanıtıcısı bekleme görev tabanlı bir alternatifi etkinleştirmek için:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Bu yöntemle varolan kullanabileceğiniz <xref:System.Threading.WaitHandle> zaman uyumsuz yöntemleri uygulamalarında.  Örneğin, belirli bir zamanda yürütme zaman uyumsuz işlemleri sayısını azaltma istiyorsanız, bir semafor kullanabilirler (bir <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> nesnesi).  İçin daraltabilir *N* eşzamanlı olarak çalışan işlem sayısı için semafor 's sayısı başlatma tarafından *N*semafor üzerinde bir işlemi gerçekleştirmek için istediğiniz zaman bekleyen ve serbest bırakma bir işlem bittiğinde semafor:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Bekleme tanıtıcıları bağlı değildir ve bunun yerine görevlerle tam çalışır bir zaman uyumsuz semafor de oluşturabilirsiniz. Bunu yapmak için bu bölümünde açıklandığı gibi teknikler kullanabilirsiniz [görev tabanlı zaman uyumsuz desen kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) üstünde veri yapılarını oluşturmak için <xref:System.Threading.Tasks.Task>.  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a>Bekleme tanıtıcıları için DOKUNUN  
 Daha önce belirtildiği gibi <xref:System.Threading.Tasks.Task> sınıfını uygular <xref:System.IAsyncResult>, ve o uygulama sunan bir <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> ne zaman ayarlanacak bir bekleme tanıtıcısı döndüren özelliği <xref:System.Threading.Tasks.Task> tamamlar.  Alabileceğiniz bir <xref:System.Threading.WaitHandle> için bir <xref:System.Threading.Tasks.Task> gibi:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [Görev Tabanlı Zaman Uyumsuz Desen Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
