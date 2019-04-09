---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: 3c398aa13a8cd2b87068216d3c07fb29e1a27c3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168109"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="63851-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="63851-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="63851-103">Bir işleme iletisi yeniden deneme yanıt vermeyen bir katılımcı gönderildi.</span><span class="sxs-lookup"><span data-stu-id="63851-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="63851-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63851-104">Description</span></span>  
 <span data-ttu-id="63851-105">Yerel hareket yöneticisi belirli bir süre içinde bir yanıt almadığı için bir işleme iletisi bağımlı Katılımcısı yeniden göndermeniz gerekirse izlenen.</span><span class="sxs-lookup"><span data-stu-id="63851-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="63851-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="63851-106">Troubleshooting</span></span>  
 <span data-ttu-id="63851-107">Olası ağ veya tarihte teslim edilen gelen yanıt engelleyen ürün sorunları araştırın.</span><span class="sxs-lookup"><span data-stu-id="63851-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="63851-108">Bu iletiler birçoğu görülürse, altyapı sorunları veya aşırı uzun yanıt süreleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63851-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="63851-109">Her iki sorun sistemi içinde işlemlerinin aktarım hızını ciddi ölçüde düşürüyor.</span><span class="sxs-lookup"><span data-stu-id="63851-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63851-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63851-110">See also</span></span>

- [<span data-ttu-id="63851-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="63851-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="63851-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="63851-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="63851-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="63851-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
