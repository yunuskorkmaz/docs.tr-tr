---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: 9434f2f902a50a37fb3efee22fd3b18b33af9129
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138976"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="aac5b-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="aac5b-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="aac5b-103">WS-AT protokolü hizmeti, tanınmayan bir geçici katılımcıdan Prepared ya da yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="aac5b-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="aac5b-104">Bir hata şüpheli hareketin sonucu olduğunu bildirir, katılımcı döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="aac5b-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="aac5b-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aac5b-105">Description</span></span>  
 <span data-ttu-id="aac5b-106">Yerel hareket yöneticisi zaten unutmuş bir geçici liste Prepared ya da yeniden yürütme iletisi aldığında izlenen.</span><span class="sxs-lookup"><span data-stu-id="aac5b-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="aac5b-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="aac5b-107">Troubleshooting</span></span>  
 <span data-ttu-id="aac5b-108">Olası nedenler, geç geçici katılımcıdan gelen iletileri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="aac5b-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac5b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aac5b-109">See also</span></span>

- [<span data-ttu-id="aac5b-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="aac5b-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="aac5b-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="aac5b-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="aac5b-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="aac5b-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
