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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4cecacdcc9ec1155fbb374bb763f6858da6ccc57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="c8a21-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="c8a21-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="c8a21-103">Taşıyamaz veya ileti silemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8a21-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c8a21-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8a21-104">Description</span></span>  
 <span data-ttu-id="c8a21-105">İzleme, bir hata taşımak, silmek veya bir MSMQ iletisi reddetme çalışılırken zaman oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8a21-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="c8a21-106">MSMQ iletileri tarafından işe [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (NetMsmqBinding veya MsmqIntegrationBinding ile kullanıldığında). Bu izleme için seçilen değeri ilgili `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği.</span><span class="sxs-lookup"><span data-stu-id="c8a21-106">MSMQ messages are employed by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="c8a21-107">Bu izleme genel bir sistem hatası göstergesi değil.</span><span class="sxs-lookup"><span data-stu-id="c8a21-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="c8a21-108">Ancak, seçilen bir ileti başarısız oldu ileti değerlendirme zehirli gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8a21-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="c8a21-109">Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="c8a21-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a21-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8a21-110">See Also</span></span>  
 [<span data-ttu-id="c8a21-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="c8a21-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c8a21-112">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="c8a21-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c8a21-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="c8a21-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
