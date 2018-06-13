---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: f1092dd335be793fb3d2212b7b9398cc69d2f79f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474291"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="01874-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="01874-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="01874-103">Yürütme ileti yeniden deneme yanıt vermeyen bir katılımcısı gönderildi.</span><span class="sxs-lookup"><span data-stu-id="01874-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="01874-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01874-104">Description</span></span>  
 <span data-ttu-id="01874-105">Verilen sürede yanıt almadığından kaydetme iletisi alt Katılımcısı yeniden göndermek yerel işlem yöneticisi gerekirse izlenen.</span><span class="sxs-lookup"><span data-stu-id="01874-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="01874-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="01874-106">Troubleshooting</span></span>  
 <span data-ttu-id="01874-107">Olası ağ veya zamanında teslim edilmesini gelen yanıt önlemek ürün sorunları araştırın.</span><span class="sxs-lookup"><span data-stu-id="01874-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="01874-108">Bu iletiler çoğunu görülüyorsa altyapı sorunları veya aşırı uzun yanıt sürelerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="01874-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="01874-109">Her iki sorunları sistemi içinde işlemleri verimini büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="01874-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01874-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01874-110">See Also</span></span>  
 [<span data-ttu-id="01874-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="01874-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="01874-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="01874-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="01874-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="01874-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
