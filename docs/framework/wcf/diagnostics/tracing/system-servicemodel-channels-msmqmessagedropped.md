---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 07bef8b391a03f2c011e1d1a7c7fb4fad908e022
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44067811"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="bbd63-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="bbd63-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="bbd63-103">İletinin MSMQ bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="bbd63-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bbd63-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbd63-104">Description</span></span>  
 <span data-ttu-id="bbd63-105">İzleme, bir MSMQ iletisinin bırakıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbd63-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="bbd63-106">Windows Communication Foundation (WCF) (NetMsmqBinding veya MsmqIntegrationBinding ile kullanılır) bunları işleyemiyor olduğunda MSMQ iletileri bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbd63-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="bbd63-107">Bu türden iletilere zehirli ileti olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="bbd63-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="bbd63-108">Zehirli ileti ne zaman bırakılan `ReceiveErrorHandling` özelliği NetMsmqBinding veya MsmqIntegrationBinding `Drop`.</span><span class="sxs-lookup"><span data-stu-id="bbd63-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="bbd63-109">Bırakılan ileti kuyruktan kaldırılır ve artık kurtarılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbd63-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="bbd63-110">Bkz: [Poison ileti işleme](https://go.microsoft.com/fwlink/?LinkID=99546) iletileri zehirli duruma ne zaman ve uygun şekilde işlemek için hizmetinizi yapılandırmak nasıl daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="bbd63-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd63-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bbd63-111">See Also</span></span>  
 [<span data-ttu-id="bbd63-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="bbd63-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="bbd63-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="bbd63-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="bbd63-114">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="bbd63-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="bbd63-115">Poison ileti işleme</span><span class="sxs-lookup"><span data-stu-id="bbd63-115">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)
