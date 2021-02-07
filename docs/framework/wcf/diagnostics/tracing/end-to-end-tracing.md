---
description: 'Daha fazla bilgi edinin: uçtan uca Izleme'
title: Uçtan Uca İzleme
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: c1c4a38d4ef8c445994d42abeafbb25da9a5f326
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759438"
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="483ae-103">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="483ae-103">End-to-End Tracing</span></span>

<span data-ttu-id="483ae-104">Uçtan uca (e2e) Izleme, geliştiricilerin bir kod yolunun neden başarısız olduğunu araştırmak veya kapasite planlama ve performans analizi için ayrıntılı izleme sağlamak üzere Windows Communication Foundation (WCF) altyapısındaki kodun yürütülmesini izlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="483ae-104">End to End (e2e) Tracing allows developers to follow the execution of code in the Windows Communication Foundation (WCF) infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> <span data-ttu-id="483ae-105">Windows Communication Foundation (WCF) bir hatanın nedenini tanılamaya yardımcı olmak için üç bağıntı mekanizması sağlar: Etkinlikler, aktarımlar ve yayma.</span><span class="sxs-lookup"><span data-stu-id="483ae-105">Windows Communication Foundation (WCF) provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="483ae-106">Uçtan uca izleme senaryolarına ve bunların ilgili etkinliklerini ve izleme tasarımına yönelik bir liste için [uçtan uca Izleme senaryolarına](end-to-end-tracing-scenarios.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="483ae-106">See [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="483ae-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="483ae-107">In This Section</span></span>  

 <span data-ttu-id="483ae-108">[Etkinlik](activity.md): WINDOWS COMMUNICATION FOUNDATION (WCF) izleme modelindeki etkinlik izlemelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="483ae-108">[Activity](activity.md):  Describes activity traces in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
 <span data-ttu-id="483ae-109">[Aktarım](transfer.md): WINDOWS COMMUNICATION FOUNDATION (WCF) izleme modelinde aktarımı açıklar ve uç noktalar içindeki etkinlikleri ilişkilendirmek için aktarım kullanımını kullanın.</span><span class="sxs-lookup"><span data-stu-id="483ae-109">[Transfer](transfer.md):  Describes transfer in the Windows Communication Foundation (WCF) tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="483ae-110">[Yayma](propagation.md): WINDOWS COMMUNICATION FOUNDATION (WCF) izleme modelinde etkinlik yaymayı açıklar ve etkinlikleri uç noktalar genelinde ilişkilendirmek için yayılmayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="483ae-110">[Propagation](propagation.md):  Describes activity propagation in the Windows Communication Foundation (WCF) tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="483ae-111">İzleme Türü Özeti</span><span class="sxs-lookup"><span data-stu-id="483ae-111">Trace Type Summary</span></span>](trace-type-summary.md)  
  
 <span data-ttu-id="483ae-112">Tüm etkinlik izleme türlerinin özetini sağlar</span><span class="sxs-lookup"><span data-stu-id="483ae-112">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="483ae-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="483ae-113">See also</span></span>

- [<span data-ttu-id="483ae-114">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="483ae-114">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="483ae-115">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="483ae-115">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="483ae-116">Uçtan Uca İzleme Senaryoları</span><span class="sxs-lookup"><span data-stu-id="483ae-116">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="483ae-117">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="483ae-117">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
