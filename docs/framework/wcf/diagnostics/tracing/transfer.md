---
title: Aktarma
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 4753ec85c458a0dde3db4a6b7cdad41c69185019
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311025"
---
# <a name="transfer"></a><span data-ttu-id="15397-102">Aktarma</span><span class="sxs-lookup"><span data-stu-id="15397-102">Transfer</span></span>
<span data-ttu-id="15397-103">Bu konu, Windows Communication Foundation (WCF) Etkinlik izleme modelinde aktarımı açıklar.</span><span class="sxs-lookup"><span data-stu-id="15397-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="15397-104">Aktarım tanımı</span><span class="sxs-lookup"><span data-stu-id="15397-104">Transfer Definition</span></span>  
 <span data-ttu-id="15397-105">Etkinlikler arasında aktarımları uç noktaları içindeki ilgili etkinlikleri olaylar arasında nedensel ilişkileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="15397-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="15397-106">Denetim etkinliği sınırlarını geçmesini bir yöntem çağrısının bu etkinlikler arasında Örneğin, akışlarınız çalıştığında iki etkinliği aktarımları ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="15397-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="15397-107">Bayt hizmette gelen olduğunda WCF'de, dinleme, etkinlik ileti nesnesi oluşturulduğu için bayt alma etkinlik aktarılır.</span><span class="sxs-lookup"><span data-stu-id="15397-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="15397-108">Uçtan uca izleme senaryoları ve ilgili etkinlikler ve tasarım izleme listesi için bkz. [uçtan uca izleme senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="15397-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="15397-109">Aktarım izlemeleri yayma kullanın `ActivityTracing` yapılandırma aşağıdaki kodda gösterildiği gibi izleme kaynak ayarlama.</span><span class="sxs-lookup"><span data-stu-id="15397-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="15397-110">Uç noktaları içindeki etkinliklerini ilişkilendirmek için Aktarım kullanma</span><span class="sxs-lookup"><span data-stu-id="15397-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="15397-111">Etkinlikleri ve aktarımları probabilistically hata nedenini bulmak için kullanıcıya izin verir.</span><span class="sxs-lookup"><span data-stu-id="15397-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="15397-112">Örneğin, biz etkinlikler arasında M ve N sırasıyla M ve bileşenleri N İleri ve geri aktarmak ve aktarımı M sonra N hemen bir kilitlenme olur, biz Bunun nedeni büyük olasılıkla n'nin-m arası veri geçirme sonuç çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15397-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="15397-113">Bir denetim n ile M arasındaki akışını olduğunda bir aktarım izleme etkinliğini N M etkinliğinden yayıldığını Örneğin, bazı çalışma N etkinliklerin sınırlarını geçmesini bir yöntem çağrısının nedeniyle milyon gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="15397-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="15397-114">N zaten var olabilir veya oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="15397-114">N may already exist or has been created.</span></span> <span data-ttu-id="15397-115">N, M, N, M için bazı işlemler gerçekleştiren yeni bir etkinlik olduğunda tarafından üretilmedi.</span><span class="sxs-lookup"><span data-stu-id="15397-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="15397-116">Bir milyon aktarımı n aktarımı tarafından geri N için M ardından değil. M, n bazı işler oluşturabilir ve N o iş tamamlandığında izlemez olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="15397-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="15397-117">Aslında, N, görev tamamlanmadan önce M sonlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15397-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="15397-118">Bu, dinleyici etkinlikleri (N) olarak çoğaltılır ve sonra sona erer "Açık ServiceHost" etkinlik (M) gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="15397-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="15397-119">Bir aktarımı geri N-M, N, M için ilgili iş tamamlandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="15397-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="15397-120">N, m, örneğin, oturum açma isteklerinin (M) farklı bir oturum açma etkinliklerini alan tutar mevcut authenticator etkinlik (N) ilgisi olmayan başka bir işlem gerçekleştirmeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="15397-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="15397-121">İç içe geçme ilişkisini etkinlikler arasında M ve N. mevcut değil Bu, iki nedenden kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="15397-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="15397-122">Etkinlik M değil izlerken M başlatıldı ancak ilk olarak, gerçek işleme N gerçekleştirilen n Saniye, ne zaman N'ı zaten mevcut.</span><span class="sxs-lookup"><span data-stu-id="15397-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="15397-123">Aktarımları örneği</span><span class="sxs-lookup"><span data-stu-id="15397-123">Example of Transfers</span></span>  
 <span data-ttu-id="15397-124">Aşağıdaki liste iki aktarımı örnekler.</span><span class="sxs-lookup"><span data-stu-id="15397-124">The following lists two transfer examples.</span></span>  
  
