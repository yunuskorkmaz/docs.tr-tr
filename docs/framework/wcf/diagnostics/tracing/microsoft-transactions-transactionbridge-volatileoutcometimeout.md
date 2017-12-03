---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2a4bbaca70954e5aa89dbcfd14723551de7848f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="1f697-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="1f697-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="1f697-103">WS-AT protokolü hizmetini geçici katılımcı sonucu iletisine yanıt beklerken zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1f697-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="1f697-104">Katılımcı döndürürse, işlem sonucu şüpheli olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f697-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1f697-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f697-105">Description</span></span>  
 <span data-ttu-id="1f697-106">İzlenen Volatile katılımcı tamamlama veya iptal etmeye karar ancak belirli bir süre içinde bir yürütme veya geri alma isteğine yanıt vermedi.</span><span class="sxs-lookup"><span data-stu-id="1f697-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1f697-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="1f697-107">Troubleshooting</span></span>  
 <span data-ttu-id="1f697-108">Tüm Volatile katılımcılar verilen sürede yanıt verebilmesini olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1f697-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="1f697-109">Varsayılan süre 180 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="1f697-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="1f697-110">Bu yetersiz ise artırmak `VolatileOutcomeDelay` WS-AT için Zamanlayıcı ilkesi.</span><span class="sxs-lookup"><span data-stu-id="1f697-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f697-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f697-111">See Also</span></span>  
 [<span data-ttu-id="1f697-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="1f697-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1f697-113">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="1f697-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1f697-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="1f697-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
