---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: aeeba38eaf674453f4c87cf62f5088c55b5fde2d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290822"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="dda28-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="dda28-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>

<span data-ttu-id="dda28-103">İleti taşınamıyor ya da silinemiyor.</span><span class="sxs-lookup"><span data-stu-id="dda28-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dda28-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dda28-104">Description</span></span>  

 <span data-ttu-id="dda28-105">İzleme, bir MSMQ iletisini taşımaya, silmeye veya reddetmeye çalışırken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dda28-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="dda28-106">MSMQ iletileri Windows Communication Foundation (WCF) tarafından (NetMsmqBinding veya MsmqIntegrationBinding ile kullanıldığında) tarafından kullanılır. Bu izleme, `ReceiveErrorHandling` NetMsmqBinding veya MsmqIntegrationBinding üzerinde özelliğin seçili değeri ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="dda28-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="dda28-107">Bu izleme, bir genel sistem hatasının göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="dda28-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="dda28-108">Ancak, seçilen zarar iletisi değerlendirmesi bir ileti için başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dda28-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="dda28-109">İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="dda28-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda28-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dda28-110">See also</span></span>

- [<span data-ttu-id="dda28-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="dda28-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="dda28-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="dda28-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="dda28-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="dda28-113">Administration and Diagnostics</span></span>](../index.md)
