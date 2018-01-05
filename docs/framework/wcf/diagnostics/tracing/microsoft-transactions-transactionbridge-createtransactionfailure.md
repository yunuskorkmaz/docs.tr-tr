---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02cdc8ceb8cc667cb4160f0333ffea511dcfbd23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="5a90a-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="5a90a-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="5a90a-103">Bir işlem oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="5a90a-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5a90a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a90a-104">Description</span></span>  
 <span data-ttu-id="5a90a-105">MSDTC bir işlem oluşturamıyor olduğunda bu izleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5a90a-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="5a90a-106">Bu, kaynak yetersizliği, yeterli günlük alanının veya diğer hatalar nedeniyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a90a-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="5a90a-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="5a90a-107">Troubleshooting</span></span>  
 <span data-ttu-id="5a90a-108">Durum dizesi herhangi bir işlem yapılabilir öğe olup olmadığını belirlemek için izleme iletisi içinde inceleyin.</span><span class="sxs-lookup"><span data-stu-id="5a90a-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a90a-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a90a-109">See Also</span></span>  
 [<span data-ttu-id="5a90a-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="5a90a-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5a90a-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="5a90a-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5a90a-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="5a90a-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
