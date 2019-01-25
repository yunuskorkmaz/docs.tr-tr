---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: b25debfd9b1e6de6b93fd4dfa8b96925718d9d87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550844"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="c89b6-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="c89b6-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="c89b6-103">WS-AT protokolü hizmeti, tanınmayan bir geçici katılımcıdan Prepared ya da yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="c89b6-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="c89b6-104">Bir hata şüpheli hareketin sonucu olduğunu bildirir, katılımcı döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c89b6-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c89b6-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c89b6-105">Description</span></span>  
 <span data-ttu-id="c89b6-106">Yerel hareket yöneticisi zaten unutmuş bir geçici liste Prepared ya da yeniden yürütme iletisi aldığında izlenen.</span><span class="sxs-lookup"><span data-stu-id="c89b6-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c89b6-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="c89b6-107">Troubleshooting</span></span>  
 <span data-ttu-id="c89b6-108">Olası nedenler, geç geçici katılımcıdan gelen iletileri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="c89b6-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c89b6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c89b6-109">See also</span></span>
- [<span data-ttu-id="c89b6-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="c89b6-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="c89b6-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="c89b6-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c89b6-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="c89b6-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
