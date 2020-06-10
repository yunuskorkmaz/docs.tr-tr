---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 5bfa31d0eaf3b00017512eddc60bfa99eda619e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84582588"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="dd64c-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="dd64c-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="dd64c-103">Havuza alınmış bir bağlantıyı yeniden kullanma girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="dd64c-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="dd64c-104">Belirtilen zaman aşımı süresi içinde başka bir girişim yapılır.</span><span class="sxs-lookup"><span data-stu-id="dd64c-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dd64c-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd64c-105">Description</span></span>  
 <span data-ttu-id="dd64c-106">Bu bilgi izleme, havuza alınmış bir bağlantıyı yeniden kullanmaya çalışırken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd64c-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="dd64c-107">Bu durum, havuza alınmış bağlantının uyumlu, Ready veya hala etkin olmadığı için meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="dd64c-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="dd64c-108">Diğer havuza alınmış bağlantıyı yeniden kullanma girişimleri belirli bir zaman aşımı içinde yapılır ve kullanılabilir bağlantı bulunamaması durumunda yeni bir bağlantı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dd64c-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd64c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd64c-109">See also</span></span>

- [<span data-ttu-id="dd64c-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="dd64c-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="dd64c-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="dd64c-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="dd64c-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="dd64c-112">Administration and Diagnostics</span></span>](../index.md)
