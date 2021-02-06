---
description: ': System. ServiceModel. Channels. FailedAcceptFromPool hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 1b3c15594611726fd4872197b97ad4ed56c085c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635265"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="d724e-103">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="d724e-103">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>

<span data-ttu-id="d724e-104">Havuza alınmış bir bağlantıyı yeniden kullanma girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="d724e-104">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="d724e-105">Belirtilen zaman aşımı süresi içinde başka bir girişim yapılır.</span><span class="sxs-lookup"><span data-stu-id="d724e-105">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d724e-106">Description</span><span class="sxs-lookup"><span data-stu-id="d724e-106">Description</span></span>  

 <span data-ttu-id="d724e-107">Bu bilgi izleme, havuza alınmış bir bağlantıyı yeniden kullanmaya çalışırken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d724e-107">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="d724e-108">Bu durum, havuza alınmış bağlantının uyumlu, Ready veya hala etkin olmadığı için meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="d724e-108">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="d724e-109">Diğer havuza alınmış bağlantıyı yeniden kullanma girişimleri belirli bir zaman aşımı içinde yapılır ve kullanılabilir bağlantı bulunamaması durumunda yeni bir bağlantı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d724e-109">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d724e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d724e-110">See also</span></span>

- [<span data-ttu-id="d724e-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="d724e-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="d724e-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="d724e-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d724e-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="d724e-113">Administration and Diagnostics</span></span>](../index.md)
