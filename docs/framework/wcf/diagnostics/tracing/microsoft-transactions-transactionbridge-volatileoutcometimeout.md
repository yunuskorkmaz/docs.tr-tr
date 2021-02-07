---
description: 'Hakkında daha fazla bilgi edinin: Microsoft. Transactions. TransactionBridge. VolatileOutcomeTimeout'
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: 5dd6ecce995d315581e1335e4dc83c425a6381b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677242"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="7fa7a-103">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="7fa7a-103">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>

<span data-ttu-id="7fa7a-104">WS-AT protokol hizmeti, geçici bir katılımcıdan bir sonuç iletisine yanıt beklerken zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-104">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="7fa7a-105">Katılımcı geri dönerse, işlem sonucu şüpheli olabilir.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-105">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7fa7a-106">Description</span><span class="sxs-lookup"><span data-stu-id="7fa7a-106">Description</span></span>  

 <span data-ttu-id="7fa7a-107">Geçici katılımcı Işlemeye veya durdurmaya karar verdiğinde, ancak belirli bir süre içinde bir COMMIT veya Rollback isteğine yanıt vermediğini izlendi.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-107">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7fa7a-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="7fa7a-108">Troubleshooting</span></span>  

 <span data-ttu-id="7fa7a-109">Tüm geçici katılımcıların verilen süre içinde yanıt verebilmesini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-109">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="7fa7a-110">Varsayılan zaman aralığı 180 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-110">The default time period is 180 seconds.</span></span>  <span data-ttu-id="7fa7a-111">Bu yeterli değilse, `VolatileOutcomeDelay` ws-at zamanlayıcı ilkesini artırın.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-111">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa7a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-112">See also</span></span>

- [<span data-ttu-id="7fa7a-113">İzleme</span><span class="sxs-lookup"><span data-stu-id="7fa7a-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="7fa7a-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="7fa7a-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7fa7a-115">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="7fa7a-115">Administration and Diagnostics</span></span>](../index.md)
