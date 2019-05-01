---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ea4c8110a8f820e0c6204fbd22b3d5b747709fba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61950468"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="01340-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="01340-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="01340-103">PeerMaintainer modülü, belirli bir işlemi (ayrıntıları izleme iletisi gövdesi içinde yer alan) gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="01340-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="01340-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01340-104">Description</span></span>  
 <span data-ttu-id="01340-105">Bu izleme, çeşitli PeerMaintainer işlemleri sırasında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="01340-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="01340-106">PeerMaintainer PeerNode iç bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="01340-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="01340-107">Dakika başı veya alınan her 32 ileti LinkUtility iletisi Komşuları istatistiklerle kaç mesajları hakkında ve ne kadar yararlı (olmayan-untampered yinelemeleri) gönderir.</span><span class="sxs-lookup"><span data-stu-id="01340-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="01340-108">Bu, belirli bir komşunun bağlantısı yardımcı programı belirlenmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="01340-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="01340-109">Yaklaşık beş dakikada, Bakımcı komşu bağlantı durumunu denetler.</span><span class="sxs-lookup"><span data-stu-id="01340-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="01340-110">Komşu bağlantı sayısını ideal miktarı aşarsa, Bakımcı az yararlı bağlantıları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="01340-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="01340-111">Yeterli bağlantı yoksa, yeni bağlantılar Bakımcı devralır.</span><span class="sxs-lookup"><span data-stu-id="01340-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01340-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01340-112">See also</span></span>

- [<span data-ttu-id="01340-113">İzleme</span><span class="sxs-lookup"><span data-stu-id="01340-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="01340-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="01340-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="01340-115">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="01340-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
