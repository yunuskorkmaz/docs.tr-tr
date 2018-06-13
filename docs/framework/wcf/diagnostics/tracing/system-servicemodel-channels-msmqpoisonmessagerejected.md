---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 7dc1e4120caae7c4a592067f5e77ed4f56e82e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33478172"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="1966e-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="1966e-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="1966e-103">Zehirli ileti reddedildi.</span><span class="sxs-lookup"><span data-stu-id="1966e-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1966e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1966e-104">Description</span></span>  
 <span data-ttu-id="1966e-105">İzleme zararlı bir ileti karşılaştı ve daha sonra reddedildiği olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1966e-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="1966e-106">Bu meydana zaman `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği ayarlanmış `Reject`.</span><span class="sxs-lookup"><span data-stu-id="1966e-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="1966e-107">Reddedilen ileti geri gönderen için teslim [sahipsiz sırayı](http://go.microsoft.com/fwlink/?LinkId=99544).</span><span class="sxs-lookup"><span data-stu-id="1966e-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="1966e-108">Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkId=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="1966e-108">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="1966e-109">Bkz: [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) MSMQ reddedilen ileti anlamı hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="1966e-109">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1966e-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1966e-110">See Also</span></span>  
 [<span data-ttu-id="1966e-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="1966e-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1966e-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="1966e-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1966e-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="1966e-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="1966e-114">Poison ileti işleme</span><span class="sxs-lookup"><span data-stu-id="1966e-114">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="1966e-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="1966e-115">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkId=99548)
