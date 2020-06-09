---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 93afa0b495e20c02c58ac1fa75c31715eaa0e8dc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596096"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="529e3-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="529e3-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="529e3-103">İletilerin gelen alım oranı çok yüksek.</span><span class="sxs-lookup"><span data-stu-id="529e3-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="529e3-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="529e3-104">Description</span></span>  
 <span data-ttu-id="529e3-105">Bu izleme, gelen iletileri işlemeye çalışırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="529e3-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="529e3-106">Bu komşu için kota kümesi aşıldığından bir ileti belirli bir komşuyla iletilemez.</span><span class="sxs-lookup"><span data-stu-id="529e3-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="529e3-107">Bu, yanıt vermeyen bir komşu, bu komşu için bekleyen bir ileti biriktirme listesini temizlemezse meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="529e3-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="529e3-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="529e3-108">Troubleshooting</span></span>  
 <span data-ttu-id="529e3-109">Ağ içinde iletilerin gönderilme hızını azaltın.</span><span class="sxs-lookup"><span data-stu-id="529e3-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="529e3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="529e3-110">See also</span></span>

- [<span data-ttu-id="529e3-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="529e3-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="529e3-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="529e3-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="529e3-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="529e3-113">Administration and Diagnostics</span></span>](../index.md)
