---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: f3474fc1bb0ed0d11df6289ed6470447d815f5ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475757"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="16d61-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="16d61-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="16d61-103">Bu bağlantı havuzundaki bağlantılar kapatılırken bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="16d61-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="16d61-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16d61-104">Description</span></span>  
 <span data-ttu-id="16d61-105">Bu hata düzeyi izleme özelliğini Windows Communication Foundation (WCF) ait bağlantı tarafından kullanılan bağlantı havuzu kapatılırken bir hata oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="16d61-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="16d61-106">Havuza alınmış bağlantısının başarısız bir kapatma veya havuza alınan bağlantıları CloseTimeout içinde kümesi bu olası nedenlerden biri.</span><span class="sxs-lookup"><span data-stu-id="16d61-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="16d61-107">Bu durum, aynı havuz içindeki kalan tüm kapatılmamış bağlantıları iptal edilir; diğer havuzlardaki kapatılmamış bağlantıları terk.</span><span class="sxs-lookup"><span data-stu-id="16d61-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16d61-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16d61-108">See Also</span></span>  
 [<span data-ttu-id="16d61-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="16d61-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="16d61-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="16d61-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="16d61-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="16d61-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
