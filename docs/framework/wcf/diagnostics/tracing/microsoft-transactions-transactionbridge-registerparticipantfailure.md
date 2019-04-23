---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e56a9ed1d837af27d481282e0e106d537ec41ee3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164300"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="70309-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="70309-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="70309-103">Denetim Protokolü için katılımcı WS-AT protokolü hizmeti kaydedilemedi.</span><span class="sxs-lookup"><span data-stu-id="70309-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="70309-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70309-104">Description</span></span>  
 <span data-ttu-id="70309-105">Geçersiz bir kayıt isteği MSDTC algılarsa, izlenen.</span><span class="sxs-lookup"><span data-stu-id="70309-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="70309-106">Bu, birden çok tamamlama kayıt isteklerini ve iç hata tarafından kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="70309-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="70309-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="70309-107">Troubleshooting</span></span>  
 <span data-ttu-id="70309-108">Kayıt tamamlanması için birden çok kez denemeyin.</span><span class="sxs-lookup"><span data-stu-id="70309-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="70309-109">Ayrıca, eyleme dönüştürülebilir herhangi bir öğe olup olmadığını belirlemek için izleme iletisi durumu dizede inceleyin.</span><span class="sxs-lookup"><span data-stu-id="70309-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70309-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70309-110">See also</span></span>

- [<span data-ttu-id="70309-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="70309-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="70309-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="70309-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="70309-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="70309-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
