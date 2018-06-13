---
title: ETW ile Çözümleme İzleme
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 210418b8a8765a1fc59658e9df57c92ce087c95f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809270"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="1ee44-102">ETW ile Çözümleme İzleme</span><span class="sxs-lookup"><span data-stu-id="1ee44-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="1ee44-103">Windows Communication Foundation (WCF) çözümleme izleme bir WCF Hizmeti yürütülmesi sırasında tanılama bilgileri yakalamak için bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="1ee44-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="1ee44-104">WCF hizmetleri bir üretim ortamında sorun giderme izin vermek için WCF yığınında anahtar noktalarda WCF analiz izleme olaylarını gösterilen.</span><span class="sxs-lookup"><span data-stu-id="1ee44-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="1ee44-105">Çözümleme izleme WCF hizmetleri için bir ürün sunucusunun performansı üzerinde en az etki barındıran sahip [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF hizmetleri bu olayları olay izleme için Windows (ETW) oturumuna çok verimli bir şekilde gösterilen gibi.</span><span class="sxs-lookup"><span data-stu-id="1ee44-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ee44-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1ee44-106">In This Section</span></span>  
 [<span data-ttu-id="1ee44-107">Analitik İzlemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1ee44-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="1ee44-108">İçinde WCF analiz izleme nasıl çalıştığı açıklanır [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ee44-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="1ee44-109">Analitik İzlemeyi Dinamik Olarak Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1ee44-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="1ee44-110">Etkinleştirmek veya kullanarak dinamik olarak ETW İzleme devre dışı bırakma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1ee44-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="1ee44-111">İleti Akışı İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1ee44-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="1ee44-112">İleti akışı izlemeyi yapılandırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="1ee44-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="1ee44-113">Analitik İzleme Etkinliği Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1ee44-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="1ee44-114">Bir olay kimliklerini olay düzeyleri, olay iletileri ve anahtar sözcükler tablosu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ee44-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee44-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ee44-115">See Also</span></span>  
 [<span data-ttu-id="1ee44-116">WCF Hizmetleri ve Windows için Olay İzleme</span><span class="sxs-lookup"><span data-stu-id="1ee44-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [<span data-ttu-id="1ee44-117">Windows'da Olay İzleme ile Olayları İzleme</span><span class="sxs-lookup"><span data-stu-id="1ee44-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
