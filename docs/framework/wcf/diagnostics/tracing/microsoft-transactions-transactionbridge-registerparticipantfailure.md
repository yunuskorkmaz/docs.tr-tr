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
ms.openlocfilehash: 16b0261a53df29b1fc2049c25375c651735a524c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="ac252-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="ac252-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="ac252-103">WS-AT protokolü hizmeti katılımcı Denetim Protokolü için kaydedilemedi.</span><span class="sxs-lookup"><span data-stu-id="ac252-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ac252-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac252-104">Description</span></span>  
 <span data-ttu-id="ac252-105">Geçersiz bir kayıt isteğini MSDTC algılarsa, izlenen.</span><span class="sxs-lookup"><span data-stu-id="ac252-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="ac252-106">Bu, birden çok tamamlama kayıt isteklerini ve iç hatalar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ac252-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ac252-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="ac252-107">Troubleshooting</span></span>  
 <span data-ttu-id="ac252-108">Tamamlama kaydolun için birden çok kez çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="ac252-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="ac252-109">Ayrıca, herhangi bir işlem yapılabilir öğe olup olmadığını belirlemek için izleme iletisi içinde durum dizesi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="ac252-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac252-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac252-110">See Also</span></span>  
 [<span data-ttu-id="ac252-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="ac252-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ac252-112">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="ac252-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ac252-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="ac252-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
