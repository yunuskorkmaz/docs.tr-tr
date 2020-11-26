---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: bc2cdc2221ec522b44c36ef3320b77124d61850e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236708"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="542ee-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="542ee-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>

<span data-ttu-id="542ee-103">WS-AT protokol hizmeti, geçici bir katılımcıdan bir sonuç iletisine yanıt beklerken zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="542ee-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="542ee-104">Katılımcı geri dönerse, işlem sonucu şüpheli olabilir.</span><span class="sxs-lookup"><span data-stu-id="542ee-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="542ee-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="542ee-105">Description</span></span>  

 <span data-ttu-id="542ee-106">Geçici katılımcı Işlemeye veya durdurmaya karar verdiğinde, ancak belirli bir süre içinde bir COMMIT veya Rollback isteğine yanıt vermediğini izlendi.</span><span class="sxs-lookup"><span data-stu-id="542ee-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="542ee-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="542ee-107">Troubleshooting</span></span>  

 <span data-ttu-id="542ee-108">Tüm geçici katılımcıların verilen süre içinde yanıt verebilmesini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="542ee-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="542ee-109">Varsayılan zaman aralığı 180 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="542ee-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="542ee-110">Bu yeterli değilse, `VolatileOutcomeDelay` ws-at zamanlayıcı ilkesini artırın.</span><span class="sxs-lookup"><span data-stu-id="542ee-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="542ee-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="542ee-111">See also</span></span>

- [<span data-ttu-id="542ee-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="542ee-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="542ee-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="542ee-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="542ee-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="542ee-114">Administration and Diagnostics</span></span>](../index.md)
