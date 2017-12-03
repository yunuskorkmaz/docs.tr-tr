---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 830a55a9f82c38b0a58783c49d3f58f64d5afdb4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="8739f-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="8739f-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="8739f-103">WS-AT protokolü hizmeti hazırlanma yanıt vermediğinden dayanıklı katılımcı yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="8739f-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="8739f-104">Sonuç olarak, işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8739f-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8739f-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8739f-105">Description</span></span>  
 <span data-ttu-id="8739f-106">Dayanıklı katılımcı hala hazırlama sırasında bir yeniden yürütme ileti alırsanız izlenen.</span><span class="sxs-lookup"><span data-stu-id="8739f-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="8739f-107">Bu bu durumu için geçersiz bir ileti ve işlem iptal edecek.</span><span class="sxs-lookup"><span data-stu-id="8739f-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8739f-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="8739f-108">Troubleshooting</span></span>  
 <span data-ttu-id="8739f-109">Bu hatanın işlem sonucunu emin değilseniz ancak (alt TransactionManagers dahil) dayanıklı katılımcı, hatasından kurtarıldı indiate olabilir ve durumunu isteyin.</span><span class="sxs-lookup"><span data-stu-id="8739f-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8739f-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8739f-110">See Also</span></span>  
 [<span data-ttu-id="8739f-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="8739f-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8739f-112">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="8739f-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8739f-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="8739f-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
