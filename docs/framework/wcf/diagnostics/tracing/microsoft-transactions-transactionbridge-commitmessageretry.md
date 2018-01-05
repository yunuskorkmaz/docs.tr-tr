---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58adacd909ad5254f9fb1e67b42f122e0ea01ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="f3c11-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="f3c11-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="f3c11-103">Yürütme ileti yeniden deneme yanıt vermeyen bir katılımcısı gönderildi.</span><span class="sxs-lookup"><span data-stu-id="f3c11-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f3c11-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3c11-104">Description</span></span>  
 <span data-ttu-id="f3c11-105">Verilen sürede yanıt almadığından kaydetme iletisi alt Katılımcısı yeniden göndermek yerel işlem yöneticisi gerekirse izlenen.</span><span class="sxs-lookup"><span data-stu-id="f3c11-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f3c11-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="f3c11-106">Troubleshooting</span></span>  
 <span data-ttu-id="f3c11-107">Olası ağ veya zamanında teslim edilmesini gelen yanıt önlemek ürün sorunları araştırın.</span><span class="sxs-lookup"><span data-stu-id="f3c11-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="f3c11-108">Bu iletiler çoğunu görülüyorsa altyapı sorunları veya aşırı uzun yanıt sürelerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="f3c11-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="f3c11-109">Her iki sorunları sistemi içinde işlemleri verimini büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="f3c11-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3c11-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3c11-110">See Also</span></span>  
 [<span data-ttu-id="f3c11-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="f3c11-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f3c11-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="f3c11-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f3c11-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="f3c11-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
