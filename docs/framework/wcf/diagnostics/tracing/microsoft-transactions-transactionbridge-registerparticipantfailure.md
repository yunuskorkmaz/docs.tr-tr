---
description: 'Hakkında daha fazla bilgi edinin: Microsoft. Transactions. TransactionBridge. RegisterParticipantFailure'
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e930ee66720a9f397999d729e8d680fce9a37e29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770631"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="8ce40-103">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="8ce40-103">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>

<span data-ttu-id="8ce40-104">WS-AT protokol hizmeti, bir katılımcıyı denetim protokolü için kaydedemedi.</span><span class="sxs-lookup"><span data-stu-id="8ce40-104">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8ce40-105">Description</span><span class="sxs-lookup"><span data-stu-id="8ce40-105">Description</span></span>  

 <span data-ttu-id="8ce40-106">MSDTC geçersiz bir kayıt isteği algılarsa izleniyor.</span><span class="sxs-lookup"><span data-stu-id="8ce40-106">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="8ce40-107">Bu, birden çok tamamlama kayıt isteği ve iç hatalardan kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ce40-107">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8ce40-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="8ce40-108">Troubleshooting</span></span>  

 <span data-ttu-id="8ce40-109">Tamamlamayı birden çok kez kaydetmeyi denemeyin.</span><span class="sxs-lookup"><span data-stu-id="8ce40-109">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="8ce40-110">Ayrıca, herhangi bir eylem yapılabilir öğe olup olmadığını öğrenmek için izleme iletisindeki durum dizesini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="8ce40-110">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce40-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ce40-111">See also</span></span>

- [<span data-ttu-id="8ce40-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="8ce40-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="8ce40-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="8ce40-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8ce40-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="8ce40-114">Administration and Diagnostics</span></span>](../index.md)
