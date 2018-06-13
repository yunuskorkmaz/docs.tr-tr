---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: ad05a2b8552cc09d45e950e2c3336d86be918963
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33479137"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="ed6c6-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="ed6c6-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="ed6c6-103">MSMQ İleti bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ed6c6-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ed6c6-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed6c6-104">Description</span></span>  
 <span data-ttu-id="ed6c6-105">İzleme, bir MSMQ İleti bırakıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed6c6-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="ed6c6-106">Windows Communication Foundation (WCF) (NetMsmqBinding ya da MsmqIntegrationBinding ile kullanılır) işlemek başlatılamadığında MSMQ iletileri bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed6c6-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="ed6c6-107">Bu türden iletilere zarar iletileri adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ed6c6-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="ed6c6-108">Zararlı bir ileti olduğunda bırakılan `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği ayarlanmış `Drop`.</span><span class="sxs-lookup"><span data-stu-id="ed6c6-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="ed6c6-109">Bırakılan ileti kuyruktan kaldırılır ve artık kurtarılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed6c6-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="ed6c6-110">Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="ed6c6-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed6c6-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed6c6-111">See Also</span></span>  
 [<span data-ttu-id="ed6c6-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="ed6c6-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ed6c6-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="ed6c6-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ed6c6-114">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="ed6c6-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="ed6c6-115">Poison ileti işleme</span><span class="sxs-lookup"><span data-stu-id="ed6c6-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
