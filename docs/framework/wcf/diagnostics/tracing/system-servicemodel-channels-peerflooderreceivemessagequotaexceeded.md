---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: d4fbbeaaa1daeea62b5495d0b30c37d0297ccd75
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249923"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="36144-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="36144-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>

<span data-ttu-id="36144-103">İletilerin gelen alım oranı çok yüksek.</span><span class="sxs-lookup"><span data-stu-id="36144-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="36144-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36144-104">Description</span></span>  

 <span data-ttu-id="36144-105">Bu izleme, gelen iletileri işlemeye çalışırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="36144-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="36144-106">Bu komşu için kota kümesi aşıldığından bir ileti belirli bir komşuyla iletilemez.</span><span class="sxs-lookup"><span data-stu-id="36144-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="36144-107">Bu, yanıt vermeyen bir komşu, bu komşu için bekleyen bir ileti biriktirme listesini temizlemezse meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="36144-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="36144-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="36144-108">Troubleshooting</span></span>  

 <span data-ttu-id="36144-109">Ağ içinde iletilerin gönderilme hızını azaltın.</span><span class="sxs-lookup"><span data-stu-id="36144-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36144-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36144-110">See also</span></span>

- [<span data-ttu-id="36144-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="36144-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="36144-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="36144-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="36144-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="36144-113">Administration and Diagnostics</span></span>](../index.md)
