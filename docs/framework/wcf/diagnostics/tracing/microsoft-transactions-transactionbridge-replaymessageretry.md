---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da0af06181ce888fe00203cf1e780257cd142be7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="47cb3-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="47cb3-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="47cb3-103">Bir ileti denemesi, yanıt vermeyen bir düzenleyiciye gönderildi.</span><span class="sxs-lookup"><span data-stu-id="47cb3-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="47cb3-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47cb3-104">Description</span></span>  
 <span data-ttu-id="47cb3-105">Yerel işlem yöneticisi verilen sürede yanıt almadığından üstün Düzenleyicisi yeniden yürütme iletiyi göndermeyi gerekirse izlenen.</span><span class="sxs-lookup"><span data-stu-id="47cb3-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="47cb3-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="47cb3-106">Troubleshooting</span></span>  
 <span data-ttu-id="47cb3-107">Olası ağ veya zamanında teslim edilmesini gelen yanıt önlemek ürün sorunları araştırın.</span><span class="sxs-lookup"><span data-stu-id="47cb3-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="47cb3-108">Bu iletiler çoğunu görülüyorsa altyapı sorunları veya aşırı uzun yanıt sürelerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="47cb3-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="47cb3-109">Her iki sorunları sistemi içinde işlemleri verimini büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="47cb3-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47cb3-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47cb3-110">See Also</span></span>  
 [<span data-ttu-id="47cb3-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="47cb3-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="47cb3-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="47cb3-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="47cb3-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="47cb3-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
