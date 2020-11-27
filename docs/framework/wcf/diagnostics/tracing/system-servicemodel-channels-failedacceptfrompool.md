---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 8615cca7d4ed8ea1f40baa9502e7136d4349eb9c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256319"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="18435-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="18435-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>

<span data-ttu-id="18435-103">Havuza alınmış bir bağlantıyı yeniden kullanma girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="18435-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="18435-104">Belirtilen zaman aşımı süresi içinde başka bir girişim yapılır.</span><span class="sxs-lookup"><span data-stu-id="18435-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="18435-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18435-105">Description</span></span>  

 <span data-ttu-id="18435-106">Bu bilgi izleme, havuza alınmış bir bağlantıyı yeniden kullanmaya çalışırken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="18435-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="18435-107">Bu durum, havuza alınmış bağlantının uyumlu, Ready veya hala etkin olmadığı için meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="18435-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="18435-108">Diğer havuza alınmış bağlantıyı yeniden kullanma girişimleri belirli bir zaman aşımı içinde yapılır ve kullanılabilir bağlantı bulunamaması durumunda yeni bir bağlantı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="18435-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18435-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18435-109">See also</span></span>

- [<span data-ttu-id="18435-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="18435-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="18435-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="18435-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="18435-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="18435-112">Administration and Diagnostics</span></span>](../index.md)
