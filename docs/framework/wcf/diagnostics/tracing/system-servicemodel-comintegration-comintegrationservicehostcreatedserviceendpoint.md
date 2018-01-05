---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87eac8f0e3949ac47c7bb2915a87043bdc205b8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="156f3-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="156f3-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="156f3-103">Taşıyamaz veya ileti silemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="156f3-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="156f3-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="156f3-104">Description</span></span>  
 <span data-ttu-id="156f3-105">İzleme, bir hata taşımak, silmek veya bir MSMQ iletisi reddetme çalışılırken zaman oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="156f3-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="156f3-106">MSMQ iletileri tarafından işe [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (NetMsmqBinding veya MsmqIntegrationBinding ile kullanıldığında). Bu izleme için seçilen değeri ilgili `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği.</span><span class="sxs-lookup"><span data-stu-id="156f3-106">MSMQ messages are employed by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="156f3-107">Bu izleme genel bir sistem hatası göstergesi değil.</span><span class="sxs-lookup"><span data-stu-id="156f3-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="156f3-108">Ancak, seçilen bir ileti başarısız oldu ileti değerlendirme zehirli gösterir.</span><span class="sxs-lookup"><span data-stu-id="156f3-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="156f3-109">Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="156f3-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="156f3-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="156f3-110">See Also</span></span>  
 [<span data-ttu-id="156f3-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="156f3-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="156f3-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="156f3-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="156f3-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="156f3-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
