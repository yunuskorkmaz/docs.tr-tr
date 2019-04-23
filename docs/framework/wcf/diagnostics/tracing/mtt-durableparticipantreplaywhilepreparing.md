---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: f5d74d73cc43b500d3920ca03905f4eb7543619a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075541"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="42825-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="42825-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="42825-103">WS-AT protokolü hizmetini hazırlama için yanıt vermedi dayanıklı bir katılımcı yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="42825-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="42825-104">Sonuç olarak, işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="42825-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="42825-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42825-105">Description</span></span>  
 <span data-ttu-id="42825-106">Dayanıklı bir katılımcı hala hazırlama sırasında yeniden yürütme iletisi aldıysanız izlenen.</span><span class="sxs-lookup"><span data-stu-id="42825-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="42825-107">Bu durum için geçersiz bir ileti budur ve işlem iptal edecek.</span><span class="sxs-lookup"><span data-stu-id="42825-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="42825-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="42825-108">Troubleshooting</span></span>  
 <span data-ttu-id="42825-109">Bu hatanın hareketin sonucu emin değilseniz ancak (alt TransactionManagers dahil) dayanıklı bir katılımcı hata durumundan kurtuldu indiate olabilir ve durumunu istek.</span><span class="sxs-lookup"><span data-stu-id="42825-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42825-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42825-110">See also</span></span>

- [<span data-ttu-id="42825-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="42825-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="42825-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="42825-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="42825-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="42825-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
