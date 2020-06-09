---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ce97eaa2ad5c9dbd5f4d6f81186960c489eb4b85
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596083"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="c6f97-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="c6f97-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="c6f97-103">Peerbakımcı modülü belirli bir işlemi gerçekleştiriyor (izleme iletisi gövdesinde bulunan Ayrıntılar).</span><span class="sxs-lookup"><span data-stu-id="c6f97-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="c6f97-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6f97-104">Description</span></span>  
 <span data-ttu-id="c6f97-105">Bu izleme, çeşitli Peerbakımcı işlemleri sırasında oluşur.</span><span class="sxs-lookup"><span data-stu-id="c6f97-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="c6f97-106">Peerbakımcı, bir PeerNode iç bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="c6f97-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="c6f97-107">Her dakika veya alınan her 32 ileti, komşunlarına kaç tane ileti değiştirildiğini ve kaç tane yararlı olduğunu (yinelenmeyen, değiştirilmemiş) gösteren istatistiklerle bir LinkUtility iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="c6f97-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="c6f97-108">Bu, belirli bir komşunun bağlantı yardımcı programını belirlemesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c6f97-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="c6f97-109">Her beş dakikada bir, bakımcı, komşu bağlantıların sistem durumunu denetler.</span><span class="sxs-lookup"><span data-stu-id="c6f97-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="c6f97-110">Komşu bağlantı sayısı ideal miktarı aşarsa, bakımcı en az faydalı bağlantıları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="c6f97-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="c6f97-111">Yeterli bağlantı yoksa, bakımcı yeni bağlantıları alır.</span><span class="sxs-lookup"><span data-stu-id="c6f97-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f97-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6f97-112">See also</span></span>

- [<span data-ttu-id="c6f97-113">İzleme</span><span class="sxs-lookup"><span data-stu-id="c6f97-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="c6f97-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="c6f97-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c6f97-115">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="c6f97-115">Administration and Diagnostics</span></span>](../index.md)
