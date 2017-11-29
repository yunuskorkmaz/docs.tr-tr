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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a00a6a06fd5214f1f65bdb6369839d717078da77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="6755c-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="6755c-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="6755c-103">WS-AT protokolü hizmeti hazırlanma yanıt vermediğinden dayanıklı katılımcı yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="6755c-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="6755c-104">Sonuç olarak, işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6755c-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6755c-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6755c-105">Description</span></span>  
 <span data-ttu-id="6755c-106">Dayanıklı katılımcı hala hazırlama sırasında bir yeniden yürütme ileti alırsanız izlenen.</span><span class="sxs-lookup"><span data-stu-id="6755c-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="6755c-107">Bu bu durumu için geçersiz bir ileti ve işlem iptal edecek.</span><span class="sxs-lookup"><span data-stu-id="6755c-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6755c-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="6755c-108">Troubleshooting</span></span>  
 <span data-ttu-id="6755c-109">Bu hatanın işlem sonucunu emin değilseniz ancak (alt TransactionManagers dahil) dayanıklı katılımcı, hatasından kurtarıldı indiate olabilir ve durumunu isteyin.</span><span class="sxs-lookup"><span data-stu-id="6755c-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6755c-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6755c-110">See Also</span></span>  
 [<span data-ttu-id="6755c-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="6755c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="6755c-112">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="6755c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="6755c-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="6755c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
