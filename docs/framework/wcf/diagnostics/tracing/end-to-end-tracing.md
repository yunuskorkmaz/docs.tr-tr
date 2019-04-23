---
title: Uçtan Uca İzleme
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: fd2964b39c758e41620fb453ddd8f61a1aa550aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092148"
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="c8b02-102">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="c8b02-102">End-to-End Tracing</span></span>
<span data-ttu-id="c8b02-103">Uçtan uca (e2e) izleme neden bir kod yolu başarısız oldu araştırmak için ya da kapasite planlama ve performans analizi için ayrıntılı izleme sağlamak için Windows Communication Foundation (WCF) altyapısındaki kodun yürütülmesini izlemek geliştiricilerin sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8b02-103">End to End (e2e) Tracing allows developers to follow the execution of code in the Windows Communication Foundation (WCF) infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> <span data-ttu-id="c8b02-104">Windows Communication Foundation (WCF), bir hatanın nedenini tanılamaya yardımcı olmak için üç bağıntı mekanizmaları sağlar: etkinlikleri, aktarımı ve yayma.</span><span class="sxs-lookup"><span data-stu-id="c8b02-104">Windows Communication Foundation (WCF) provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="c8b02-105">Bkz: [uçtan uca izleme senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) uçtan uca izleme senaryoları ve ilgili etkinlikler ve tasarım izleme listesi.</span><span class="sxs-lookup"><span data-stu-id="c8b02-105">See [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8b02-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c8b02-106">In This Section</span></span>  
 <span data-ttu-id="c8b02-107">[Etkinlik](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Windows Communication Foundation (WCF) izleme modelinde etkinlik izlemeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8b02-107">[Activity](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Describes activity traces in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
 <span data-ttu-id="c8b02-108">[Aktarım](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Windows Communication Foundation (WCF) izleme modelinde aktarımı açıklar ve uç noktaları içindeki etkinliklerini ilişkilendirmek için aktarımı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="c8b02-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Describes transfer in the Windows Communication Foundation (WCF) tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="c8b02-109">[Yayma](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Etkinlik yayma, Windows Communication Foundation (model izleme ve uç noktalar genelinde etkinliklerini ilişkilendirmek için yayma işlemi kullanarak WCF) açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8b02-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Describes activity propagation in the Windows Communication Foundation (WCF) tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="c8b02-110">İzleme Türü Özeti</span><span class="sxs-lookup"><span data-stu-id="c8b02-110">Trace Type Summary</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/trace-type-summary.md)  
  
 <span data-ttu-id="c8b02-111">Tüm etkinliklerin özetini izleme türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8b02-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b02-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8b02-112">See also</span></span>

- [<span data-ttu-id="c8b02-113">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c8b02-113">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="c8b02-114">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="c8b02-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="c8b02-115">Uçtan Uca İzleme Senaryoları</span><span class="sxs-lookup"><span data-stu-id="c8b02-115">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="c8b02-116">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="c8b02-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
