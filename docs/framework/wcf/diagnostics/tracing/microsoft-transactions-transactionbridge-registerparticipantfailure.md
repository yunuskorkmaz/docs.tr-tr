---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: 1819a269a6775c8541f38f4aa5d733002e3c1e9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599691"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="9a033-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="9a033-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="9a033-103">WS-AT protokol hizmeti, bir katılımcıyı denetim protokolü için kaydedemedi.</span><span class="sxs-lookup"><span data-stu-id="9a033-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9a033-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a033-104">Description</span></span>  
 <span data-ttu-id="9a033-105">MSDTC geçersiz bir kayıt isteği algılarsa izleniyor.</span><span class="sxs-lookup"><span data-stu-id="9a033-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="9a033-106">Bu, birden çok tamamlama kayıt isteği ve iç hatalardan kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="9a033-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9a033-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="9a033-107">Troubleshooting</span></span>  
 <span data-ttu-id="9a033-108">Tamamlamayı birden çok kez kaydetmeyi denemeyin.</span><span class="sxs-lookup"><span data-stu-id="9a033-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="9a033-109">Ayrıca, herhangi bir eylem yapılabilir öğe olup olmadığını öğrenmek için izleme iletisindeki durum dizesini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="9a033-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a033-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a033-110">See also</span></span>

- [<span data-ttu-id="9a033-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="9a033-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="9a033-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="9a033-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9a033-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="9a033-113">Administration and Diagnostics</span></span>](../index.md)
