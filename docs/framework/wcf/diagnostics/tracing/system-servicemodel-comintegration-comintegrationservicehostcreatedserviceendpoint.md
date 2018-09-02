---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 7e7bd48d206456af6a5a8662516c4d9c82b3ed2f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384778"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="70daf-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="70daf-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="70daf-103">Taşınamıyor veya ileti Sil.</span><span class="sxs-lookup"><span data-stu-id="70daf-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="70daf-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70daf-104">Description</span></span>  
 <span data-ttu-id="70daf-105">İzleme taşımak, silmek veya bir MSMQ iletisinin reddetme çalışırken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="70daf-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="70daf-106">MSMQ iletileri tarafından Windows Communication Foundation ((NetMsmqBinding veya MsmqIntegrationBinding ile kullanıldığında) WCF) çalışan. Bu izleme, seçili değerine ilgili `ReceiveErrorHandling` NetMsmqBinding veya MsmqIntegrationBinding özelliği.</span><span class="sxs-lookup"><span data-stu-id="70daf-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="70daf-107">Bu izleme genel bir sistem hatası göstergesi değil.</span><span class="sxs-lookup"><span data-stu-id="70daf-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="70daf-108">Ancak, seçilen bir iletide başarısız oldu iletisi değerlendirme zehirli gösterir.</span><span class="sxs-lookup"><span data-stu-id="70daf-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="70daf-109">Bkz: [Poison ileti işleme](https://go.microsoft.com/fwlink/?LinkID=99546) iletileri zehirli duruma ne zaman ve uygun şekilde işlemek için hizmetinizi yapılandırmak nasıl daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="70daf-109">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70daf-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70daf-110">See Also</span></span>  
 [<span data-ttu-id="70daf-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="70daf-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="70daf-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="70daf-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="70daf-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="70daf-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
