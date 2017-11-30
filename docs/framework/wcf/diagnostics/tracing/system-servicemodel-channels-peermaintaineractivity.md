---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3cde90bf5e9c57ff54378eaaf970aec219871a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="7600f-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="7600f-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="7600f-103">PeerMaintainer Modülü (izleme ileti gövdesi içinde ayrıntıları) belirli bir işlemi gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="7600f-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="7600f-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7600f-104">Description</span></span>  
 <span data-ttu-id="7600f-105">Bu izleme, çeşitli PeerMaintainer işlemleri sırasında oluşur.</span><span class="sxs-lookup"><span data-stu-id="7600f-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="7600f-106">PeerMaintainer PeerNode iç bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="7600f-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="7600f-107">Dakikada ya da aldığınız her 32 iletileri LinkUtility iletisi Komşuları istatistiklerle birlikte kaç iletileri hakkında değiştirilir ve yararlı (olmayan-untampered yinelemeleri) kaç gönderir.</span><span class="sxs-lookup"><span data-stu-id="7600f-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="7600f-108">Bu, belirli komşu 's bağlantı yardımcı programı belirlenmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7600f-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="7600f-109">Yaklaşık her beş dakikada Bakımcı komşu bağlantıları durumunu denetler.</span><span class="sxs-lookup"><span data-stu-id="7600f-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="7600f-110">Komşu bağlantıları sayısı ideal miktarını aşarsa Bakımcı az yararlı bağlantıları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="7600f-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="7600f-111">Yeterli bağlantıları değilse Bakımcı yeni bağlantıları edinir.</span><span class="sxs-lookup"><span data-stu-id="7600f-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7600f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7600f-112">See Also</span></span>  
 [<span data-ttu-id="7600f-113">İzleme</span><span class="sxs-lookup"><span data-stu-id="7600f-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="7600f-114">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="7600f-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="7600f-115">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="7600f-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
