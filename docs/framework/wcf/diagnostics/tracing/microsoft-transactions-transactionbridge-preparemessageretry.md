---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b8199398e4e0bfe8ad42f6c8ba8adb11e883236e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="8fc1a-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="8fc1a-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="8fc1a-103">Prepare ileti yeniden deneme yanıt vermeyen bir katılımcısı gönderildi.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8fc1a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fc1a-104">Description</span></span>  
 <span data-ttu-id="8fc1a-105">Verilen sürede yanıt almadığından hazırlama ileti alt Katılımcısı yeniden göndermek yerel işlem yöneticisi gerekirse izlenen.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8fc1a-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="8fc1a-106">Troubleshooting</span></span>  
 <span data-ttu-id="8fc1a-107">Olası ağ veya zamanında teslim edilmesini gelen yanıt önlemek ürün sorunları araştırın.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="8fc1a-108">Bu iletiler çoğunu görülüyorsa altyapı sorunları veya aşırı uzun yanıt sürelerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="8fc1a-109">Her iki sorunlarını sistemi içinde işlemleri verimliliğini önemli ölçüde azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc1a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-110">See Also</span></span>  
 [<span data-ttu-id="8fc1a-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="8fc1a-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8fc1a-112">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="8fc1a-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8fc1a-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="8fc1a-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
