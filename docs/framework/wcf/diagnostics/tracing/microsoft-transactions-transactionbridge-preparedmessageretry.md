---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: edab153123ae48702811532df3b5b5bf0849c26a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275924"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="4a478-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="4a478-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>

<span data-ttu-id="4a478-103">Hazırlanmış bir ileti yeniden denemesi, yanıt vermeyen bir düzenleyiciye gönderildi.</span><span class="sxs-lookup"><span data-stu-id="4a478-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4a478-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a478-104">Description</span></span>  

 <span data-ttu-id="4a478-105">Yerel Işlem yöneticisinin belirli bir süre içinde yanıt almadığı için hazırlanmış bir iletiyi bir üstün düzenleyiciye yeniden göndermesi gerekiyorsa izleniyor</span><span class="sxs-lookup"><span data-stu-id="4a478-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4a478-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="4a478-106">Troubleshooting</span></span>  

 <span data-ttu-id="4a478-107">Yanıtın zamanında teslim edilmesini önleyen olası ağ veya ürün sorunlarını araştırın.</span><span class="sxs-lookup"><span data-stu-id="4a478-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="4a478-108">Bu mesajların birçoğu görülemiyorsa, altyapı sorunları veya anormal bir şekilde uzun yanıt süreleri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="4a478-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="4a478-109">Her iki sorun da sistem içindeki işlemlerin verimini büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="4a478-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a478-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a478-110">See also</span></span>

- [<span data-ttu-id="4a478-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="4a478-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="4a478-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="4a478-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4a478-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="4a478-113">Administration and Diagnostics</span></span>](../index.md)
