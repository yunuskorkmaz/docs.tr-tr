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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2a99e8b3158da9d473d50bc7792ce9e2aa19bb27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="025e1-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="025e1-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="025e1-103">Belirtilen işlem için belirtilen işlem, zaman uyumsuz iptal nedeniyle tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="025e1-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="025e1-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="025e1-104">Description</span></span>  
 <span data-ttu-id="025e1-105">Geçerli işlem, başka bir katılımcı iptal için gerçekleşen zaman aşımlarını oylama ya da bir işlem katılımcı içinde başka bir hata nedeniyle durduruldu.</span><span class="sxs-lookup"><span data-stu-id="025e1-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="025e1-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="025e1-106">Troubleshooting</span></span>  
 <span data-ttu-id="025e1-107">Bu iptal beklenmiyorsa durdurma gerçek nedenini belirlemek için tüm sistem günlüklerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="025e1-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="025e1-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="025e1-108">See Also</span></span>  
 [<span data-ttu-id="025e1-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="025e1-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="025e1-110">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="025e1-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="025e1-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="025e1-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
