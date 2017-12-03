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
ms.openlocfilehash: 539a926e5f378f77553b308245acbf33ebb325d7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transfer"></a><span data-ttu-id="f3bf3-102">Aktarma</span><span class="sxs-lookup"><span data-stu-id="f3bf3-102">Transfer</span></span>
<span data-ttu-id="f3bf3-103">Bu konu, aktarımı açıklar [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Etkinlik izleme modeli.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-103">This topic describes transfer in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="f3bf3-104">Aktarım tanımı</span><span class="sxs-lookup"><span data-stu-id="f3bf3-104">Transfer Definition</span></span>  
 <span data-ttu-id="f3bf3-105">Etkinlikler arasında aktarımları uç noktaları içindeki ilgili etkinlikleri olaylar arasında nedensel ilişkileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="f3bf3-106">Denetim bu etkinlikler arasında Örneğin, etkinlik sınırları geçmeden bir yöntem çağrısı akar olduğunda iki etkinlik aktarımları ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="f3bf3-107">İçinde [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], bayt hizmeti üzerinde dinleme etkinlik ileti nesnesi oluşturulduğu için bayt alma etkinlik aktarılır gelen olduğunda.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-107">In [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="f3bf3-108">Uçtan uca izleme senaryoları ve bunların ilgili etkinliği ve tasarım izleme listesi için bkz: [uçtan uca izleme senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="f3bf3-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="f3bf3-109">Aktarım izlemeleri yaymak üzere kullanmak `ActivityTracing` izleme kaynağında aşağıdaki yapılandırma kodda gösterildiği şekilde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="f3bf3-110">Uç noktaları'nda etkinlikler ilişkilendirmek için aktarımı kullanma</span><span class="sxs-lookup"><span data-stu-id="f3bf3-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="f3bf3-111">Etkinlikler ve aktarımları probabilistically bir hatasının kök nedenini bulmak için kullanıcıya izin verir.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="f3bf3-112">Örneğin, biz geri ve İleri etkinlikler arasında M ve N sırasıyla M ve bileşenleri N aktarmak ve bir kilitlenme N sağ aktarımı M sonra gerçekleşir. Biz N'ın veri geri M geçirilmesini nedeni büyük olasılıkla sonuç çizim yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="f3bf3-113">M ve n arasında denetim akışı olduğunda bir aktarım izleme etkinliği N M etkinliğinden yayılan Örneğin, N etkinlikleri sınırları geçmeden bir yöntem çağrısı nedeniyle M için bazı çalışma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="f3bf3-114">N zaten var olabilir veya oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-114">N may already exist or has been created.</span></span> <span data-ttu-id="f3bf3-115">N, M N, M için bazı çalışma gerçekleştirir yeni bir etkinlik olduğunda tarafından oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="f3bf3-116">N M bir aktarımı tarafından aktarımı geri N M için takip edilebilir değil. M N bazı iş oluşturabilir ve N o iş tamamlandığında izlemez olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="f3bf3-117">Aslında, N, görev tamamlanmadan önce M sonlandırabilir.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="f3bf3-118">Dinleyici etkinlikleri (N) olarak çoğaltılır ve ardından sonlandırır "Açık ServiceHost" etkinliğinde (M) olur.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="f3bf3-119">Bir aktarımı geri N-M N, M için ilgili iş tamamlandı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="f3bf3-120">N, M, örneğin, oturum açma isteklerinin (M) farklı bir oturum açma etkinliklerden alan tutar varolan kimlik doğrulayıcı aktivite (N) ilişkisiz başka bir işlem gerçekleştirmeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="f3bf3-121">İç içe geçmiş ilişkisi etkinlikler arasında M ve n mevcut değil Bu iki nedenden kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="f3bf3-122">Etkinlik M değil izlediğinizde M başlatılan rağmen ilk olarak, gerçek işleme N içinde gerçekleştirilen n İkincisi, ne zaman N zaten mevcut.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="f3bf3-123">Aktarımları örneği</span><span class="sxs-lookup"><span data-stu-id="f3bf3-123">Example of Transfers</span></span>  
 <span data-ttu-id="f3bf3-124">Aşağıdaki listeler iki aktarımı örnekler.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-124">The following lists two transfer examples.</span></span>  
  
-   <span data-ttu-id="f3bf3-125">Hizmet ana bilgisayarını oluşturduğunuzda, çağrıyı yapan kod denetiminden Oluşturucusu kazanır veya arama kod oluşturucuya aktarır.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="f3bf3-126">Oluşturucusu yürütme tamamlandığında, çağrıyı yapan kod denetimi döndürür veya çağıran kodu Oluşturucu aktarır.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="f3bf3-127">İç içe geçmiş ilişkinin bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-127">This is the case of a nested relationship.</span></span>  
  
-   <span data-ttu-id="f3bf3-128">Dinleyici aktarım veri işlemeye başladığında, yeni bir iş parçacığı oluşturur ve işleme, Denetim ve veri geçirme için uygun içerik için bayt alma etkinlik aktarır.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="f3bf3-129">Bu iş parçacığı isteği işlemeyi tamamladığında, bayt alma etkinlik hiçbir şey geri dinleyiciye geçirir.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="f3bf3-130">Bu durumda, bir aktarımı ancak yeni iş parçacığı etkinliği dışında herhangi bir aktarım sahip.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="f3bf3-131">İki etkinlik ilgili ancak iç içe değil.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="f3bf3-132">Etkinlik aktarım sırası</span><span class="sxs-lookup"><span data-stu-id="f3bf3-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="f3bf3-133">Doğru biçimlendirilmiş etkinlik aktarım dizisi aşağıdaki adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1.  <span data-ttu-id="f3bf3-134">Yeni bir gAId seçerek oluşan yeni bir etkinlik başlayın.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2.  <span data-ttu-id="f3bf3-135">Aktarım izleme bu yeni gAId geçerli etkinlik kimliği yayma</span><span class="sxs-lookup"><span data-stu-id="f3bf3-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3.  <span data-ttu-id="f3bf3-136">TLS yeni kimlik</span><span class="sxs-lookup"><span data-stu-id="f3bf3-136">Set the new ID in TLS</span></span>  
  
4.  <span data-ttu-id="f3bf3-137">Yeni etkinlik tarafından başlangıcını belirtmek için bir başlangıç izlemesi yayma.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5.  <span data-ttu-id="f3bf3-138">Özgün etkinlik dönün aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="f3bf3-138">Return to the original activity consists of the following:</span></span>  
  
6.  <span data-ttu-id="f3bf3-139">Özgün gAId bir aktarım izleme yayma</span><span class="sxs-lookup"><span data-stu-id="f3bf3-139">Emit a transfer trace to the original gAId</span></span>  
  
7.  <span data-ttu-id="f3bf3-140">Yeni Etkinlik sonunu göstermek için İzlemeyi Durdur yayma</span><span class="sxs-lookup"><span data-stu-id="f3bf3-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8.  <span data-ttu-id="f3bf3-141">TLS eski gAId ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="f3bf3-142">Aşağıdaki kod örneğinde bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="f3bf3-143">Bu örnek, bir engelleme çağrı yeni etkinlik aktarırken yaptığınız ve askıya Sürdür izlemeleri içerir varsayar.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3bf3-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3bf3-144">See Also</span></span>  
 [<span data-ttu-id="f3bf3-145">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f3bf3-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="f3bf3-146">İzlemeleri görüntüleme bağıntılı için hizmet izleme görüntüleyicisini kullanma ve sorun giderme</span><span class="sxs-lookup"><span data-stu-id="f3bf3-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="f3bf3-147">Uçtan uca izleme senaryoları</span><span class="sxs-lookup"><span data-stu-id="f3bf3-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="f3bf3-148">Hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="f3bf3-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
