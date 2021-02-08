---
description: ': System. ServiceModel. Channels. MsmqMessageRejected hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 4400519c814627fd2a2f2585359d6d6376798ac0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780953"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="0fa80-103">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="0fa80-103">System.ServiceModel.Channels.MsmqMessageRejected</span></span>

<span data-ttu-id="0fa80-104">MSMQ iletiyi reddetti.</span><span class="sxs-lookup"><span data-stu-id="0fa80-104">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0fa80-105">Description</span><span class="sxs-lookup"><span data-stu-id="0fa80-105">Description</span></span>  

 <span data-ttu-id="0fa80-106">Bu izleme bir MSMQ iletisinin reddedildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0fa80-106">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="0fa80-107">Windows Communication Foundation (WCF) (NetMsmqBinding veya MsmqIntegrationBinding ile kullanılan) bunları işleyemediğinde MSMQ iletileri reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="0fa80-107">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="0fa80-108">Bu tür iletiler, zarar iletileri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0fa80-108">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="0fa80-109">`ReceiveErrorHandling`NetMsmqBinding veya MsmqIntegrationBinding üzerindeki özellik olarak ayarlandığında bir zarar iletisi reddedilir `Reject` .</span><span class="sxs-lookup"><span data-stu-id="0fa80-109">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="0fa80-110">Reddedilen bir ileti, gönderenin teslim [edilemeyen Ileti kuyruğuna](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0fa80-110">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="0fa80-111">İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="0fa80-111">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="0fa80-112">Reddedilen iletinin MSMQ 'da anlamı hakkında daha fazla bilgi için bkz. [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="0fa80-112">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fa80-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fa80-113">See also</span></span>

- [<span data-ttu-id="0fa80-114">İzleme</span><span class="sxs-lookup"><span data-stu-id="0fa80-114">Tracing</span></span>](index.md)
- [<span data-ttu-id="0fa80-115">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="0fa80-115">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0fa80-116">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="0fa80-116">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="0fa80-117">Zehirli Ileti Işleme</span><span class="sxs-lookup"><span data-stu-id="0fa80-117">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="0fa80-118">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="0fa80-118">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
