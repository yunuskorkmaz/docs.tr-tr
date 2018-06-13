---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: 663c06251f7a52a60b32e2f5cc3c47663436c66b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33476043"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="bafb6-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="bafb6-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="bafb6-103">WS-AT protokolü hizmeti tanınmayan bir geçici Katılımcısı Prepared ya da yeniden yürütme bir ileti aldı.</span><span class="sxs-lookup"><span data-stu-id="bafb6-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="bafb6-104">Bir hata bildirir hareketin sonucu şüpheli olduğunu katılımcı döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bafb6-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bafb6-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bafb6-105">Description</span></span>  
 <span data-ttu-id="bafb6-106">Yerel işlem yöneticisi unutulursa bir değişken kaydı Prepared ya da yeniden yürütme iletisi aldığında izlenen.</span><span class="sxs-lookup"><span data-stu-id="bafb6-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="bafb6-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="bafb6-107">Troubleshooting</span></span>  
 <span data-ttu-id="bafb6-108">Olası nedenler, geç Volatile katılımcı gelen iletileri araştırın.</span><span class="sxs-lookup"><span data-stu-id="bafb6-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bafb6-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bafb6-109">See Also</span></span>  
 [<span data-ttu-id="bafb6-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="bafb6-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="bafb6-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="bafb6-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="bafb6-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="bafb6-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
