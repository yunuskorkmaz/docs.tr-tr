---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: de0bdd9e5ab922b09249bf550fde745042be8e58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156487"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="9644f-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="9644f-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="9644f-103">Havuza alınmış bir bağlantıyı yeniden kullanma girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="9644f-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="9644f-104">Belirtilen zaman aşımı süresi içinde başka bir girişimde bulunulmaz.</span><span class="sxs-lookup"><span data-stu-id="9644f-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9644f-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9644f-105">Description</span></span>  
 <span data-ttu-id="9644f-106">Bu bilgilendirici izleme, havuza alınmış bir bağlantıyı yeniden çalışılırken bir hata oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9644f-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="9644f-107">Havuza alınmış bağlantı değil uyumlu, hazır ve hala etkin olduğu için bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="9644f-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="9644f-108">Belirli bir zaman aşımı süresi içinde yapılan ek diğer havuza alınmış bağlantıyı yeniden dener ve kullanılabilir bağlantı yok bulunan durumda yeni bir bağlantı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9644f-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9644f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9644f-109">See also</span></span>

- [<span data-ttu-id="9644f-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="9644f-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="9644f-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="9644f-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9644f-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="9644f-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
