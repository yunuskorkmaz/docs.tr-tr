---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.date: 03/30/2017
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
ms.openlocfilehash: a243acc3d8a17e4a53b3d05e3420f481f7b6dc6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486037"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="bfcc0-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="bfcc0-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="bfcc0-103">Belirtilen işlem için belirtilen işlem, zaman uyumsuz iptal nedeniyle tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="bfcc0-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bfcc0-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfcc0-104">Description</span></span>  
 <span data-ttu-id="bfcc0-105">Geçerli işlem, başka bir katılımcı iptal için gerçekleşen zaman aşımlarını oylama ya da bir işlem katılımcı içinde başka bir hata nedeniyle durduruldu.</span><span class="sxs-lookup"><span data-stu-id="bfcc0-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="bfcc0-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="bfcc0-106">Troubleshooting</span></span>  
 <span data-ttu-id="bfcc0-107">Bu iptal beklenmiyorsa durdurma gerçek nedenini belirlemek için tüm sistem günlüklerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bfcc0-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfcc0-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bfcc0-108">See Also</span></span>  
 [<span data-ttu-id="bfcc0-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="bfcc0-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="bfcc0-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="bfcc0-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="bfcc0-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="bfcc0-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
