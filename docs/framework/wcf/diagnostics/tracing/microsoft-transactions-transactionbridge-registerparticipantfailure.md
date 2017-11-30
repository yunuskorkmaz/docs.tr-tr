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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e3cbe9443f32ec9752198646e96cc1012d7343c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="9cbcb-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="9cbcb-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="9cbcb-103">WS-AT protokolü hizmeti katılımcı Denetim Protokolü için kaydedilemedi.</span><span class="sxs-lookup"><span data-stu-id="9cbcb-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9cbcb-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cbcb-104">Description</span></span>  
 <span data-ttu-id="9cbcb-105">Geçersiz bir kayıt isteğini MSDTC algılarsa, izlenen.</span><span class="sxs-lookup"><span data-stu-id="9cbcb-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="9cbcb-106">Bu, birden çok tamamlama kayıt isteklerini ve iç hatalar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="9cbcb-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9cbcb-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="9cbcb-107">Troubleshooting</span></span>  
 <span data-ttu-id="9cbcb-108">Tamamlama kaydolun için birden çok kez çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="9cbcb-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="9cbcb-109">Ayrıca, herhangi bir işlem yapılabilir öğe olup olmadığını belirlemek için izleme iletisi içinde durum dizesi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="9cbcb-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cbcb-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9cbcb-110">See Also</span></span>  
 [<span data-ttu-id="9cbcb-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="9cbcb-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="9cbcb-112">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="9cbcb-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="9cbcb-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="9cbcb-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
