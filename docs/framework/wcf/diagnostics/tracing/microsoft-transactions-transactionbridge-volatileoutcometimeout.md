---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: b64f61d25c3be87019151cbf560becd3384ec182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475637"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="a294b-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="a294b-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="a294b-103">WS-AT protokolü hizmetini geçici katılımcı sonucu iletisine yanıt beklerken zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a294b-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="a294b-104">Katılımcı döndürürse, işlem sonucu şüpheli olabilir.</span><span class="sxs-lookup"><span data-stu-id="a294b-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a294b-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a294b-105">Description</span></span>  
 <span data-ttu-id="a294b-106">İzlenen Volatile katılımcı tamamlama veya iptal etmeye karar ancak belirli bir süre içinde bir yürütme veya geri alma isteğine yanıt vermedi.</span><span class="sxs-lookup"><span data-stu-id="a294b-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a294b-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="a294b-107">Troubleshooting</span></span>  
 <span data-ttu-id="a294b-108">Tüm Volatile katılımcılar verilen sürede yanıt verebilmesini olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a294b-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="a294b-109">Varsayılan süre 180 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="a294b-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="a294b-110">Bu yetersiz ise artırmak `VolatileOutcomeDelay` WS-AT için Zamanlayıcı ilkesi.</span><span class="sxs-lookup"><span data-stu-id="a294b-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a294b-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a294b-111">See Also</span></span>  
 [<span data-ttu-id="a294b-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="a294b-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a294b-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="a294b-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a294b-114">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="a294b-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
