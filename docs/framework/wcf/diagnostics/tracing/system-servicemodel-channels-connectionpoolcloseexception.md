---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: d8edb8e916578247e62e3a3eb3b11b80f93416cd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286961"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="17963-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="17963-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>

<span data-ttu-id="17963-103">Bu bağlantı havuzundaki bağlantılar kapatılırken bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="17963-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="17963-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17963-104">Description</span></span>  

 <span data-ttu-id="17963-105">Bu hata düzeyi izleme, Windows Communication Foundation (WCF) bağlantı havuzu özelliği tarafından kullanılan bağlantı havuzlarını kapatırken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="17963-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="17963-106">Bunun olası bir nedeni, havuza alınmış bir bağlantının başarısız bir kapanışı veya CloseTimeout içindeki bir havuza alınmış bağlantı kümesidir.</span><span class="sxs-lookup"><span data-stu-id="17963-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="17963-107">Bu özel durum oluştuğunda, bu havuzun içindeki kalan kapatılmamış bağlantılar iptal edilir; diğer havuzların içindeki kapatılmamış bağlantılar bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="17963-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17963-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17963-108">See also</span></span>

- [<span data-ttu-id="17963-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="17963-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="17963-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="17963-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="17963-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="17963-111">Administration and Diagnostics</span></span>](../index.md)
