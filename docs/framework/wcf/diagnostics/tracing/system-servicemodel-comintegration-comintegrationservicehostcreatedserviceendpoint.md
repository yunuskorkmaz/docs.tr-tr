---
description: ': System. ServiceModel. Channels. MsmqMoveOrDeleteAttemptFailed hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 7b3c8dad9e3a3e88dff72706917f3729d55b3799
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769747"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="f02b7-103">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="f02b7-103">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>

<span data-ttu-id="f02b7-104">İleti taşınamıyor ya da silinemiyor.</span><span class="sxs-lookup"><span data-stu-id="f02b7-104">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f02b7-105">Description</span><span class="sxs-lookup"><span data-stu-id="f02b7-105">Description</span></span>  

 <span data-ttu-id="f02b7-106">İzleme, bir MSMQ iletisini taşımaya, silmeye veya reddetmeye çalışırken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f02b7-106">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="f02b7-107">MSMQ iletileri Windows Communication Foundation (WCF) tarafından (NetMsmqBinding veya MsmqIntegrationBinding ile kullanıldığında) tarafından kullanılır. Bu izleme, `ReceiveErrorHandling` NetMsmqBinding veya MsmqIntegrationBinding üzerinde özelliğin seçili değeri ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="f02b7-107">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="f02b7-108">Bu izleme, bir genel sistem hatasının göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="f02b7-108">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="f02b7-109">Ancak, seçilen zarar iletisi değerlendirmesi bir ileti için başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f02b7-109">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="f02b7-110">İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="f02b7-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f02b7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f02b7-111">See also</span></span>

- [<span data-ttu-id="f02b7-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="f02b7-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="f02b7-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="f02b7-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f02b7-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="f02b7-114">Administration and Diagnostics</span></span>](../index.md)
