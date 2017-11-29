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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e50e104816567927f53673f9b1da9c3c5beac3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="3d767-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="3d767-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="3d767-103">Havuza alınmış bir bağlantıyı yeniden kullanma girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="3d767-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="3d767-104">Belirtilen zaman aşımı süresi içinde başka bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="3d767-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3d767-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d767-105">Description</span></span>  
 <span data-ttu-id="3d767-106">Bu bilgi izleme havuza alınmış bir bağlantıyı yeniden kullanma girişimi sırasında bir hata oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d767-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="3d767-107">Havuza alınmış bağlantı uyumlu, hazır veya hala etkin değil olduğundan bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="3d767-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="3d767-108">Belirli bir zaman aşımı süresi içinde yapılan ek diğer havuza alınan bir bağlantıyı yeniden dener ve kullanılabilir bağlantı bulunamıyor durumda yeni bir bağlantı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3d767-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d767-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d767-109">See Also</span></span>  
 [<span data-ttu-id="3d767-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="3d767-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="3d767-111">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="3d767-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="3d767-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="3d767-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
