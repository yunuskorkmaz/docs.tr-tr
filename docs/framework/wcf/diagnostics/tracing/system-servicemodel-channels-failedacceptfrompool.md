---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 59bba87095931c80a7ce347def2656a7a1f6f949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33479325"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="90f82-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="90f82-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="90f82-103">Havuza alınmış bir bağlantıyı yeniden kullanma girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="90f82-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="90f82-104">Belirtilen zaman aşımı süresi içinde başka bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="90f82-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="90f82-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90f82-105">Description</span></span>  
 <span data-ttu-id="90f82-106">Bu bilgi izleme havuza alınmış bir bağlantıyı yeniden kullanma girişimi sırasında bir hata oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="90f82-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="90f82-107">Havuza alınmış bağlantı uyumlu, hazır veya hala etkin değil olduğundan bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="90f82-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="90f82-108">Belirli bir zaman aşımı süresi içinde yapılan ek diğer havuza alınan bir bağlantıyı yeniden dener ve kullanılabilir bağlantı bulunamıyor durumda yeni bir bağlantı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="90f82-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f82-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="90f82-109">See Also</span></span>  
 [<span data-ttu-id="90f82-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="90f82-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="90f82-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="90f82-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="90f82-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="90f82-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
