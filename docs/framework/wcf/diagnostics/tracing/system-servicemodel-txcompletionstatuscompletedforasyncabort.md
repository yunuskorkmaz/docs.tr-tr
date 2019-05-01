---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.date: 03/30/2017
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
ms.openlocfilehash: f84cc9336d6cce7d8c477a1feb6caf45b0662177
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996937"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="e379f-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="e379f-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="e379f-103">Belirtilen işlem için belirtilen işlem nedeniyle zaman uyumsuz iptal tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e379f-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e379f-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e379f-104">Description</span></span>  
 <span data-ttu-id="e379f-105">Geçerli işlem, başka bir katılımcı iptal için gerçekleşen zaman aşımları oylama veya bir işlem katılımcı içinde başka bir hata nedeniyle durduruldu.</span><span class="sxs-lookup"><span data-stu-id="e379f-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e379f-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="e379f-106">Troubleshooting</span></span>  
 <span data-ttu-id="e379f-107">Bu iptal beklenmedikse gerçek iptal nedenini belirlemek için tüm sistem günlüklerini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="e379f-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e379f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e379f-108">See also</span></span>

- [<span data-ttu-id="e379f-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="e379f-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="e379f-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="e379f-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e379f-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="e379f-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
