---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 23a0113488b1b1ef0bc161d4134b9325ef81406c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236721"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="2be50-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="2be50-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>

<span data-ttu-id="2be50-103">Yanıt vermeyen bir düzenleyiciye yeniden yürütme iletisi gönderildi.</span><span class="sxs-lookup"><span data-stu-id="2be50-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2be50-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2be50-104">Description</span></span>  

 <span data-ttu-id="2be50-105">Yerel Işlem yöneticisinin belirli bir süre içinde yanıt almadığı için bir yeniden yürütme iletisini bir üstün düzenleyiciye yeniden göndermesi gerekiyorsa izleniyor.</span><span class="sxs-lookup"><span data-stu-id="2be50-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="2be50-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="2be50-106">Troubleshooting</span></span>  

 <span data-ttu-id="2be50-107">Yanıtın zamanında teslim edilmesini önleyen olası ağ veya ürün sorunlarını araştırın.</span><span class="sxs-lookup"><span data-stu-id="2be50-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="2be50-108">Bu mesajların birçoğu görülemiyorsa, altyapı sorunları veya anormal bir şekilde uzun yanıt süreleri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="2be50-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="2be50-109">Her iki sorun da sistem içindeki işlemlerin verimini büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="2be50-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be50-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2be50-110">See also</span></span>

- [<span data-ttu-id="2be50-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="2be50-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="2be50-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="2be50-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2be50-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="2be50-113">Administration and Diagnostics</span></span>](../index.md)
