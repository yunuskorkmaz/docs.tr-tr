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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19312862a9ae801ae0909c390b0c86ee989f7f94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="1a676-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="1a676-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="1a676-103">Bir işlem oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="1a676-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1a676-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a676-104">Description</span></span>  
 <span data-ttu-id="1a676-105">MSDTC bir işlem oluşturamıyor olduğunda bu izleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1a676-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="1a676-106">Bu, kaynak yetersizliği, yeterli günlük alanının veya diğer hatalar nedeniyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a676-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1a676-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="1a676-107">Troubleshooting</span></span>  
 <span data-ttu-id="1a676-108">Durum dizesi herhangi bir işlem yapılabilir öğe olup olmadığını belirlemek için izleme iletisi içinde inceleyin.</span><span class="sxs-lookup"><span data-stu-id="1a676-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a676-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a676-109">See Also</span></span>  
 [<span data-ttu-id="1a676-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="1a676-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1a676-111">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="1a676-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1a676-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="1a676-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
