---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: 22992b4dfad4b4867adda0fcbbd8ecc5eb67d87e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160154"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="12e42-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="12e42-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="12e42-103">WS-AT protokolü hizmetini geçici bir katılımcı sonucu iletisine yanıt beklerken zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="12e42-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="12e42-104">Katılımcı döndürürse, şüpheli işlem sonucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="12e42-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="12e42-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12e42-105">Description</span></span>  
 <span data-ttu-id="12e42-106">Geçici bir katılımcı tamamlama veya iptal karar verdi, ancak bir yürütme veya geri alma isteği için belirli bir süre içinde yanıt vermedi izlenen.</span><span class="sxs-lookup"><span data-stu-id="12e42-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="12e42-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="12e42-107">Troubleshooting</span></span>  
 <span data-ttu-id="12e42-108">Tüm geçici katılımcıları belirtilen süre içinde yanıt verebilir durumda olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="12e42-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="12e42-109">Varsayılan süre 180 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="12e42-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="12e42-110">Bu yetersiz kalırsa, artırmak `VolatileOutcomeDelay` WS-AT Zamanlayıcı ilkesini.</span><span class="sxs-lookup"><span data-stu-id="12e42-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e42-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12e42-111">See also</span></span>

- [<span data-ttu-id="12e42-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="12e42-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="12e42-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="12e42-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="12e42-114">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="12e42-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
