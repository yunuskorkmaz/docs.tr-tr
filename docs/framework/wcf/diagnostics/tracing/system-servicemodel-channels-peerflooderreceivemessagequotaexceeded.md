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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2931eec5646b44eea19d70b11eb43c056b0ee0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="0b44a-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="0b44a-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="0b44a-103">İletilerin gelen alma hızı çok yüksektir.</span><span class="sxs-lookup"><span data-stu-id="0b44a-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0b44a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b44a-104">Description</span></span>  
 <span data-ttu-id="0b44a-105">Bu izleme, gelen iletileri işlemek çalışılırken zaman oluşur.</span><span class="sxs-lookup"><span data-stu-id="0b44a-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="0b44a-106">Bu komşusu için belirlediğiniz kotayı aştığı için bir ileti için belirli bir komşu iletilemedi.</span><span class="sxs-lookup"><span data-stu-id="0b44a-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="0b44a-107">Bu durum, bu komşusu için biriktirme listesi iletileri temizlemek bir yanıt vermeyen komşu başarısız oluşur.</span><span class="sxs-lookup"><span data-stu-id="0b44a-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0b44a-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="0b44a-108">Troubleshooting</span></span>  
 <span data-ttu-id="0b44a-109">Mesh içinde gönderilen iletileri hızını azaltın.</span><span class="sxs-lookup"><span data-stu-id="0b44a-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b44a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b44a-110">See Also</span></span>  
 [<span data-ttu-id="0b44a-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="0b44a-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0b44a-112">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="0b44a-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0b44a-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="0b44a-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
