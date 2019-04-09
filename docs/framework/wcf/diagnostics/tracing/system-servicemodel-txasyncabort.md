---
title: System.ServiceModel.TxAsyncAbort
ms.date: 03/30/2017
ms.assetid: bce47ff2-abd0-4b58-8667-ebf1ef3580b8
ms.openlocfilehash: a6989da7b457e819a49d7c27e8732c7f33dc51b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133932"
---
# <a name="systemservicemodeltxasyncabort"></a><span data-ttu-id="68205-102">System.ServiceModel.TxAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="68205-102">System.ServiceModel.TxAsyncAbort</span></span>
<span data-ttu-id="68205-103">Belirtilen işlem zaman uyumsuz olarak durduruldu.</span><span class="sxs-lookup"><span data-stu-id="68205-103">The specified transaction was asynchronously aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="68205-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68205-104">Description</span></span>  
 <span data-ttu-id="68205-105">Geçerli işlem, başka bir katılımcı iptal için gerçekleşen zaman aşımları oylama veya bir işlem katılımcı içinde başka bir hata nedeniyle durduruldu.</span><span class="sxs-lookup"><span data-stu-id="68205-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="68205-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="68205-106">Troubleshooting</span></span>  
 <span data-ttu-id="68205-107">Bu iptal gerçek iptal nedenini belirlemek için beklenmeyen ise tüm sistem günlüklerini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="68205-107">Check all system logs if this abort is unexpected to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68205-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68205-108">See also</span></span>

- [<span data-ttu-id="68205-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="68205-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="68205-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="68205-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="68205-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="68205-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
