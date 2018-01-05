---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b433e5e3c0a961098f82ad601d127290b1d6bd73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="d270e-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="d270e-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="d270e-103">MSMQ İleti reddedildi.</span><span class="sxs-lookup"><span data-stu-id="d270e-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d270e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d270e-104">Description</span></span>  
 <span data-ttu-id="d270e-105">Bu izleme, bir MSMQ İleti reddedildi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d270e-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="d270e-106">MSMQ iletileri olabilir ne zaman reddedilen [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (NetMsmqBinding ya da MsmqIntegrationBinding ile kullanılır) bunları işleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="d270e-106">MSMQ messages can be rejected when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="d270e-107">Bu türden iletilere zarar iletileri adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d270e-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="d270e-108">Zararlı bir ileti reddedildi zaman `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği ayarlanmış `Reject`.</span><span class="sxs-lookup"><span data-stu-id="d270e-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="d270e-109">Reddedilen ileti geri gönderen için teslim [sahipsiz sırayı](http://go.microsoft.com/fwlink/?LinkID=99544).</span><span class="sxs-lookup"><span data-stu-id="d270e-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="d270e-110">Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="d270e-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="d270e-111">Bkz: [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) MSMQ reddedilen ileti anlamı hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="d270e-111">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d270e-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d270e-112">See Also</span></span>  
 [<span data-ttu-id="d270e-113">İzleme</span><span class="sxs-lookup"><span data-stu-id="d270e-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="d270e-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="d270e-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="d270e-115">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="d270e-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="d270e-116">Poison ileti işleme</span><span class="sxs-lookup"><span data-stu-id="d270e-116">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [<span data-ttu-id="d270e-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="d270e-117">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkID=99548)
