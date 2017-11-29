---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b497231326c640b93b96500df39732104e0f0c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="a0873-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="a0873-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="a0873-103">WS-AT protokolü hizmeti tanınmayan bir geçici Katılımcısı Prepared ya da yeniden yürütme bir ileti aldı.</span><span class="sxs-lookup"><span data-stu-id="a0873-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="a0873-104">Bir hata bildirir hareketin sonucu şüpheli olduğunu katılımcı döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a0873-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a0873-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0873-105">Description</span></span>  
 <span data-ttu-id="a0873-106">Yerel işlem yöneticisi unutulursa bir değişken kaydı Prepared ya da yeniden yürütme iletisi aldığında izlenen.</span><span class="sxs-lookup"><span data-stu-id="a0873-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a0873-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="a0873-107">Troubleshooting</span></span>  
 <span data-ttu-id="a0873-108">Olası nedenler, geç Volatile katılımcı gelen iletileri araştırın.</span><span class="sxs-lookup"><span data-stu-id="a0873-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0873-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0873-109">See Also</span></span>  
 [<span data-ttu-id="a0873-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="a0873-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a0873-111">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="a0873-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a0873-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="a0873-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
