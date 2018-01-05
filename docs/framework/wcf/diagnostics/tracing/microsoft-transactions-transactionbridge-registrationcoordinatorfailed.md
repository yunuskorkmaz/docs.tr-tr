---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 583aa5685ee3da768bea06333b90817d5e17e838
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="43c2e-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="43c2e-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>
<span data-ttu-id="43c2e-103">WS-AT protokolü hizmeti ilgili düzenleyiciye bir kayıt iletisi gönderilemedi</span><span class="sxs-lookup"><span data-stu-id="43c2e-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="43c2e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43c2e-104">Description</span></span>  
 <span data-ttu-id="43c2e-105">Yerel TransactionManager kendi üst TransactionManager nedeniyle bir ileti göndermek için kullanamama kaydı mümkün değilse, izlenen.</span><span class="sxs-lookup"><span data-stu-id="43c2e-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="43c2e-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="43c2e-106">Troubleshooting</span></span>  
 <span data-ttu-id="43c2e-107">İleti gönderme hataya neden olan özel durum izleme iletisi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="43c2e-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c2e-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43c2e-108">See Also</span></span>  
 [<span data-ttu-id="43c2e-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="43c2e-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="43c2e-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="43c2e-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="43c2e-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="43c2e-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
