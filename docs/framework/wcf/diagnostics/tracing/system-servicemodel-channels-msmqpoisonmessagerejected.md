---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: c5401bae1d8e7f61939d8de321353f59f412f966
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535339"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="d6ddc-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="d6ddc-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="d6ddc-103">Zarar iletisi reddedildi.</span><span class="sxs-lookup"><span data-stu-id="d6ddc-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d6ddc-104">Description</span><span class="sxs-lookup"><span data-stu-id="d6ddc-104">Description</span></span>  

 <span data-ttu-id="d6ddc-105">İzleme, bir zarar iletisi ile karşılaşıldığını ve daha sonra reddedildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6ddc-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="d6ddc-106">Bu, `ReceiveErrorHandling` NetMsmqBinding veya MsmqIntegrationBinding üzerindeki özellik olarak ayarlandığında oluşur `Reject` .</span><span class="sxs-lookup"><span data-stu-id="d6ddc-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="d6ddc-107">Reddedilen bir ileti, gönderenin teslim [edilemeyen Ileti kuyruğuna](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="d6ddc-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="d6ddc-108">İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="d6ddc-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="d6ddc-109">Reddedilen iletinin MSMQ 'da anlamı hakkında daha fazla bilgi için bkz. [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="d6ddc-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ddc-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6ddc-110">See also</span></span>

- [<span data-ttu-id="d6ddc-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="d6ddc-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="d6ddc-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="d6ddc-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d6ddc-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="d6ddc-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="d6ddc-114">Zehirli Ileti Işleme</span><span class="sxs-lookup"><span data-stu-id="d6ddc-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="d6ddc-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d6ddc-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
