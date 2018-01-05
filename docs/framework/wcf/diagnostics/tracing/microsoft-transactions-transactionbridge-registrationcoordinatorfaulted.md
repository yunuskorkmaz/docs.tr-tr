---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cf9f8a9fba43a915fd71e397c4aed54c8d95197
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="db7b0-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="db7b0-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>
<span data-ttu-id="db7b0-103">WS-AT protokolü hizmeti Koordinatörü kayıt iletisine yanıt olarak bir hata aldı.</span><span class="sxs-lookup"><span data-stu-id="db7b0-103">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="db7b0-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db7b0-104">Description</span></span>  
 <span data-ttu-id="db7b0-105">Yerel TransactionManager kendi üst TransactionManager döndürülen bir hata nedeniyle kaydı mümkün değilse, izlenen.</span><span class="sxs-lookup"><span data-stu-id="db7b0-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="db7b0-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="db7b0-106">Troubleshooting</span></span>  
 <span data-ttu-id="db7b0-107">Döndürülen hata izleme iletisi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="db7b0-107">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db7b0-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db7b0-108">See Also</span></span>  
 [<span data-ttu-id="db7b0-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="db7b0-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="db7b0-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="db7b0-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="db7b0-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="db7b0-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
