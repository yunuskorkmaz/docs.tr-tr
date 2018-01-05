---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02831a83103f5a6bd83fc2aed474245bdeda65d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="f5169-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="f5169-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="f5169-103">WS-AT protokolü hizmeti katılımcı Denetim Protokolü için kaydedilemedi.</span><span class="sxs-lookup"><span data-stu-id="f5169-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f5169-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5169-104">Description</span></span>  
 <span data-ttu-id="f5169-105">Geçersiz bir kayıt isteğini MSDTC algılarsa, izlenen.</span><span class="sxs-lookup"><span data-stu-id="f5169-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="f5169-106">Bu, birden çok tamamlama kayıt isteklerini ve iç hatalar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="f5169-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f5169-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="f5169-107">Troubleshooting</span></span>  
 <span data-ttu-id="f5169-108">Tamamlama kaydolun için birden çok kez çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="f5169-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="f5169-109">Ayrıca, herhangi bir işlem yapılabilir öğe olup olmadığını belirlemek için izleme iletisi içinde durum dizesi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="f5169-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5169-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5169-110">See Also</span></span>  
 [<span data-ttu-id="f5169-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="f5169-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f5169-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="f5169-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f5169-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="f5169-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
