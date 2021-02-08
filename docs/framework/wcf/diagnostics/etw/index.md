---
description: 'Daha fazla bilgi edinin: ETW ile analitik Izleme'
title: ETW ile Çözümleme İzleme
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: fd40d40de2508fd251c793e4455c1e656a1cbbf6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798803"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="ea3e8-103">ETW ile Çözümleme İzleme</span><span class="sxs-lookup"><span data-stu-id="ea3e8-103">Analytic Tracing with ETW</span></span>

<span data-ttu-id="ea3e8-104">Windows Communication Foundation (WCF) analitik izleme, bir WCF hizmetinin yürütülmesi sırasında tanılama bilgilerini yakalamak için bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="ea3e8-104">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="ea3e8-105">WCF analitik izleme olayları, bir üretim ortamında WCF hizmetleri sorunlarını gidermeye olanak tanımak için WCF yığınındaki anahtar noktalarında dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="ea3e8-105">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="ea3e8-106">WCF Hizmetleri için analitik izleme, [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] Bu olaylar Windows Için olay izleme (ETW) oturumuna çok verimli bir şekilde yayıldığından, WCF hizmetlerini barındıran bir ürün sunucusunun performansı üzerinde en az etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="ea3e8-106">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea3e8-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ea3e8-107">In This Section</span></span>  

 [<span data-ttu-id="ea3e8-108">Çözümleme İzleme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ea3e8-108">Analytic Tracing Overview</span></span>](analytic-tracing-overview.md)  
 <span data-ttu-id="ea3e8-109">WCF analitik izlemenin ' de nasıl çalıştığını açıklar [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ea3e8-109">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="ea3e8-110">Analitik İzlemeyi Dinamik Olarak Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ea3e8-110">Dynamically Enabling Analytic Tracing</span></span>](dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="ea3e8-111">ETW kullanarak izlemenin dinamik olarak nasıl etkinleştirileceğini veya devre dışı bırakılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ea3e8-111">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="ea3e8-112">İleti Akışı İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ea3e8-112">Configuring Message Flow Tracing</span></span>](configuring-message-flow-tracing.md)  
 <span data-ttu-id="ea3e8-113">İleti akışı izlemenin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ea3e8-113">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="ea3e8-114">Çözümleme İzleme Etkinliği Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ea3e8-114">Analytic Trace Event Reference</span></span>](analytic-trace-event-reference.md)  
 <span data-ttu-id="ea3e8-115">Olay düzeyleri, olay iletileri ve anahtar kelimeleri ile olay kimliklerinin bir tablosunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea3e8-115">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea3e8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea3e8-116">See also</span></span>

- [<span data-ttu-id="ea3e8-117">Windows için WCF Hizmetleri ve Etkinlik İzleme</span><span class="sxs-lookup"><span data-stu-id="ea3e8-117">WCF Services and Event Tracing for Windows</span></span>](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [<span data-ttu-id="ea3e8-118">Windows'ta Olay İzleme ile Olayları İzleme</span><span class="sxs-lookup"><span data-stu-id="ea3e8-118">Tracking Events into Event Tracing in Windows</span></span>](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
