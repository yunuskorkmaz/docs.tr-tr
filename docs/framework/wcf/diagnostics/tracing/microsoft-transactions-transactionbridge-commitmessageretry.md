---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: 28b83b293570adf3b1cfdc15c77afd0f0cf768eb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259031"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="8ad25-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="8ad25-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>

<span data-ttu-id="8ad25-103">Bir tamamlama iletisi yeniden denemesi, yanıt vermeyen bir katılımcıya gönderildi.</span><span class="sxs-lookup"><span data-stu-id="8ad25-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8ad25-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ad25-104">Description</span></span>  

 <span data-ttu-id="8ad25-105">Yerel Işlem yöneticisinin belirli bir süre içinde yanıt almadığı için bir Işleme iletisini bir alt katılımcıya yeniden göndermesi gerekiyorsa izleniyor.</span><span class="sxs-lookup"><span data-stu-id="8ad25-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8ad25-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="8ad25-106">Troubleshooting</span></span>  

 <span data-ttu-id="8ad25-107">Yanıtın zamanında teslim edilmesini önleyen olası ağ veya ürün sorunlarını araştırın.</span><span class="sxs-lookup"><span data-stu-id="8ad25-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="8ad25-108">Bu mesajların birçoğu görülemiyorsa, altyapı sorunları veya anormal bir şekilde uzun yanıt süreleri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="8ad25-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="8ad25-109">Her iki sorun da sistem içindeki işlemlerin verimini büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="8ad25-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad25-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ad25-110">See also</span></span>

- [<span data-ttu-id="8ad25-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="8ad25-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="8ad25-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="8ad25-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8ad25-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="8ad25-113">Administration and Diagnostics</span></span>](../index.md)
