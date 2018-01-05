---
title: Aktarma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83bb76cc46d72f3d368de20669391c3e7f24a0f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="transfer"></a>Aktarma
Bu konu, aktarımı açıklar [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Etkinlik izleme modeli.  
  
## <a name="transfer-definition"></a>Aktarım tanımı  
 Etkinlikler arasında aktarımları uç noktaları içindeki ilgili etkinlikleri olaylar arasında nedensel ilişkileri temsil eder. Denetim bu etkinlikler arasında Örneğin, etkinlik sınırları geçmeden bir yöntem çağrısı akar olduğunda iki etkinlik aktarımları ile ilişkilidir. İçinde [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], bayt hizmeti üzerinde dinleme etkinlik ileti nesnesi oluşturulduğu için bayt alma etkinlik aktarılır gelen olduğunda. Uçtan uca izleme senaryoları ve bunların ilgili etkinliği ve tasarım izleme listesi için bkz: [uçtan uca izleme senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
 Aktarım izlemeleri yaymak üzere kullanmak `ActivityTracing` izleme kaynağında aşağıdaki yapılandırma kodda gösterildiği şekilde ayarlama.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Uç noktaları'nda etkinlikler ilişkilendirmek için aktarımı kullanma  
 Etkinlikler ve aktarımları probabilistically bir hatasının kök nedenini bulmak için kullanıcıya izin verir. Örneğin, biz geri ve İleri etkinlikler arasında M ve N sırasıyla M ve bileşenleri N aktarmak ve bir kilitlenme N sağ aktarımı M sonra gerçekleşir. Biz N'ın veri geri M geçirilmesini nedeni büyük olasılıkla sonuç çizim yapabilirsiniz.  
  
 M ve n arasında denetim akışı olduğunda bir aktarım izleme etkinliği N M etkinliğinden yayılan Örneğin, N etkinlikleri sınırları geçmeden bir yöntem çağrısı nedeniyle M için bazı çalışma gerçekleştirir. N zaten var olabilir veya oluşturuldu. N, M N, M için bazı çalışma gerçekleştirir yeni bir etkinlik olduğunda tarafından oluşturdu.  
  
 N M bir aktarımı tarafından aktarımı geri N M için takip edilebilir değil. M N bazı iş oluşturabilir ve N o iş tamamlandığında izlemez olmasıdır. Aslında, N, görev tamamlanmadan önce M sonlandırabilir. Dinleyici etkinlikleri (N) olarak çoğaltılır ve ardından sonlandırır "Açık ServiceHost" etkinliğinde (M) olur. Bir aktarımı geri N-M N, M için ilgili iş tamamlandı anlamına gelir.  
  
 N, M, örneğin, oturum açma isteklerinin (M) farklı bir oturum açma etkinliklerden alan tutar varolan kimlik doğrulayıcı aktivite (N) ilişkisiz başka bir işlem gerçekleştirmeye devam edebilirsiniz.  
  
 İç içe geçmiş ilişkisi etkinlikler arasında M ve n mevcut değil Bu iki nedenden kaynaklanabilir. Etkinlik M değil izlediğinizde M başlatılan rağmen ilk olarak, gerçek işleme N içinde gerçekleştirilen n İkincisi, ne zaman N zaten mevcut.  
  
## <a name="example-of-transfers"></a>Aktarımları örneği  
 Aşağıdaki listeler iki aktarımı örnekler.  
  
-   Hizmet ana bilgisayarını oluşturduğunuzda, çağrıyı yapan kod denetiminden Oluşturucusu kazanır veya arama kod oluşturucuya aktarır. Oluşturucusu yürütme tamamlandığında, çağrıyı yapan kod denetimi döndürür veya çağıran kodu Oluşturucu aktarır. İç içe geçmiş ilişkinin bir durumdur.  
  
-   Dinleyici aktarım veri işlemeye başladığında, yeni bir iş parçacığı oluşturur ve işleme, Denetim ve veri geçirme için uygun içerik için bayt alma etkinlik aktarır. Bu iş parçacığı isteği işlemeyi tamamladığında, bayt alma etkinlik hiçbir şey geri dinleyiciye geçirir. Bu durumda, bir aktarımı ancak yeni iş parçacığı etkinliği dışında herhangi bir aktarım sahip. İki etkinlik ilgili ancak iç içe değil.  
  
## <a name="activity-transfer-sequence"></a>Etkinlik aktarım sırası  
 Doğru biçimlendirilmiş etkinlik aktarım dizisi aşağıdaki adımları içerir.  
  
1.  Yeni bir gAId seçerek oluşan yeni bir etkinlik başlayın.  
  
2.  Aktarım izleme bu yeni gAId geçerli etkinlik kimliği yayma  
  
3.  TLS yeni kimlik  
  
4.  Yeni etkinlik tarafından başlangıcını belirtmek için bir başlangıç izlemesi yayma.  
  
5.  Özgün etkinlik dönün aşağıdakilerden oluşur:  
  
6.  Özgün gAId bir aktarım izleme yayma  
  
7.  Yeni Etkinlik sonunu göstermek için İzlemeyi Durdur yayma  
  
8.  TLS eski gAId ayarlayın.  
  
 Aşağıdaki kod örneğinde bunun nasıl yapılacağı gösterilmektedir. Bu örnek, bir engelleme çağrı yeni etkinlik aktarırken yaptığınız ve askıya Sürdür izlemeleri içerir varsayar.  
  
```  
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  
// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();   
// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  
// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  
// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  
// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  
// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  
// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);   
// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  
// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  
// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;    
// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlemeyi Yapılandırma](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Uçtan Uca İzleme Senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
