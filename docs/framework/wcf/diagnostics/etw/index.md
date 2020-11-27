---
title: ETW ile Çözümleme İzleme
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 4bb31eeac7c5d3c8c30f66090b07de9f8af4d5a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274627"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="4e7b9-102">ETW ile Çözümleme İzleme</span><span class="sxs-lookup"><span data-stu-id="4e7b9-102">Analytic Tracing with ETW</span></span>

<span data-ttu-id="4e7b9-103">Windows Communication Foundation (WCF) analitik izleme, bir WCF hizmetinin yürütülmesi sırasında tanılama bilgilerini yakalamak için bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="4e7b9-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="4e7b9-104">WCF analitik izleme olayları, bir üretim ortamında WCF hizmetleri sorunlarını gidermeye olanak tanımak için WCF yığınındaki anahtar noktalarında dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="4e7b9-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="4e7b9-105">WCF Hizmetleri için analitik izleme, [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] Bu olaylar Windows Için olay izleme (ETW) oturumuna çok verimli bir şekilde yayıldığından, WCF hizmetlerini barındıran bir ürün sunucusunun performansı üzerinde en az etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="4e7b9-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e7b9-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4e7b9-106">In This Section</span></span>  

 [<span data-ttu-id="4e7b9-107">Çözümleme İzleme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4e7b9-107">Analytic Tracing Overview</span></span>](analytic-tracing-overview.md)  
 <span data-ttu-id="4e7b9-108">WCF analitik izlemenin ' de nasıl çalıştığını açıklar [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4e7b9-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="4e7b9-109">Analitik İzlemeyi Dinamik Olarak Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="4e7b9-109">Dynamically Enabling Analytic Tracing</span></span>](dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="4e7b9-110">ETW kullanarak izlemenin dinamik olarak nasıl etkinleştirileceğini veya devre dışı bırakılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4e7b9-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="4e7b9-111">İleti Akışı İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4e7b9-111">Configuring Message Flow Tracing</span></span>](configuring-message-flow-tracing.md)  
 <span data-ttu-id="4e7b9-112">İleti akışı izlemenin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4e7b9-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="4e7b9-113">Çözümleme İzleme Etkinliği Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4e7b9-113">Analytic Trace Event Reference</span></span>](analytic-trace-event-reference.md)  
 <span data-ttu-id="4e7b9-114">Olay düzeyleri, olay iletileri ve anahtar kelimeleri ile olay kimliklerinin bir tablosunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e7b9-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7b9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e7b9-115">See also</span></span>

- [<span data-ttu-id="4e7b9-116">Windows için WCF Hizmetleri ve Etkinlik İzleme</span><span class="sxs-lookup"><span data-stu-id="4e7b9-116">WCF Services and Event Tracing for Windows</span></span>](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [<span data-ttu-id="4e7b9-117">Windows'ta Olay İzleme ile Olayları İzleme</span><span class="sxs-lookup"><span data-stu-id="4e7b9-117">Tracking Events into Event Tracing in Windows</span></span>](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
