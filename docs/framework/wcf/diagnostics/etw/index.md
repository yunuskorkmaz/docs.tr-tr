---
title: ETW ile Çözümleme İzleme
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: cff13439995d8a90da15b7afa15723f21574e35e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193732"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="c4cd7-102">ETW ile Çözümleme İzleme</span><span class="sxs-lookup"><span data-stu-id="c4cd7-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="c4cd7-103">Windows Communication Foundation (WCF) analitik izleme bir WCF Hizmeti yürütülmesi sırasında tanılama bilgileri toplamak için bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="c4cd7-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="c4cd7-104">WCF analiz izleme olaylar, WCF hizmetleri bir üretim ortamında giderme izin vermek için WCF yığınında önemli anlarda gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c4cd7-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="c4cd7-105">Çözümleme izleme WCF hizmetleri için bir ürün sunucusunun performansını en az etki barındıran sahip [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF hizmetleri gibi bu olaylar için bir olay izleme için Windows (ETW) oturumu çok verimli bir şekilde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c4cd7-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c4cd7-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c4cd7-106">In This Section</span></span>  
 [<span data-ttu-id="c4cd7-107">Çözümleme İzleme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c4cd7-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="c4cd7-108">WCF analiz izleme işleyişi anlatılmaktadır [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c4cd7-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="c4cd7-109">Analitik İzlemeyi Dinamik Olarak Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c4cd7-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="c4cd7-110">Etkinleştirmek veya devre dışı kullanılarak dinamik olarak ETW İzleme anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4cd7-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="c4cd7-111">İleti Akışı İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c4cd7-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="c4cd7-112">İleti akışı izlemeyi yapılandırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="c4cd7-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="c4cd7-113">Çözümleme İzleme Etkinliği Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c4cd7-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="c4cd7-114">Olay kimliklerini olay düzeyleri, olay iletileri ve anahtar sözcükler, bir tablo gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4cd7-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4cd7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4cd7-115">See also</span></span>

- [<span data-ttu-id="c4cd7-116">Windows için WCF Hizmetleri ve Etkinlik İzleme</span><span class="sxs-lookup"><span data-stu-id="c4cd7-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
- [<span data-ttu-id="c4cd7-117">Windows'ta Olay İzleme ile Olayları İzleme</span><span class="sxs-lookup"><span data-stu-id="c4cd7-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
