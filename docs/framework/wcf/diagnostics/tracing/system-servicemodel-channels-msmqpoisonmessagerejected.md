---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 6b0e6e3ebcf5d414e9dbbcecd09ba2e8bb3ddd3a
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674810"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="a9435-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="a9435-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="a9435-103">Zehirli ileti reddedildi.</span><span class="sxs-lookup"><span data-stu-id="a9435-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a9435-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9435-104">Description</span></span>  

 <span data-ttu-id="a9435-105">İz, zehirli bir iletiyle karşılaşıldığını ve daha sonra reddedildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9435-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="a9435-106">Bu, NetMsmqBinding veya MsmqIntegrationBinding'deki `ReceiveErrorHandling` özellik . `Reject`</span><span class="sxs-lookup"><span data-stu-id="a9435-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="a9435-107">Reddedilen ileti gönderenin [Ölü Harf Kuyruğuna](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)geri teslim edilir.</span><span class="sxs-lookup"><span data-stu-id="a9435-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="a9435-108">İletilerin ne zaman zehirhaline geldiği ve hizmetinizi uygun şekilde işlemek üzere nasıl yapılandırılacağı hakkında daha fazla bilgi için [Poison-Message Handling](../../feature-details/poison-message-handling.md)'e bakın.</span><span class="sxs-lookup"><span data-stu-id="a9435-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="a9435-109">Reddedilen iletinin MSMQ'da ne anlama geldiğini hakkında daha fazla bilgi [için](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))bkz.</span><span class="sxs-lookup"><span data-stu-id="a9435-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9435-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9435-110">See also</span></span>

- [<span data-ttu-id="a9435-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="a9435-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="a9435-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="a9435-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a9435-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="a9435-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="a9435-114">Zehir-Mesaj Taşıma</span><span class="sxs-lookup"><span data-stu-id="a9435-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="a9435-115">[MQMarkMessageReddedildi](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="a9435-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
