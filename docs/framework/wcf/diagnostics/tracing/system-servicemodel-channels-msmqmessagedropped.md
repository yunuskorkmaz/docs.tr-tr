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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55b489bcad85eff5adba16f6f40493c88e476505
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="68975-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="68975-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="68975-103">MSMQ İleti bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="68975-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="68975-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68975-104">Description</span></span>  
 <span data-ttu-id="68975-105">İzleme, bir MSMQ İleti bırakıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="68975-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="68975-106">MSMQ iletileri bırakılan ne zaman [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (NetMsmqBinding ya da MsmqIntegrationBinding ile kullanılır) bunları işleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="68975-106">MSMQ messages can be dropped when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="68975-107">Bu türden iletilere zarar iletileri adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="68975-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="68975-108">Zararlı bir ileti olduğunda bırakılan `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği ayarlanmış `Drop`.</span><span class="sxs-lookup"><span data-stu-id="68975-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="68975-109">Bırakılan ileti kuyruktan kaldırılır ve artık kurtarılabilir.</span><span class="sxs-lookup"><span data-stu-id="68975-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="68975-110">Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="68975-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68975-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68975-111">See Also</span></span>  
 [<span data-ttu-id="68975-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="68975-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="68975-113">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="68975-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="68975-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="68975-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="68975-115">Poison ileti işleme</span><span class="sxs-lookup"><span data-stu-id="68975-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
