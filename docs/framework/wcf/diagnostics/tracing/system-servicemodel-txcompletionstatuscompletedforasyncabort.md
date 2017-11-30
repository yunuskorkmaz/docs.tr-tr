---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3595b98ca8c78fb6bdf86a08dcd56b37a4770405
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="7c043-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="7c043-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="7c043-103">Belirtilen işlem için belirtilen işlem, zaman uyumsuz iptal nedeniyle tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7c043-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7c043-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c043-104">Description</span></span>  
 <span data-ttu-id="7c043-105">Geçerli işlem, başka bir katılımcı iptal için gerçekleşen zaman aşımlarını oylama ya da bir işlem katılımcı içinde başka bir hata nedeniyle durduruldu.</span><span class="sxs-lookup"><span data-stu-id="7c043-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7c043-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="7c043-106">Troubleshooting</span></span>  
 <span data-ttu-id="7c043-107">Bu iptal beklenmiyorsa durdurma gerçek nedenini belirlemek için tüm sistem günlüklerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7c043-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c043-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c043-108">See Also</span></span>  
 [<span data-ttu-id="7c043-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="7c043-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="7c043-110">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="7c043-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="7c043-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="7c043-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
