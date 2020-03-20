---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674767"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="d4776-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="d4776-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="d4776-103">MSMQ iletiyi reddetti.</span><span class="sxs-lookup"><span data-stu-id="d4776-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d4776-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4776-104">Description</span></span>  
 <span data-ttu-id="d4776-105">Bu izleme, bir MSMQ iletisi reddedildi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4776-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="d4776-106">MSMQ iletileri, Windows Communication Foundation (WCF) (NetMsmqBinding veya MsmqIntegrationBinding ile birlikte kullanılır) bunları işleyemediğinde reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4776-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="d4776-107">Bu tür iletilere zehirli iletiler denir.</span><span class="sxs-lookup"><span data-stu-id="d4776-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="d4776-108">NetMsmqBinding veya `ReceiveErrorHandling` MsmqIntegrationBinding'deki özellik `Reject`.</span><span class="sxs-lookup"><span data-stu-id="d4776-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="d4776-109">Reddedilen ileti gönderenin [Ölü Harf Kuyruğuna](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)geri teslim edilir.</span><span class="sxs-lookup"><span data-stu-id="d4776-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="d4776-110">İletilerin ne zaman zehirhaline geldiği ve hizmetinizi uygun şekilde işlemek üzere nasıl yapılandırılacağı hakkında daha fazla bilgi için [Poison-Message Handling](../../feature-details/poison-message-handling.md)'e bakın.</span><span class="sxs-lookup"><span data-stu-id="d4776-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="d4776-111">Reddedilen iletinin MSMQ'da ne anlama geldiğini hakkında daha fazla bilgi [için](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))bkz.</span><span class="sxs-lookup"><span data-stu-id="d4776-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4776-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4776-112">See also</span></span>

- [<span data-ttu-id="d4776-113">İzleme</span><span class="sxs-lookup"><span data-stu-id="d4776-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="d4776-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="d4776-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d4776-115">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="d4776-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="d4776-116">Zehir-Mesaj Taşıma</span><span class="sxs-lookup"><span data-stu-id="d4776-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="d4776-117">[MQMarkMessageReddedildi](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="d4776-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
