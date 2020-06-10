---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: 50dd3070525bbc6d36956b25dee587ec7864d3ff
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594315"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="fb7aa-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="fb7aa-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="fb7aa-103">Hazırlanmış bir ileti yeniden denemesi, yanıt vermeyen bir düzenleyiciye gönderildi.</span><span class="sxs-lookup"><span data-stu-id="fb7aa-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fb7aa-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb7aa-104">Description</span></span>  
 <span data-ttu-id="fb7aa-105">Yerel Işlem yöneticisinin belirli bir süre içinde yanıt almadığı için hazırlanmış bir iletiyi bir üstün düzenleyiciye yeniden göndermesi gerekiyorsa izleniyor</span><span class="sxs-lookup"><span data-stu-id="fb7aa-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="fb7aa-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="fb7aa-106">Troubleshooting</span></span>  
 <span data-ttu-id="fb7aa-107">Yanıtın zamanında teslim edilmesini önleyen olası ağ veya ürün sorunlarını araştırın.</span><span class="sxs-lookup"><span data-stu-id="fb7aa-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="fb7aa-108">Bu mesajların birçoğu görülemiyorsa, altyapı sorunları veya anormal bir şekilde uzun yanıt süreleri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="fb7aa-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="fb7aa-109">Her iki sorun da sistem içindeki işlemlerin verimini büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="fb7aa-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb7aa-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb7aa-110">See also</span></span>

- [<span data-ttu-id="fb7aa-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="fb7aa-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="fb7aa-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="fb7aa-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fb7aa-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="fb7aa-113">Administration and Diagnostics</span></span>](../index.md)
