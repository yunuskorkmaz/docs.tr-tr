---
title: "ETW ile Çözümleme İzleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a16f66ed8443749764e66d2616ae566ad788d571
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="b1ac2-102">ETW ile Çözümleme İzleme</span><span class="sxs-lookup"><span data-stu-id="b1ac2-102">Analytic Tracing with ETW</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="b1ac2-103">Çözümleme izleme yürütülmesi sırasında tanılama bilgileri yakalamak için bir yol sunan bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="b1ac2-103"> analytic tracing offers a way to capture diagnostic information during the execution of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="b1ac2-104">Çözümleme izleme olayları yayılan anahtar noktalarında [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] , sorun giderme izin vermek için yığın [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] bir üretim ortamında Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="b1ac2-104"> analytic tracing events are emitted at key points in the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stack to allow troubleshooting of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services in a production environment.</span></span> <span data-ttu-id="b1ac2-105">Analitik izlemeyi [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmetleri barındıran bir ürün sunucusunun performansı üzerinde en az etki olan [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri bu olayları olay izleme için Windows (ETW) oturumuna çok verimli bir şekilde gösterilen gibi.</span><span class="sxs-lookup"><span data-stu-id="b1ac2-105">Analytic tracing for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1ac2-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b1ac2-106">In This Section</span></span>  
 [<span data-ttu-id="b1ac2-107">Analitik İzlemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b1ac2-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="b1ac2-108">Anlatılmaktadır nasıl [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] çözümleme izleme çalışır [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1ac2-108">Discusses how [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="b1ac2-109">Analitik İzlemeyi Dinamik Olarak Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b1ac2-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="b1ac2-110">Etkinleştirmek veya kullanarak dinamik olarak ETW İzleme devre dışı bırakma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b1ac2-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="b1ac2-111">İleti Akışı İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b1ac2-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="b1ac2-112">İleti akışı izlemeyi yapılandırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="b1ac2-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="b1ac2-113">Analitik İzleme Etkinliği Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b1ac2-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="b1ac2-114">Bir olay kimliklerini olay düzeyleri, olay iletileri ve anahtar sözcükler tablosu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1ac2-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ac2-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1ac2-115">See Also</span></span>  
 [<span data-ttu-id="b1ac2-116">WCF Hizmetleri ve Windows için Olay İzleme</span><span class="sxs-lookup"><span data-stu-id="b1ac2-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [<span data-ttu-id="b1ac2-117">Windows'da Olay İzleme ile Olayları İzleme</span><span class="sxs-lookup"><span data-stu-id="b1ac2-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
