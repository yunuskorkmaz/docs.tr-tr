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
ms.openlocfilehash: 55d87621ecac587a5449dbe5d93572432ef7d757
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="01a2a-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="01a2a-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>
<span data-ttu-id="01a2a-103">WS-AT protokolü hizmeti ilgili düzenleyiciye bir kayıt iletisi gönderilemedi</span><span class="sxs-lookup"><span data-stu-id="01a2a-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="01a2a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01a2a-104">Description</span></span>  
 <span data-ttu-id="01a2a-105">Yerel TransactionManager kendi üst TransactionManager nedeniyle bir ileti göndermek için kullanamama kaydı mümkün değilse, izlenen.</span><span class="sxs-lookup"><span data-stu-id="01a2a-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="01a2a-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="01a2a-106">Troubleshooting</span></span>  
 <span data-ttu-id="01a2a-107">İleti gönderme hataya neden olan özel durum izleme iletisi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="01a2a-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a2a-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01a2a-108">See Also</span></span>  
 [<span data-ttu-id="01a2a-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="01a2a-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="01a2a-110">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="01a2a-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="01a2a-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="01a2a-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
