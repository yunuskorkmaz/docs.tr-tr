---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: e602dd7da2a5652ec10e74fa05c73b75afec2ed4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551997"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="1519f-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="1519f-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="1519f-103">MSMQ iletiyi reddetti.</span><span class="sxs-lookup"><span data-stu-id="1519f-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1519f-104">Description</span><span class="sxs-lookup"><span data-stu-id="1519f-104">Description</span></span>  
 <span data-ttu-id="1519f-105">Bu izleme bir MSMQ iletisinin reddedildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1519f-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="1519f-106">Windows Communication Foundation (WCF) (NetMsmqBinding veya MsmqIntegrationBinding ile kullanılan) bunları işleyemediğinde MSMQ iletileri reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="1519f-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="1519f-107">Bu tür iletiler, zarar iletileri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1519f-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="1519f-108">`ReceiveErrorHandling`NetMsmqBinding veya MsmqIntegrationBinding üzerindeki özellik olarak ayarlandığında bir zarar iletisi reddedilir `Reject` .</span><span class="sxs-lookup"><span data-stu-id="1519f-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="1519f-109">Reddedilen bir ileti, gönderenin teslim [edilemeyen Ileti kuyruğuna](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="1519f-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="1519f-110">İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="1519f-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="1519f-111">Reddedilen iletinin MSMQ 'da anlamı hakkında daha fazla bilgi için bkz. [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1519f-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1519f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1519f-112">See also</span></span>

- [<span data-ttu-id="1519f-113">İzleme</span><span class="sxs-lookup"><span data-stu-id="1519f-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="1519f-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="1519f-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1519f-115">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="1519f-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="1519f-116">Zehirli Ileti Işleme</span><span class="sxs-lookup"><span data-stu-id="1519f-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="1519f-117">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1519f-117">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
