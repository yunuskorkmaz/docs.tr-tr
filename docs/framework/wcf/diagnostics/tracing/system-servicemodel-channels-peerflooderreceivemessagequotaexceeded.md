---
description: 'Daha fazla bilgi edinin: System. ServiceModel. Channels. Peertaşan Derreceivemessagequotaaşılmıştı'
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 8ad164b253491f3a533c4828cd76f915eb5aed68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780887"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="4b520-103">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="4b520-103">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>

<span data-ttu-id="4b520-104">İletilerin gelen alım oranı çok yüksek.</span><span class="sxs-lookup"><span data-stu-id="4b520-104">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4b520-105">Description</span><span class="sxs-lookup"><span data-stu-id="4b520-105">Description</span></span>  

 <span data-ttu-id="4b520-106">Bu izleme, gelen iletileri işlemeye çalışırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="4b520-106">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="4b520-107">Bu komşu için kota kümesi aşıldığından bir ileti belirli bir komşuyla iletilemez.</span><span class="sxs-lookup"><span data-stu-id="4b520-107">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="4b520-108">Bu, yanıt vermeyen bir komşu, bu komşu için bekleyen bir ileti biriktirme listesini temizlemezse meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="4b520-108">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4b520-109">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="4b520-109">Troubleshooting</span></span>  

 <span data-ttu-id="4b520-110">Ağ içinde iletilerin gönderilme hızını azaltın.</span><span class="sxs-lookup"><span data-stu-id="4b520-110">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b520-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b520-111">See also</span></span>

- [<span data-ttu-id="4b520-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="4b520-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="4b520-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="4b520-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4b520-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="4b520-114">Administration and Diagnostics</span></span>](../index.md)
