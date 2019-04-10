---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 02e275fa212128c65beda4bc3703949e75ea5092
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220896"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="ccf81-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="ccf81-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="ccf81-103">Yanıt vermeyen bir katılımcı hazırlama ileti yeniden gönderildi.</span><span class="sxs-lookup"><span data-stu-id="ccf81-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ccf81-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccf81-104">Description</span></span>  
 <span data-ttu-id="ccf81-105">Yerel hareket yöneticisi belirli bir süre içinde bir yanıt almadığı için bir hazırlama ileti bağımlı Katılımcısı yeniden göndermeniz gerekirse izlenen.</span><span class="sxs-lookup"><span data-stu-id="ccf81-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ccf81-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="ccf81-106">Troubleshooting</span></span>  
 <span data-ttu-id="ccf81-107">Olası ağ veya tarihte teslim edilen gelen yanıt engelleyen ürün sorunları araştırın.</span><span class="sxs-lookup"><span data-stu-id="ccf81-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="ccf81-108">Bu iletiler birçoğu görülürse, altyapı sorunları veya aşırı uzun yanıt süreleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccf81-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="ccf81-109">Her iki sorun sistem işlemleri hacmini önemli ölçüde azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="ccf81-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf81-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccf81-110">See also</span></span>

- [<span data-ttu-id="ccf81-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="ccf81-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="ccf81-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="ccf81-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ccf81-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="ccf81-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
