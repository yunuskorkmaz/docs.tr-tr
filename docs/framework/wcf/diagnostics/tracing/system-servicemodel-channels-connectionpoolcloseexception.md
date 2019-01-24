---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: b2d49910ecbcd67beca83e2fbeabfbcafe6e1dd0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628038"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="df131-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="df131-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="df131-103">Bu bağlantı havuzundaki bağlantı kapatılırken bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="df131-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="df131-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df131-104">Description</span></span>  
 <span data-ttu-id="df131-105">Bu hata düzeyi izleme özelliğini Windows Communication Foundation (WCF) ait bağlantı tarafından kullanılan bağlantı havuzları kapatılırken bir hata oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="df131-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="df131-106">Bunun olası bir nedeni, havuza alınmış bir bağlantının başarısız bir kapanış veya havuza alınmış bağlantıları CloseTimeout içinde bir dizi ' dir.</span><span class="sxs-lookup"><span data-stu-id="df131-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="df131-107">Bu özel durum oluştuğunda, bu havuz içindeki kalan tüm kapatılmamış bağlantıları iptal edilir; içindeki diğer havuzlara kapatılmamış bağlantılar yayını bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="df131-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df131-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df131-108">See also</span></span>
- [<span data-ttu-id="df131-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="df131-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="df131-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="df131-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="df131-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="df131-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
