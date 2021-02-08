---
description: 'Hakkında daha fazla bilgi edinin: Microsoft. Transactions. TransactionBridge. ReplayMessageRetry'
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: e4de1416fab2cf7098d0276b6130999c01ea6e3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803262"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="7bdc2-103">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="7bdc2-103">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>

<span data-ttu-id="7bdc2-104">Yanıt vermeyen bir düzenleyiciye yeniden yürütme iletisi gönderildi.</span><span class="sxs-lookup"><span data-stu-id="7bdc2-104">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7bdc2-105">Description</span><span class="sxs-lookup"><span data-stu-id="7bdc2-105">Description</span></span>  

 <span data-ttu-id="7bdc2-106">Yerel Işlem yöneticisinin belirli bir süre içinde yanıt almadığı için bir yeniden yürütme iletisini bir üstün düzenleyiciye yeniden göndermesi gerekiyorsa izleniyor.</span><span class="sxs-lookup"><span data-stu-id="7bdc2-106">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7bdc2-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="7bdc2-107">Troubleshooting</span></span>  

 <span data-ttu-id="7bdc2-108">Yanıtın zamanında teslim edilmesini önleyen olası ağ veya ürün sorunlarını araştırın.</span><span class="sxs-lookup"><span data-stu-id="7bdc2-108">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="7bdc2-109">Bu mesajların birçoğu görülemiyorsa, altyapı sorunları veya anormal bir şekilde uzun yanıt süreleri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="7bdc2-109">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="7bdc2-110">Her iki sorun da sistem içindeki işlemlerin verimini büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="7bdc2-110">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bdc2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bdc2-111">See also</span></span>

- [<span data-ttu-id="7bdc2-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="7bdc2-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="7bdc2-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="7bdc2-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7bdc2-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="7bdc2-114">Administration and Diagnostics</span></span>](../index.md)
