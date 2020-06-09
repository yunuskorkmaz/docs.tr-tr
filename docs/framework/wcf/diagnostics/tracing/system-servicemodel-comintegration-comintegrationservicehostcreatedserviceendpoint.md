---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 8b81cdcaf74aca044260495867b2c4f1de517682
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593756"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="8b92a-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="8b92a-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="8b92a-103">İleti taşınamıyor ya da silinemiyor.</span><span class="sxs-lookup"><span data-stu-id="8b92a-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8b92a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b92a-104">Description</span></span>  
 <span data-ttu-id="8b92a-105">İzleme, bir MSMQ iletisini taşımaya, silmeye veya reddetmeye çalışırken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b92a-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="8b92a-106">MSMQ iletileri Windows Communication Foundation (WCF) tarafından (NetMsmqBinding veya MsmqIntegrationBinding ile kullanıldığında) tarafından kullanılır. Bu izleme, `ReceiveErrorHandling` NetMsmqBinding veya MsmqIntegrationBinding üzerinde özelliğin seçili değeri ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="8b92a-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="8b92a-107">Bu izleme, bir genel sistem hatasının göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="8b92a-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="8b92a-108">Ancak, seçilen zarar iletisi değerlendirmesi bir ileti için başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b92a-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="8b92a-109">İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="8b92a-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b92a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b92a-110">See also</span></span>

- [<span data-ttu-id="8b92a-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="8b92a-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="8b92a-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="8b92a-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8b92a-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="8b92a-113">Administration and Diagnostics</span></span>](../index.md)
