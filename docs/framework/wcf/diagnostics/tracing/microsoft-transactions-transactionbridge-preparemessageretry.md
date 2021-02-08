---
description: 'Hakkında daha fazla bilgi edinin: Microsoft. Transactions. TransactionBridge. PrepareMessageRetry'
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 7555336f1082eb097017f9440015f6ab201cdeae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770787"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="0bd08-103">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="0bd08-103">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>

<span data-ttu-id="0bd08-104">Bir hazırlık iletisi yeniden denemesi, yanıt vermeyen bir katılımcıya gönderildi.</span><span class="sxs-lookup"><span data-stu-id="0bd08-104">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0bd08-105">Description</span><span class="sxs-lookup"><span data-stu-id="0bd08-105">Description</span></span>  

 <span data-ttu-id="0bd08-106">Yerel Işlem yöneticisinin belirli bir sürede yanıt almadığı için bir uygulamayı bir alt katılımcıya yeniden göndermesi gerekiyorsa izleniyor.</span><span class="sxs-lookup"><span data-stu-id="0bd08-106">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0bd08-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="0bd08-107">Troubleshooting</span></span>  

 <span data-ttu-id="0bd08-108">Yanıtın zamanında teslim edilmesini önleyen olası ağ veya ürün sorunlarını araştırın.</span><span class="sxs-lookup"><span data-stu-id="0bd08-108">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="0bd08-109">Bu mesajların birçoğu görülemiyorsa, altyapı sorunları veya anormal bir şekilde uzun yanıt süreleri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="0bd08-109">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="0bd08-110">Her iki sorun da sistem içindeki işlemlerin verimini büyük ölçüde azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="0bd08-110">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd08-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bd08-111">See also</span></span>

- [<span data-ttu-id="0bd08-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="0bd08-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="0bd08-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="0bd08-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0bd08-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="0bd08-114">Administration and Diagnostics</span></span>](../index.md)
