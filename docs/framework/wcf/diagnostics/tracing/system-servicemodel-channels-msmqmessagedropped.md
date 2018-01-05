---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2f905c345db89e909920334a7dbb524095bc46b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="4b1b1-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="4b1b1-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="4b1b1-103">MSMQ İleti bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="4b1b1-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4b1b1-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b1b1-104">Description</span></span>  
 <span data-ttu-id="4b1b1-105">İzleme, bir MSMQ İleti bırakıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b1b1-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="4b1b1-106">MSMQ iletileri bırakılan ne zaman [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (NetMsmqBinding ya da MsmqIntegrationBinding ile kullanılır) bunları işleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="4b1b1-106">MSMQ messages can be dropped when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="4b1b1-107">Bu türden iletilere zarar iletileri adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4b1b1-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="4b1b1-108">Zararlı bir ileti olduğunda bırakılan `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği ayarlanmış `Drop`.</span><span class="sxs-lookup"><span data-stu-id="4b1b1-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="4b1b1-109">Bırakılan ileti kuyruktan kaldırılır ve artık kurtarılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b1b1-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="4b1b1-110">Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="4b1b1-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b1b1-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b1b1-111">See Also</span></span>  
 [<span data-ttu-id="4b1b1-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="4b1b1-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="4b1b1-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="4b1b1-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="4b1b1-114">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="4b1b1-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="4b1b1-115">Poison ileti işleme</span><span class="sxs-lookup"><span data-stu-id="4b1b1-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
