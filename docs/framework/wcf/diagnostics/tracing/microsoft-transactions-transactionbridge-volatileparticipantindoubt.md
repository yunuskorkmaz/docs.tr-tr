---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98ce61e4a46f8853e61e0ef44fdc78cf3e94431a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="9a258-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="9a258-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="9a258-103">WS-AT protokolü hizmeti tanınmayan bir geçici Katılımcısı Prepared ya da yeniden yürütme bir ileti aldı.</span><span class="sxs-lookup"><span data-stu-id="9a258-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="9a258-104">Bir hata bildirir hareketin sonucu şüpheli olduğunu katılımcı döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9a258-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9a258-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a258-105">Description</span></span>  
 <span data-ttu-id="9a258-106">Yerel işlem yöneticisi unutulursa bir değişken kaydı Prepared ya da yeniden yürütme iletisi aldığında izlenen.</span><span class="sxs-lookup"><span data-stu-id="9a258-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9a258-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="9a258-107">Troubleshooting</span></span>  
 <span data-ttu-id="9a258-108">Olası nedenler, geç Volatile katılımcı gelen iletileri araştırın.</span><span class="sxs-lookup"><span data-stu-id="9a258-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a258-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a258-109">See Also</span></span>  
 [<span data-ttu-id="9a258-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="9a258-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="9a258-111">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="9a258-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="9a258-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="9a258-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
