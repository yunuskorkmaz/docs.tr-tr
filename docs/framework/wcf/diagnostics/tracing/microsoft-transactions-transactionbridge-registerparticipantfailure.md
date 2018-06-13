---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: fb5e50e7332269690a200334ef936dd0d5525e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475120"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="f4682-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="f4682-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="f4682-103">WS-AT protokolü hizmeti katılımcı Denetim Protokolü için kaydedilemedi.</span><span class="sxs-lookup"><span data-stu-id="f4682-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f4682-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4682-104">Description</span></span>  
 <span data-ttu-id="f4682-105">Geçersiz bir kayıt isteğini MSDTC algılarsa, izlenen.</span><span class="sxs-lookup"><span data-stu-id="f4682-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="f4682-106">Bu, birden çok tamamlama kayıt isteklerini ve iç hatalar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="f4682-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f4682-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="f4682-107">Troubleshooting</span></span>  
 <span data-ttu-id="f4682-108">Tamamlama kaydolun için birden çok kez çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="f4682-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="f4682-109">Ayrıca, herhangi bir işlem yapılabilir öğe olup olmadığını belirlemek için izleme iletisi içinde durum dizesi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="f4682-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4682-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4682-110">See Also</span></span>  
 [<span data-ttu-id="f4682-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="f4682-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f4682-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="f4682-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f4682-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="f4682-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
