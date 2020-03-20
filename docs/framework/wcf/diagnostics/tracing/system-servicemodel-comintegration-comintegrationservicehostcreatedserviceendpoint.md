---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: f89dd1373d67714046f8cb958582c3a5dea04456
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674786"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="1a27d-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="1a27d-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="1a27d-103">İletiyi taşıyamaz veya silemez.</span><span class="sxs-lookup"><span data-stu-id="1a27d-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1a27d-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a27d-104">Description</span></span>  
 <span data-ttu-id="1a27d-105">İzleme, bir MSMQ iletisini taşımaya, silmeye veya reddetmeye çalışırken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a27d-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="1a27d-106">MSMQ iletileri Windows Communication Foundation (WCF) tarafından kullanılır (NetMsmqBinding veya MsmqIntegrationBinding ile birlikte kullanıldığında). Bu izleme, NetMsmqBinding `ReceiveErrorHandling` veya MsmqIntegrationBinding üzerinde özelliğin seçilen değeri ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="1a27d-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="1a27d-107">Bu izleme, genel bir sistem hatasının göstergesi değildir.</span><span class="sxs-lookup"><span data-stu-id="1a27d-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="1a27d-108">Ancak, seçilen zehirli ileti nin bir ileti için başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a27d-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="1a27d-109">İletilerin ne zaman zehirhaline geldiği ve hizmetinizi uygun şekilde işlemek üzere nasıl yapılandırılacağı hakkında daha fazla bilgi için [Poison-Message Handling](../../feature-details/poison-message-handling.md)'e bakın.</span><span class="sxs-lookup"><span data-stu-id="1a27d-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a27d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a27d-110">See also</span></span>

- [<span data-ttu-id="1a27d-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="1a27d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="1a27d-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="1a27d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1a27d-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="1a27d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
