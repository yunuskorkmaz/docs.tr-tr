---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df0f983d646ea89eeef338b9742843e9fa50487b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="657a8-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="657a8-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="657a8-103">Havuza alınmış bir bağlantıyı yeniden kullanma girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="657a8-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="657a8-104">Belirtilen zaman aşımı süresi içinde başka bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="657a8-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="657a8-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="657a8-105">Description</span></span>  
 <span data-ttu-id="657a8-106">Bu bilgi izleme havuza alınmış bir bağlantıyı yeniden kullanma girişimi sırasında bir hata oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="657a8-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="657a8-107">Havuza alınmış bağlantı uyumlu, hazır veya hala etkin değil olduğundan bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="657a8-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="657a8-108">Belirli bir zaman aşımı süresi içinde yapılan ek diğer havuza alınan bir bağlantıyı yeniden dener ve kullanılabilir bağlantı bulunamıyor durumda yeni bir bağlantı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="657a8-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="657a8-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="657a8-109">See Also</span></span>  
 [<span data-ttu-id="657a8-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="657a8-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="657a8-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="657a8-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="657a8-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="657a8-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
