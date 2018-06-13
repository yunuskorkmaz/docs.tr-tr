---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fe88e70ab4955305d78baa1158cd73a93ba2ed2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33476326"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="e05d8-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="e05d8-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="e05d8-103">WS-AT protokolü hizmeti hazırlanma yanıt vermediğinden dayanıklı katılımcı yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="e05d8-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="e05d8-104">Sonuç olarak, işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e05d8-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e05d8-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e05d8-105">Description</span></span>  
 <span data-ttu-id="e05d8-106">Dayanıklı katılımcı hala hazırlama sırasında bir yeniden yürütme ileti alırsanız izlenen.</span><span class="sxs-lookup"><span data-stu-id="e05d8-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="e05d8-107">Bu bu durumu için geçersiz bir ileti ve işlem iptal edecek.</span><span class="sxs-lookup"><span data-stu-id="e05d8-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e05d8-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="e05d8-108">Troubleshooting</span></span>  
 <span data-ttu-id="e05d8-109">Bu hatanın işlem sonucunu emin değilseniz ancak (alt TransactionManagers dahil) dayanıklı katılımcı, hatasından kurtarıldı indiate olabilir ve durumunu isteyin.</span><span class="sxs-lookup"><span data-stu-id="e05d8-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e05d8-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e05d8-110">See Also</span></span>  
 [<span data-ttu-id="e05d8-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="e05d8-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e05d8-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="e05d8-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e05d8-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="e05d8-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
