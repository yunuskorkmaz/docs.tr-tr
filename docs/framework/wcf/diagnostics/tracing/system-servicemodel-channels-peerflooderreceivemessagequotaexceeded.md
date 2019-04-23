---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 0ca3d198ce225221348ac7b405ea91ad215cd298
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190905"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="6744a-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="6744a-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="6744a-103">İletilerin gelen alma hızı çok yüksektir.</span><span class="sxs-lookup"><span data-stu-id="6744a-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6744a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6744a-104">Description</span></span>  
 <span data-ttu-id="6744a-105">Bu izleme, gelen iletileri işlemek çalışılırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="6744a-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="6744a-106">Bu komşu için belirlediğiniz kotayı aştığı için bir ileti için belirli bir komşu iletilemedi.</span><span class="sxs-lookup"><span data-stu-id="6744a-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="6744a-107">Bekleyen iletiler, bir biriktirme listesi için bir komşu temizlemek bir yanıt vermeyen komşu başarısız olduğunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="6744a-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6744a-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="6744a-108">Troubleshooting</span></span>  
 <span data-ttu-id="6744a-109">Kafes içinde gönderilen iletileri oranı azaltın.</span><span class="sxs-lookup"><span data-stu-id="6744a-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6744a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6744a-110">See also</span></span>

- [<span data-ttu-id="6744a-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="6744a-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="6744a-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="6744a-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6744a-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="6744a-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
