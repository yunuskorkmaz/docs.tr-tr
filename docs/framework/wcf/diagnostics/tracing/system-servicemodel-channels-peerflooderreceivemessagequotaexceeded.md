---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 136baabc0760826aa9ba76dc19862c9c4b60e16e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="8b014-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="8b014-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="8b014-103">İletilerin gelen alma hızı çok yüksektir.</span><span class="sxs-lookup"><span data-stu-id="8b014-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8b014-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b014-104">Description</span></span>  
 <span data-ttu-id="8b014-105">Bu izleme, gelen iletileri işlemek çalışılırken zaman oluşur.</span><span class="sxs-lookup"><span data-stu-id="8b014-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="8b014-106">Bu komşusu için belirlediğiniz kotayı aştığı için bir ileti için belirli bir komşu iletilemedi.</span><span class="sxs-lookup"><span data-stu-id="8b014-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="8b014-107">Bu durum, bu komşusu için biriktirme listesi iletileri temizlemek bir yanıt vermeyen komşu başarısız oluşur.</span><span class="sxs-lookup"><span data-stu-id="8b014-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8b014-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="8b014-108">Troubleshooting</span></span>  
 <span data-ttu-id="8b014-109">Mesh içinde gönderilen iletileri hızını azaltın.</span><span class="sxs-lookup"><span data-stu-id="8b014-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b014-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b014-110">See Also</span></span>  
 [<span data-ttu-id="8b014-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="8b014-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8b014-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="8b014-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8b014-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="8b014-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
