---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: d8acdb2f94e752860025ee2963aa78682b43b079
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216918"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="51f2d-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="51f2d-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="51f2d-103">Yanıt vermeyen bir düzenleyiciye hazırlıklı ileti yeniden gönderildi.</span><span class="sxs-lookup"><span data-stu-id="51f2d-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="51f2d-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51f2d-104">Description</span></span>  
 <span data-ttu-id="51f2d-105">Yerel hareket yöneticisi belirli bir süre içinde bir yanıt almadığı için üstün bir düzenleyici için hazırlanmış bir iletisini yeniden göndermeniz gerekirse izlenen /</span><span class="sxs-lookup"><span data-stu-id="51f2d-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="51f2d-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="51f2d-106">Troubleshooting</span></span>  
 <span data-ttu-id="51f2d-107">Olası ağ veya tarihte teslim edilen gelen yanıt engelleyen ürün sorunları araştırın.</span><span class="sxs-lookup"><span data-stu-id="51f2d-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="51f2d-108">Bu iletiler birçoğu görülürse, altyapı sorunları veya aşırı uzun yanıt süreleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51f2d-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="51f2d-109">Her iki sorun sistemi içinde işlemlerinin aktarım hızını ciddi ölçüde düşürüyor.</span><span class="sxs-lookup"><span data-stu-id="51f2d-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f2d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51f2d-110">See also</span></span>

- [<span data-ttu-id="51f2d-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="51f2d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="51f2d-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="51f2d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="51f2d-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="51f2d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
