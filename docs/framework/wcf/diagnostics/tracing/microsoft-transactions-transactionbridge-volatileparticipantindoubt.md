---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: ab1c2c8afe3a66536810a614cc6deac12519cb9b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599639"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="89280-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="89280-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="89280-103">WS-AT protokol hizmeti, tanınmayan bir geçici katılımcıdan hazırlanmış veya yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="89280-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="89280-104">Katılımcıya bir hata döndürüldü, işlemin sonucunun şüpheli olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="89280-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="89280-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89280-105">Description</span></span>  
 <span data-ttu-id="89280-106">Yerel Işlem Yöneticisi zaten unutmakta olan geçici bir listeden hazırlanmış veya yeniden yürütme iletisi aldığında izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="89280-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="89280-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="89280-107">Troubleshooting</span></span>  
 <span data-ttu-id="89280-108">Geçici katılımcıdan gelen geç mesajların olası nedenlerini araştırın.</span><span class="sxs-lookup"><span data-stu-id="89280-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89280-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89280-109">See also</span></span>

- [<span data-ttu-id="89280-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="89280-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="89280-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="89280-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="89280-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="89280-112">Administration and Diagnostics</span></span>](../index.md)
