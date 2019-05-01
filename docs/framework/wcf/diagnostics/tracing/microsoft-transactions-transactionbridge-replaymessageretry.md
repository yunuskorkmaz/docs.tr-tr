---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 0c9e79709f5929e1fa123a8d1695ca720046e9e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997535"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="6871a-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="6871a-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="6871a-103">Bir ileti denemesi, yanıt vermeyen bir düzenleyiciye gönderildi.</span><span class="sxs-lookup"><span data-stu-id="6871a-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6871a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6871a-104">Description</span></span>  
 <span data-ttu-id="6871a-105">Yerel hareket yöneticisi belirli bir süre içinde bir yanıt almadığı için üstün bir düzenleyici için bir yeniden yürütme iletisini yeniden göndermeniz gerekirse izlenen.</span><span class="sxs-lookup"><span data-stu-id="6871a-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6871a-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="6871a-106">Troubleshooting</span></span>  
 <span data-ttu-id="6871a-107">Olası ağ veya tarihte teslim edilen gelen yanıt engelleyen ürün sorunları araştırın.</span><span class="sxs-lookup"><span data-stu-id="6871a-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="6871a-108">Bu iletiler birçoğu görülürse, altyapı sorunları veya aşırı uzun yanıt süreleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6871a-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="6871a-109">Her iki sorun sistemi içinde işlemlerinin aktarım hızını ciddi ölçüde düşürüyor.</span><span class="sxs-lookup"><span data-stu-id="6871a-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6871a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6871a-110">See also</span></span>

- [<span data-ttu-id="6871a-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="6871a-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="6871a-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="6871a-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6871a-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="6871a-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
