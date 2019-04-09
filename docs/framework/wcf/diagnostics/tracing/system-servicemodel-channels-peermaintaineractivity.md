---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ea4c8110a8f820e0c6204fbd22b3d5b747709fba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126041"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="64083-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="64083-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="64083-103">PeerMaintainer modülü, belirli bir işlemi (ayrıntıları izleme iletisi gövdesi içinde yer alan) gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="64083-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="64083-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64083-104">Description</span></span>  
 <span data-ttu-id="64083-105">Bu izleme, çeşitli PeerMaintainer işlemleri sırasında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="64083-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="64083-106">PeerMaintainer PeerNode iç bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="64083-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="64083-107">Dakika başı veya alınan her 32 ileti LinkUtility iletisi Komşuları istatistiklerle kaç mesajları hakkında ve ne kadar yararlı (olmayan-untampered yinelemeleri) gönderir.</span><span class="sxs-lookup"><span data-stu-id="64083-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="64083-108">Bu, belirli bir komşunun bağlantısı yardımcı programı belirlenmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="64083-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="64083-109">Yaklaşık beş dakikada, Bakımcı komşu bağlantı durumunu denetler.</span><span class="sxs-lookup"><span data-stu-id="64083-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="64083-110">Komşu bağlantı sayısını ideal miktarı aşarsa, Bakımcı az yararlı bağlantıları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="64083-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="64083-111">Yeterli bağlantı yoksa, yeni bağlantılar Bakımcı devralır.</span><span class="sxs-lookup"><span data-stu-id="64083-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64083-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64083-112">See also</span></span>

- [<span data-ttu-id="64083-113">İzleme</span><span class="sxs-lookup"><span data-stu-id="64083-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="64083-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="64083-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="64083-115">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="64083-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
