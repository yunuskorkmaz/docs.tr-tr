---
description: ': System. ServiceModel. Channels. ConnectionPoolCloseException hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: a65739cc872f3cd175d76e9113380f9f4185d498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644638"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="984ed-103">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="984ed-103">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>

<span data-ttu-id="984ed-104">Bu bağlantı havuzundaki bağlantılar kapatılırken bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="984ed-104">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="984ed-105">Description</span><span class="sxs-lookup"><span data-stu-id="984ed-105">Description</span></span>  

 <span data-ttu-id="984ed-106">Bu hata düzeyi izleme, Windows Communication Foundation (WCF) bağlantı havuzu özelliği tarafından kullanılan bağlantı havuzlarını kapatırken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="984ed-106">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="984ed-107">Bunun olası bir nedeni, havuza alınmış bir bağlantının başarısız bir kapanışı veya CloseTimeout içindeki bir havuza alınmış bağlantı kümesidir.</span><span class="sxs-lookup"><span data-stu-id="984ed-107">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="984ed-108">Bu özel durum oluştuğunda, bu havuzun içindeki kalan kapatılmamış bağlantılar iptal edilir; diğer havuzların içindeki kapatılmamış bağlantılar bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="984ed-108">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="984ed-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="984ed-109">See also</span></span>

- [<span data-ttu-id="984ed-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="984ed-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="984ed-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="984ed-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="984ed-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="984ed-112">Administration and Diagnostics</span></span>](../index.md)
