---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 3dd28276cd3a39497c0387f5b9d0adec23d07c37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182201"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="ce6ab-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="ce6ab-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="ce6ab-103">Bu bağlantı havuzundaki bağlantı kapatılırken bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ce6ab-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce6ab-104">Description</span></span>  
 <span data-ttu-id="ce6ab-105">Bu hata düzeyi izleme özelliğini Windows Communication Foundation (WCF) ait bağlantı tarafından kullanılan bağlantı havuzları kapatılırken bir hata oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="ce6ab-106">Bunun olası bir nedeni, havuza alınmış bir bağlantının başarısız bir kapanış veya havuza alınmış bağlantıları CloseTimeout içinde bir dizi ' dir.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="ce6ab-107">Bu özel durum oluştuğunda, bu havuz içindeki kalan tüm kapatılmamış bağlantıları iptal edilir; içindeki diğer havuzlara kapatılmamış bağlantılar yayını bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce6ab-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-108">See also</span></span>

- [<span data-ttu-id="ce6ab-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="ce6ab-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="ce6ab-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="ce6ab-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ce6ab-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="ce6ab-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
