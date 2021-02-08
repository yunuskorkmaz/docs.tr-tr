---
description: ': System. ServiceModel. Channels. Peerbakımeylemsizlik etkinliği hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: da4e4cf87da808cb6779445b6507b51d098132b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780888"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="cb485-103">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="cb485-103">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>

<span data-ttu-id="cb485-104">Peerbakımcı modülü belirli bir işlemi gerçekleştiriyor (izleme iletisi gövdesinde bulunan Ayrıntılar).</span><span class="sxs-lookup"><span data-stu-id="cb485-104">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="cb485-105">Description</span><span class="sxs-lookup"><span data-stu-id="cb485-105">Description</span></span>  

 <span data-ttu-id="cb485-106">Bu izleme, çeşitli Peerbakımcı işlemleri sırasında oluşur.</span><span class="sxs-lookup"><span data-stu-id="cb485-106">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="cb485-107">Peerbakımcı, bir PeerNode iç bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="cb485-107">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="cb485-108">Her dakika veya alınan her 32 ileti, komşunlarına kaç tane ileti değiştirildiğini ve kaç tane yararlı olduğunu (yinelenmeyen, değiştirilmemiş) gösteren istatistiklerle bir LinkUtility iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="cb485-108">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="cb485-109">Bu, belirli bir komşunun bağlantı yardımcı programını belirlemesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="cb485-109">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="cb485-110">Her beş dakikada bir, bakımcı, komşu bağlantıların sistem durumunu denetler.</span><span class="sxs-lookup"><span data-stu-id="cb485-110">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="cb485-111">Komşu bağlantı sayısı ideal miktarı aşarsa, bakımcı en az faydalı bağlantıları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="cb485-111">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="cb485-112">Yeterli bağlantı yoksa, bakımcı yeni bağlantıları alır.</span><span class="sxs-lookup"><span data-stu-id="cb485-112">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb485-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb485-113">See also</span></span>

- [<span data-ttu-id="cb485-114">İzleme</span><span class="sxs-lookup"><span data-stu-id="cb485-114">Tracing</span></span>](index.md)
- [<span data-ttu-id="cb485-115">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="cb485-115">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="cb485-116">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="cb485-116">Administration and Diagnostics</span></span>](../index.md)
