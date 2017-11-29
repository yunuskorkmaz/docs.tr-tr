---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 88ee90abb10e9f5e09deecb3d3d66c54dc289592
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="3b707-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="3b707-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="3b707-103">Hazırlanmış ileti yeniden denemesi, yanıt vermeyen bir düzenleyiciye gönderildi.</span><span class="sxs-lookup"><span data-stu-id="3b707-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3b707-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b707-104">Description</span></span>  
 <span data-ttu-id="3b707-105">Verilen sürede yanıt almadığından üstün Düzenleyicisi için hazırlanmış bir ileti yeniden göndermek yerel işlem yöneticisi gerekirse izlenen /</span><span class="sxs-lookup"><span data-stu-id="3b707-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="3b707-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="3b707-106">Troubleshooting</span></span>  
 <span data-ttu-id="3b707-107">Olası ağ veya zamanında teslim edilmesini gelen yanıt önlemek ürün sorunları araştırın.</span><span class="sxs-lookup"><span data-stu-id="3b707-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="3b707-108">Bu iletiler çoğunu görülüyorsa altyapı sorunları veya aşırı uzun yanıt sürelerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="3b707-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="3b707-109">Her iki sorunları sistemi içinde işlemleri verimini büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="3b707-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b707-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b707-110">See Also</span></span>  
 [<span data-ttu-id="3b707-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="3b707-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="3b707-112">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="3b707-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="3b707-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="3b707-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
