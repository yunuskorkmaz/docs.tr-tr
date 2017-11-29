---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0ea98388efe14ac0d18a94ec056a441096a4d7c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="c747e-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="c747e-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="c747e-103">Bu bağlantı havuzundaki bağlantılar kapatılırken bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="c747e-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c747e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c747e-104">Description</span></span>  
 <span data-ttu-id="c747e-105">Bu hata düzeyi izleme tarafından kullanılan bağlantı havuzu kapatılırken bir hata oluştu gösterir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]kullanıcının bağlantı havuzu özelliği.</span><span class="sxs-lookup"><span data-stu-id="c747e-105">This error level trace indicates that an error has occurred while closing the connection pools used by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]’s connection pooling feature.</span></span> <span data-ttu-id="c747e-106">Havuza alınmış bağlantısının başarısız bir kapatma veya havuza alınan bağlantıları CloseTimeout içinde kümesi bu olası nedenlerden biri.</span><span class="sxs-lookup"><span data-stu-id="c747e-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="c747e-107">Bu durum, aynı havuz içindeki kalan tüm kapatılmamış bağlantıları iptal edilir; diğer havuzlardaki kapatılmamış bağlantıları terk.</span><span class="sxs-lookup"><span data-stu-id="c747e-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c747e-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c747e-108">See Also</span></span>  
 [<span data-ttu-id="c747e-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="c747e-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c747e-110">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="c747e-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c747e-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="c747e-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
