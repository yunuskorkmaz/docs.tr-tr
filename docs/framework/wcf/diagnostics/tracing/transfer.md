---
title: Aktarma
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: e0ebfff97cd33e7a588a1ab92399a97a0fbec039
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185699"
---
# <a name="transfer"></a><span data-ttu-id="bd3fe-102">Aktarma</span><span class="sxs-lookup"><span data-stu-id="bd3fe-102">Transfer</span></span>
<span data-ttu-id="bd3fe-103">Bu konu, Windows Communication Foundation (WCF) etkinlik izleme modelinde aktarım açıklar.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="bd3fe-104">Aktarım Tanımı</span><span class="sxs-lookup"><span data-stu-id="bd3fe-104">Transfer Definition</span></span>  
 <span data-ttu-id="bd3fe-105">Etkinlikler arasındaki aktarımlar, uç noktalardaki ilgili etkinliklerdeki olaylar arasındaki nedensel ilişkileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="bd3fe-106">İki etkinlik, bu etkinlikler arasında denetim akışı olduğunda aktarımlarla ilişkilidir, örneğin, bir yöntem geçiş etkinlik sınırları çağırır.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="bd3fe-107">WCF'de, hizmete baytlar geldiğinde, At'ı Dinle etkinliği ileti nesnesinin oluşturulduğu Bayt Al etkinliğine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="bd3fe-108">Uçtan uca izleme senaryolarının ve bunların ilgili etkinlik ve izleme tasarımlarının listesi için [bkz.](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="bd3fe-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="bd3fe-109">Aktarım izlemelerini yalamak için, aşağıdaki yapılandırma kodunda gösterildiği gibi izleme kaynağındaki `ActivityTracing` ayarı kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="bd3fe-110">Son Noktalardaki Etkinlikleri Ilişkilendirmek için Aktarım Kullanma</span><span class="sxs-lookup"><span data-stu-id="bd3fe-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="bd3fe-111">Etkinlikler ve aktarımlar, kullanıcının bir hatanın temel nedenini probabilistically olarak bulmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="bd3fe-112">Örneğin, M ve N bileşenlerindeki m ve n etkinlikleri arasında ileri geri aktarırsak ve M'e aktarıldıktan hemen sonra N'de bir çökme meydana gelirse, bunun N'nin verileri M'e aktarması ndan kaynaklandığı sonucuna varabiliriz.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="bd3fe-113">M ve N arasında bir kontrol akışı olduğunda, bir aktarım izi M aktivitesinden N aktivitesine yayılır. Örneğin, N, etkinliklerin sınırlarını aşma yı çağırma yöntemi nedeniyle M için bazı işler gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="bd3fe-114">N zaten var olabilir veya oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-114">N may already exist or has been created.</span></span> <span data-ttu-id="bd3fe-115">N, M için bazı işler gerçekleştiren yeni bir etkinlik olduğunda N, M tarafından ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="bd3fe-116">M'den N'ye geçiş, N'den M'ye geri aktarılmasıyla takip edilemez. Bunun nedeni, M'nin N'de bazı işler ortaya çıkarabiliyor ve N bu çalışmayı tamamladığında izlenmiyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="bd3fe-117">Aslında, M, N görevini tamamlamadan önce sonlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="bd3fe-118">Bu, Dinleyici etkinliklerini (N) oluşturan ve sonra sona erdiren "Open ServiceHost" etkinliğinde (M) gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="bd3fe-119">N'den M'ye geçiş, N'nin M ile ilgili çalışmayı tamamladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="bd3fe-120">N, m ile ilgisi olmayan diğer işlemleri gerçekleştirmeye devam edebilir, örneğin, farklı oturum açma etkinliklerinden oturum açma istekleri (M) almaya devam eden varolan bir kimlik doğrulayıcı etkinliği (N).</span><span class="sxs-lookup"><span data-stu-id="bd3fe-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="bd3fe-121">M ve N etkinlikleri arasında iç içe geçme ilişkisi olmak zorunda değildir. Bu iki nedenden dolayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="bd3fe-122">İlk olarak, M etkinliği N'de gerçekleştirilen gerçek işlemeyi izlemediğinde, M'yi başlatan N.'ye rağmen. İkincisi, N zaten var olduğunda.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="bd3fe-123">Aktarım Örneği</span><span class="sxs-lookup"><span data-stu-id="bd3fe-123">Example of Transfers</span></span>  
 <span data-ttu-id="bd3fe-124">Aşağıda iki aktarım örneği listelenin.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="bd3fe-125">Bir hizmet ana bilgisayarı oluşturduğunuzda, oluşturucu çağrı kodundan denetim kazanır veya çağrı kodu oluşturucuya aktarır.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="bd3fe-126">Oluşturucu yürütmeyi tamamladığında, denetimi arama koduna döndürür veya oluşturucu arama koduna geri aktarır.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="bd3fe-127">Bu iç içe bir ilişki durumudur.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="bd3fe-128">Bir dinleyici aktarım verilerini işlemeye başladığında, yeni bir iş parçacığı oluşturur ve Yeni Bir Elek oluşturma Bytes etkinliği işleme, denetim ve veri aktarmak için uygun bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="bd3fe-129">Bu iş parçacığı isteği işleme yi bitirdiğinde, Bayt Al etkinliği dinleyiciye hiçbir şey geri aktaramaz.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="bd3fe-130">Bu durumda, yeni iş parçacığı etkinliğinden bir aktarım var, ancak aktarım yok.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="bd3fe-131">İki etkinlik ilişkilidir, ancak iç içe geçmez.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="bd3fe-132">Etkinlik Aktarım Sırası</span><span class="sxs-lookup"><span data-stu-id="bd3fe-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="bd3fe-133">İyi biçimlendirilmiş bir etkinlik aktarım sırası aşağıdaki adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="bd3fe-134">Yeni bir gAId seçmekte oluşan yeni bir etkinlik başlatın.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="bd3fe-135">Geçerli etkinlik kimliğinden bu yeni gAId'ye aktarım izi yayı</span><span class="sxs-lookup"><span data-stu-id="bd3fe-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="bd3fe-136">TLS'de yeni kimliği ayarlama</span><span class="sxs-lookup"><span data-stu-id="bd3fe-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="bd3fe-137">Yeni etkinliğin başlangıcını göstermek için bir başlangıç izi yayan.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="bd3fe-138">Özgün faaliyete dönüş aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="bd3fe-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="bd3fe-139">Orijinal gAId bir transfer izi yayan</span><span class="sxs-lookup"><span data-stu-id="bd3fe-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="bd3fe-140">Yeni etkinliğin sonunu belirtmek için bir Dur izi yontun</span><span class="sxs-lookup"><span data-stu-id="bd3fe-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="bd3fe-141">TLS'yi eski gAId'e ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="bd3fe-142">Aşağıdaki kod örneği, bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="bd3fe-143">Bu örnek, yeni faaliyete aktarılırken engelleme çağrısı yapıldığını varsayar ve askıya alma/devam izlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bd3fe-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd3fe-144">See also</span></span>

- [<span data-ttu-id="bd3fe-145">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bd3fe-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="bd3fe-146">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma </span><span class="sxs-lookup"><span data-stu-id="bd3fe-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="bd3fe-147">Uçtan Uca İzleme Senaryoları</span><span class="sxs-lookup"><span data-stu-id="bd3fe-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="bd3fe-148">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="bd3fe-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
