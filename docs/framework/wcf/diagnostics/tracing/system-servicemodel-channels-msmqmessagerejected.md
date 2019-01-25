---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 87d6e6fc3205fff9bd977ebe77004dfa489098cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681228"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="c8693-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="c8693-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="c8693-103">İletinin MSMQ reddetti.</span><span class="sxs-lookup"><span data-stu-id="c8693-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c8693-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8693-104">Description</span></span>  
 <span data-ttu-id="c8693-105">Bu izleme, bir MSMQ iletisinin reddedildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8693-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="c8693-106">Windows Communication Foundation (WCF) (NetMsmqBinding veya MsmqIntegrationBinding ile kullanılır) bunları işleyemiyor olduğunda MSMQ iletileri reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="c8693-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="c8693-107">Bu türden iletilere zehirli ileti olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c8693-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="c8693-108">Zehirli ileti reddedilir olduğunda `ReceiveErrorHandling` özelliği NetMsmqBinding veya MsmqIntegrationBinding `Reject`.</span><span class="sxs-lookup"><span data-stu-id="c8693-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="c8693-109">Reddedilen ileti geri gönderen için teslim [eski ileti sırası](https://go.microsoft.com/fwlink/?LinkID=99544).</span><span class="sxs-lookup"><span data-stu-id="c8693-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="c8693-110">Bkz: [Poison ileti işleme](https://go.microsoft.com/fwlink/?LinkID=99546) iletileri zehirli duruma ne zaman ve uygun şekilde işlemek için hizmetinizi yapılandırmak nasıl daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="c8693-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="c8693-111">Bkz: [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) MSMQ reddedilen ileti ne anlama hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="c8693-111">See [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8693-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8693-112">See also</span></span>
- [<span data-ttu-id="c8693-113">İzleme</span><span class="sxs-lookup"><span data-stu-id="c8693-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="c8693-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="c8693-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c8693-115">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="c8693-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="c8693-116">Poison ileti işleme</span><span class="sxs-lookup"><span data-stu-id="c8693-116">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)
- [<span data-ttu-id="c8693-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="c8693-117">MQMarkMessageRejected</span></span>](https://go.microsoft.com/fwlink/?LinkID=99548)
