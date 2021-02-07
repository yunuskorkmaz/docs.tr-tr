---
description: ': System. ServiceModel. Channels. MsmqPoisonMessageRejected hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 856c28dd313867de0661d4950dd67e6740e2b338
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759308"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="9ff5f-103">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="9ff5f-103">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>

<span data-ttu-id="9ff5f-104">Zarar iletisi reddedildi.</span><span class="sxs-lookup"><span data-stu-id="9ff5f-104">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9ff5f-105">Description</span><span class="sxs-lookup"><span data-stu-id="9ff5f-105">Description</span></span>  

 <span data-ttu-id="9ff5f-106">İzleme, bir zarar iletisi ile karşılaşıldığını ve daha sonra reddedildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ff5f-106">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="9ff5f-107">Bu, `ReceiveErrorHandling` NetMsmqBinding veya MsmqIntegrationBinding üzerindeki özellik olarak ayarlandığında oluşur `Reject` .</span><span class="sxs-lookup"><span data-stu-id="9ff5f-107">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="9ff5f-108">Reddedilen bir ileti, gönderenin teslim [edilemeyen Ileti kuyruğuna](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9ff5f-108">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="9ff5f-109">İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="9ff5f-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="9ff5f-110">Reddedilen iletinin MSMQ 'da anlamı hakkında daha fazla bilgi için bkz. [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="9ff5f-110">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff5f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ff5f-111">See also</span></span>

- [<span data-ttu-id="9ff5f-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="9ff5f-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="9ff5f-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="9ff5f-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9ff5f-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="9ff5f-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="9ff5f-115">Zehirli Ileti Işleme</span><span class="sxs-lookup"><span data-stu-id="9ff5f-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="9ff5f-116">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="9ff5f-116">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
