---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: c8e476ab90fda9214831fbd5beaba518f3e3bd20
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491434"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="83129-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="83129-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="83129-103">Zehirli ileti reddedildi.</span><span class="sxs-lookup"><span data-stu-id="83129-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="83129-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83129-104">Description</span></span>  
 <span data-ttu-id="83129-105">İzleme, zehirli ileti karşılaştı ve daha sonra reddedildiği olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="83129-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="83129-106">Böyle durumlarda `ReceiveErrorHandling` özelliği NetMsmqBinding veya MsmqIntegrationBinding `Reject`.</span><span class="sxs-lookup"><span data-stu-id="83129-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="83129-107">Reddedilen ileti geri gönderen için teslim [eski ileti sırası](https://go.microsoft.com/fwlink/?LinkId=99544).</span><span class="sxs-lookup"><span data-stu-id="83129-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="83129-108">Bkz: [Poison ileti işleme](https://go.microsoft.com/fwlink/?LinkId=99546) iletileri zehirli duruma ne zaman ve uygun şekilde işlemek için hizmetinizi yapılandırmak nasıl daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="83129-108">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="83129-109">Bkz: [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) MSMQ reddedilen ileti ne anlama hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="83129-109">See [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83129-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83129-110">See also</span></span>
- [<span data-ttu-id="83129-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="83129-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="83129-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="83129-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="83129-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="83129-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="83129-114">Poison ileti işleme</span><span class="sxs-lookup"><span data-stu-id="83129-114">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkId=99546)
- [<span data-ttu-id="83129-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="83129-115">MQMarkMessageRejected</span></span>](https://go.microsoft.com/fwlink/?LinkId=99548)
