---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: affa647b30dbeb9237e4c20ebb441645eda94276
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474330"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="ab5d5-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="ab5d5-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="ab5d5-103">Prepare ileti yeniden deneme yanıt vermeyen bir katılımcısı gönderildi.</span><span class="sxs-lookup"><span data-stu-id="ab5d5-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ab5d5-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab5d5-104">Description</span></span>  
 <span data-ttu-id="ab5d5-105">Verilen sürede yanıt almadığından hazırlama ileti alt Katılımcısı yeniden göndermek yerel işlem yöneticisi gerekirse izlenen.</span><span class="sxs-lookup"><span data-stu-id="ab5d5-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ab5d5-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="ab5d5-106">Troubleshooting</span></span>  
 <span data-ttu-id="ab5d5-107">Olası ağ veya zamanında teslim edilmesini gelen yanıt önlemek ürün sorunları araştırın.</span><span class="sxs-lookup"><span data-stu-id="ab5d5-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="ab5d5-108">Bu iletiler çoğunu görülüyorsa altyapı sorunları veya aşırı uzun yanıt sürelerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="ab5d5-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="ab5d5-109">Her iki sorunlarını sistemi içinde işlemleri verimliliğini önemli ölçüde azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="ab5d5-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5d5-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab5d5-110">See Also</span></span>  
 [<span data-ttu-id="ab5d5-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="ab5d5-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ab5d5-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="ab5d5-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ab5d5-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="ab5d5-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
