---
title: System.ServiceModel.TxAsyncAbort
ms.date: 03/30/2017
ms.assetid: bce47ff2-abd0-4b58-8667-ebf1ef3580b8
ms.openlocfilehash: 188f4c16be7df06558db7be015165a30e7193f9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573822"
---
# <a name="systemservicemodeltxasyncabort"></a><span data-ttu-id="45076-102">System.ServiceModel.TxAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="45076-102">System.ServiceModel.TxAsyncAbort</span></span>
<span data-ttu-id="45076-103">Belirtilen işlem zaman uyumsuz olarak durduruldu.</span><span class="sxs-lookup"><span data-stu-id="45076-103">The specified transaction was asynchronously aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="45076-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45076-104">Description</span></span>  
 <span data-ttu-id="45076-105">Geçerli işlem, başka bir katılımcı iptal için gerçekleşen zaman aşımları oylama veya bir işlem katılımcı içinde başka bir hata nedeniyle durduruldu.</span><span class="sxs-lookup"><span data-stu-id="45076-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="45076-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="45076-106">Troubleshooting</span></span>  
 <span data-ttu-id="45076-107">Bu iptal gerçek iptal nedenini belirlemek için beklenmeyen ise tüm sistem günlüklerini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="45076-107">Check all system logs if this abort is unexpected to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45076-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45076-108">See also</span></span>
- [<span data-ttu-id="45076-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="45076-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="45076-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="45076-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="45076-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="45076-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
