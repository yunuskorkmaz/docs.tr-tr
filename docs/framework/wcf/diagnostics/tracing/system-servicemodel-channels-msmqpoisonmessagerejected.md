---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 69da35f65e04a3cba15885c4fe6e57d63762cb1c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260350"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="4a8a6-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="4a8a6-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>

<span data-ttu-id="4a8a6-103">Zarar iletisi reddedildi.</span><span class="sxs-lookup"><span data-stu-id="4a8a6-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4a8a6-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a8a6-104">Description</span></span>  

 <span data-ttu-id="4a8a6-105">İzleme, bir zarar iletisi ile karşılaşıldığını ve daha sonra reddedildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a8a6-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="4a8a6-106">Bu, `ReceiveErrorHandling` NetMsmqBinding veya MsmqIntegrationBinding üzerindeki özellik olarak ayarlandığında oluşur `Reject` .</span><span class="sxs-lookup"><span data-stu-id="4a8a6-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="4a8a6-107">Reddedilen bir ileti, gönderenin teslim [edilemeyen Ileti kuyruğuna](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="4a8a6-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="4a8a6-108">İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="4a8a6-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="4a8a6-109">Reddedilen iletinin MSMQ 'da anlamı hakkında daha fazla bilgi için bkz. [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="4a8a6-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a8a6-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a8a6-110">See also</span></span>

- [<span data-ttu-id="4a8a6-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="4a8a6-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="4a8a6-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="4a8a6-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4a8a6-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="4a8a6-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="4a8a6-114">Zehirli Ileti Işleme</span><span class="sxs-lookup"><span data-stu-id="4a8a6-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="4a8a6-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4a8a6-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
