---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: 9434f2f902a50a37fb3efee22fd3b18b33af9129
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138976"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="0b80a-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="0b80a-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="0b80a-103">WS-AT protokolü hizmeti, tanınmayan bir geçici katılımcıdan Prepared ya da yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="0b80a-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="0b80a-104">Bir hata şüpheli hareketin sonucu olduğunu bildirir, katılımcı döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0b80a-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0b80a-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b80a-105">Description</span></span>  
 <span data-ttu-id="0b80a-106">Yerel hareket yöneticisi zaten unutmuş bir geçici liste Prepared ya da yeniden yürütme iletisi aldığında izlenen.</span><span class="sxs-lookup"><span data-stu-id="0b80a-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0b80a-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="0b80a-107">Troubleshooting</span></span>  
 <span data-ttu-id="0b80a-108">Olası nedenler, geç geçici katılımcıdan gelen iletileri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="0b80a-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b80a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b80a-109">See also</span></span>

- [<span data-ttu-id="0b80a-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="0b80a-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="0b80a-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="0b80a-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0b80a-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="0b80a-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
