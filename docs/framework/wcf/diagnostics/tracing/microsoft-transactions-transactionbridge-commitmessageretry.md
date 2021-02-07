---
description: 'Hakkında daha fazla bilgi edinin: Microsoft. Transactions. TransactionBridge. CommitMessageRetry'
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: 8f45463ac31c210acd8534df2c4e1ef2922f1c8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720611"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="30c21-103">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="30c21-103">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>

<span data-ttu-id="30c21-104">Bir tamamlama iletisi yeniden denemesi, yanıt vermeyen bir katılımcıya gönderildi.</span><span class="sxs-lookup"><span data-stu-id="30c21-104">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="30c21-105">Description</span><span class="sxs-lookup"><span data-stu-id="30c21-105">Description</span></span>  

 <span data-ttu-id="30c21-106">Yerel Işlem yöneticisinin belirli bir süre içinde yanıt almadığı için bir Işleme iletisini bir alt katılımcıya yeniden göndermesi gerekiyorsa izleniyor.</span><span class="sxs-lookup"><span data-stu-id="30c21-106">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="30c21-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="30c21-107">Troubleshooting</span></span>  

 <span data-ttu-id="30c21-108">Yanıtın zamanında teslim edilmesini önleyen olası ağ veya ürün sorunlarını araştırın.</span><span class="sxs-lookup"><span data-stu-id="30c21-108">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="30c21-109">Bu mesajların birçoğu görülemiyorsa, altyapı sorunları veya anormal bir şekilde uzun yanıt süreleri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="30c21-109">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="30c21-110">Her iki sorun da sistem içindeki işlemlerin verimini büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="30c21-110">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c21-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30c21-111">See also</span></span>

- [<span data-ttu-id="30c21-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="30c21-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="30c21-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="30c21-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="30c21-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="30c21-114">Administration and Diagnostics</span></span>](../index.md)