-   <span data-ttu-id="15397-125">Bir hizmet konağı oluşturduğunuzda, çağıran kod denetiminden Oluşturucu kazanır veya çağıran kod oluşturucuya aktarır.</span><span class="sxs-lookup"><span data-stu-id="15397-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="15397-126">Oluşturucu yürütme sona erdiğinde, çağrıldığı koda denetimini döndürür veya Oluşturucu çağıran koda geri aktarır.</span><span class="sxs-lookup"><span data-stu-id="15397-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="15397-127">İç içe geçmiş bir ilişkinin durum budur.</span><span class="sxs-lookup"><span data-stu-id="15397-127">This is the case of a nested relationship.</span></span>  
  
-   <span data-ttu-id="15397-128">Dinleyici aktarım veri işlemeye başladığında, yeni bir iş parçacığı oluşturur ve işleme, Denetim ve veri geçirme için uygun içerik için bayt alma etkinlik uygulamalı.</span><span class="sxs-lookup"><span data-stu-id="15397-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="15397-129">İş parçacığı istek işlemeyi tamamlandığında, bayt Al etkinliği hiçbir şey dinleyici için geçirir.</span><span class="sxs-lookup"><span data-stu-id="15397-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="15397-130">Bu durumda, bir aktarımı ancak yeni iş parçacığı etkinliği dışında hiçbir aktarım sahibiz.</span><span class="sxs-lookup"><span data-stu-id="15397-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="15397-131">İki etkinliği ilgili ancak iç içe yerleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="15397-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="15397-132">Etkinlik aktarım dizisi</span><span class="sxs-lookup"><span data-stu-id="15397-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="15397-133">İyi biçimlendirilmiş bir etkinlik aktarım dizisi, aşağıdaki adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="15397-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="15397-134">Yeni bir gAId seçerek oluşan yeni bir etkinlik başlar.</span><span class="sxs-lookup"><span data-stu-id="15397-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="15397-135">Aktarım izleme için bu yeni gAId geçerli etkinlik kimliği yayma</span><span class="sxs-lookup"><span data-stu-id="15397-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="15397-136">TLS yeni kimlik</span><span class="sxs-lookup"><span data-stu-id="15397-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="15397-137">Yeni etkinlik tarafından belirtmek için bir başlangıç izleme gösterin.</span><span class="sxs-lookup"><span data-stu-id="15397-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="15397-138">Özgün etkinlik dön aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="15397-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="15397-139">Özgün gAId bir aktarım izleme yayma</span><span class="sxs-lookup"><span data-stu-id="15397-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="15397-140">Yeni Etkinlik sonunu belirtmek için İzlemeyi Durdur yayma</span><span class="sxs-lookup"><span data-stu-id="15397-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="15397-141">TLS için eski gAId ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="15397-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="15397-142">Aşağıdaki kod örneği, bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="15397-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="15397-143">Bu örnek, bir engelleme çağrısının yeni etkinliği aktarırken yapılır ve askıya alma/sürdürme izlemeleri içerir varsayar.</span><span class="sxs-lookup"><span data-stu-id="15397-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="15397-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15397-144">See also</span></span>

- [<span data-ttu-id="15397-145">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="15397-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="15397-146">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="15397-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="15397-147">Uçtan Uca İzleme Senaryoları</span><span class="sxs-lookup"><span data-stu-id="15397-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="15397-148">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="15397-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
