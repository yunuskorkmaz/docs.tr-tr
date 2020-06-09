---
title: Aktarma
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 52b0cf35a2f8bab17252d3711f3143738c2bc39c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587775"
---
# <a name="transfer"></a><span data-ttu-id="da3fd-102">Aktarma</span><span class="sxs-lookup"><span data-stu-id="da3fd-102">Transfer</span></span>
<span data-ttu-id="da3fd-103">Bu konu, Windows Communication Foundation (WCF) etkinliği izleme modelinde aktarımı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="da3fd-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="da3fd-104">Aktarım tanımı</span><span class="sxs-lookup"><span data-stu-id="da3fd-104">Transfer Definition</span></span>  
 <span data-ttu-id="da3fd-105">Etkinlikler arasındaki aktarımlar, uç noktalar içindeki ilgili etkinliklerdeki olaylar arasındaki causal ilişkilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="da3fd-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="da3fd-106">İki etkinlik, bu etkinlikler arasındaki denetim akışı, örneğin etkinlik sınırlarını geçen bir yöntem çağrısı gibi aktarımlarla ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="da3fd-107">WCF 'de, baytların hizmette geliş durumunda dinleme etkinliği ileti nesnesinin oluşturulduğu bayt alma etkinliğine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="da3fd-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="da3fd-108">Uçtan uca izleme senaryolarına ve bunların ilgili etkinliklerini ve izleme tasarımına yönelik bir liste için bkz. [uçtan uca Izleme senaryoları](end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="da3fd-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="da3fd-109">Aktarım izlemelerini yaymak için, `ActivityTracing` izleme kaynağı üzerindeki ayarı aşağıdaki yapılandırma kodu ile gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="da3fd-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="da3fd-110">Uç noktalar Içindeki etkinlikleri Ilişkilendirmek için aktarımı kullanma</span><span class="sxs-lookup"><span data-stu-id="da3fd-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="da3fd-111">Etkinlikler ve aktarımlar, kullanıcının bir hatanın kök nedenini bilsel bulmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="da3fd-112">Örneğin, a ve N bileşenlerinde sırasıyla a ve N etkinlikleri arasında geri ve ileri aktarıldığımızda ve bir kilitlenme, d 'ye geri aktarıldıktan sonra n doğru olursa, büyük olasılıkla N 'nin verileri d 'ye geri geçirmesinin nedeni çizebiliriz.</span><span class="sxs-lookup"><span data-stu-id="da3fd-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="da3fd-113">A ve N arasında bir denetim akışı olduğunda, bir aktarım izlemesi etkinlik d 'den etkinlik N 'ye yayılır. Örneğin, N, etkinliğin sınırlarını geçen bir yöntem çağrısı nedeniyle h için biraz iş gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="da3fd-114">N zaten var veya oluşturulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-114">N may already exist or has been created.</span></span> <span data-ttu-id="da3fd-115">N, k için bazı işler gerçekleştiren yeni bir etkinlikse, n tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="da3fd-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="da3fd-116">A 'dan N 'ye bir aktarım, N 'den d 'ye geri aktarım ile izlenebilir. Bunun nedeni, N 'nin bazı işleri N 'de üretme ve işi ne zaman tamamladığını izlememe nedeni.</span><span class="sxs-lookup"><span data-stu-id="da3fd-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="da3fd-117">Aslında, h işini tamamlanmadan önce son verebilir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="da3fd-118">Bu durum, NS dinleyicisi etkinliklerini (N) ve ardından sonlandırmakta olan "açık ServiceHost" etkinliğinde (e) oluşur.</span><span class="sxs-lookup"><span data-stu-id="da3fd-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="da3fd-119">N 'den d 'ye geri aktarma işlemi, N ile ilgili çalışmanın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="da3fd-120">N, farklı oturum açma etkinliklerinden oturum açma istekleri (M) almaya devam eden, mevcut bir kimlik doğrulayıcı etkinliği (N) ile ilişkili diğer işlemleri gerçekleştirmeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="da3fd-121">İç içe geçmiş ilişki, a ve N etkinlikleri arasında olmamalıdır. Bu, iki nedenden dolayı oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="da3fd-122">İlk olarak, etkinlik M, M tarafından başlatılan N ' de gerçekleştirilen gerçek işlemeyi izlemez. İkinci olarak, N zaten var.</span><span class="sxs-lookup"><span data-stu-id="da3fd-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="da3fd-123">Aktarım örnekleri</span><span class="sxs-lookup"><span data-stu-id="da3fd-123">Example of Transfers</span></span>  
 <span data-ttu-id="da3fd-124">Aşağıda iki aktarım örneği listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="da3fd-125">Bir hizmet ana bilgisayarı oluşturduğunuzda, Oluşturucu çağıran koddan denetimi kazanır veya çağıran kod oluşturucuya aktarır.</span><span class="sxs-lookup"><span data-stu-id="da3fd-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="da3fd-126">Oluşturucunun yürütülmesi bittiğinde, çağıran koda denetim döndürür veya Oluşturucu çağıran koda geri aktarır.</span><span class="sxs-lookup"><span data-stu-id="da3fd-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="da3fd-127">Bu, iç içe geçmiş bir ilişki durumunda olur.</span><span class="sxs-lookup"><span data-stu-id="da3fd-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="da3fd-128">Bir dinleyici aktarım verilerini işlemeye başladığında, yeni bir iş parçacığı oluşturur ve alma bayt etkinliğine yönelik uygun bağlam işleme, denetim ve verileri geçirme</span><span class="sxs-lookup"><span data-stu-id="da3fd-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="da3fd-129">Bu iş parçacığı isteği işlemeyi tamamladığında, alma baytları etkinliği dinleyiciye hiçbir şey geri geçirir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="da3fd-130">Bu durumda, ' de bir aktarım yaptık, ancak yeni iş parçacığı etkinliğinden aktarım yok.</span><span class="sxs-lookup"><span data-stu-id="da3fd-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="da3fd-131">İki etkinlik ilişkili ancak iç içe değil.</span><span class="sxs-lookup"><span data-stu-id="da3fd-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="da3fd-132">Etkinlik aktarma sırası</span><span class="sxs-lookup"><span data-stu-id="da3fd-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="da3fd-133">İyi biçimlendirilmiş bir etkinlik aktarma sırası aşağıdaki adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="da3fd-134">Yeni bir gAId seçip seçmekten oluşan yeni bir etkinlik başlatın.</span><span class="sxs-lookup"><span data-stu-id="da3fd-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="da3fd-135">Geçerli etkinlik KIMLIĞINDEN bu yeni bir gAId 'ye bir aktarım izlemesi yay</span><span class="sxs-lookup"><span data-stu-id="da3fd-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="da3fd-136">Yeni KIMLIĞI TLS 'de ayarlama</span><span class="sxs-lookup"><span data-stu-id="da3fd-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="da3fd-137">Yeni etkinliğin başlangıcını tarafından göstermek için bir başlangıç izlemeyi yay.</span><span class="sxs-lookup"><span data-stu-id="da3fd-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="da3fd-138">Özgün etkinliğe geri dönme aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="da3fd-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="da3fd-139">Bir aktarım izlemesini özgün gAId 'ye yay</span><span class="sxs-lookup"><span data-stu-id="da3fd-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="da3fd-140">Yeni etkinliğin sonunu belirtmek için bir durdurma izi yay</span><span class="sxs-lookup"><span data-stu-id="da3fd-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="da3fd-141">TLS 'yi eski gAId olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="da3fd-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="da3fd-142">Aşağıdaki kod örneği bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="da3fd-143">Bu örnek, yeni etkinliğe aktarılırken bir engelleme çağrısının yapıldığını varsayar ve askıya alma/sürdürülme izlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="da3fd-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da3fd-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da3fd-144">See also</span></span>

- [<span data-ttu-id="da3fd-145">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="da3fd-145">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="da3fd-146">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma </span><span class="sxs-lookup"><span data-stu-id="da3fd-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="da3fd-147">Uçtan Uca İzleme Senaryoları</span><span class="sxs-lookup"><span data-stu-id="da3fd-147">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="da3fd-148">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="da3fd-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
