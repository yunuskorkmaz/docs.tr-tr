---
title: Uçtan Uca İzleme
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: 733ea0724fdbaea9c7d28ed2a94aba25f67ef87c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474226"
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="b1474-102">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="b1474-102">End-to-End Tracing</span></span>
<span data-ttu-id="b1474-103">Uçtan uca bir kod yolu neden başarısız oldu araştırmak veya kapasite planlama ve performans analizi için ayrıntılı izleme sağlamak için Windows Communication Foundation (WCF) altyapısında kodun yürütülmesini izlemek geliştiricilerin (e2e) izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1474-103">End to End (e2e) Tracing allows developers to follow the execution of code in the Windows Communication Foundation (WCF) infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> <span data-ttu-id="b1474-104">Windows Communication Foundation (WCF) bir hatanın nedenini tanılamaya yardımcı olmak için üç bağıntı mekanizma sağlar: etkinlikleri, aktarımları ve yayma.</span><span class="sxs-lookup"><span data-stu-id="b1474-104">Windows Communication Foundation (WCF) provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="b1474-105">Bkz: [uçtan uca izleme senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) uçtan uca izleme senaryoları ve bunların ilgili etkinliği ve tasarım izleme listesi.</span><span class="sxs-lookup"><span data-stu-id="b1474-105">See [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1474-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b1474-106">In This Section</span></span>  
 <span data-ttu-id="b1474-107">[Etkinlik](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md): Windows Communication Foundation (WCF) izleme modelinde etkinlik izlemeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b1474-107">[Activity](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Describes activity traces in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
 <span data-ttu-id="b1474-108">[Aktarım](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md): Windows Communication Foundation (WCF) izleme modelinde aktarımı açıklar ve kullanılarak aktarılmaz uç noktaları'nda etkinlikler ilişkilendirmek için.</span><span class="sxs-lookup"><span data-stu-id="b1474-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Describes transfer in the Windows Communication Foundation (WCF) tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="b1474-109">[Yayma](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md): Etkinlik yayma içinde Windows Communication Foundation (modeli izleme ve uç noktalar arasında etkinliklerini ilişkilendirmek için yayma kullanarak WCF) açıklar.</span><span class="sxs-lookup"><span data-stu-id="b1474-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Describes activity propagation in the Windows Communication Foundation (WCF) tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="b1474-110">İzleme Türü Özeti</span><span class="sxs-lookup"><span data-stu-id="b1474-110">Trace Type Summary</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/trace-type-summary.md)  
  
 <span data-ttu-id="b1474-111">İzleme türleri tüm etkinliklerin bir özetini sunar</span><span class="sxs-lookup"><span data-stu-id="b1474-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1474-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1474-112">See Also</span></span>  
 [<span data-ttu-id="b1474-113">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b1474-113">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="b1474-114">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="b1474-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="b1474-115">Uçtan Uca İzleme Senaryoları</span><span class="sxs-lookup"><span data-stu-id="b1474-115">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="b1474-116">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="b1474-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
