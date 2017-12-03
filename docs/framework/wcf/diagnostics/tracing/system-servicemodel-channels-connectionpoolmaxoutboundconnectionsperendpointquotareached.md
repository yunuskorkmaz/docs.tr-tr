---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f90ba7a245b36b24c190304f34a4481d1abda121
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="2d236-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="2d236-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="2d236-103">WS-AT protokolü hizmeti sağlanan düzenleme bağlamı kullanarak bir işleme kaydolunamadı.</span><span class="sxs-lookup"><span data-stu-id="2d236-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2d236-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d236-104">Description</span></span>  
 <span data-ttu-id="2d236-105">MSDTC verilen 2pc protokolü için bir işlem listeleme erişemediğinde izlenen.</span><span class="sxs-lookup"><span data-stu-id="2d236-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="2d236-106">Bu işlem artık, kaydetme artık izin verilir veya çok fazla kayıtlar zaten mevcut olduğundan meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="2d236-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="2d236-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="2d236-107">Troubleshooting</span></span>  
 <span data-ttu-id="2d236-108">Durum dizesi herhangi bir işlem yapılabilir öğe olup olmadığını belirlemek için izleme iletisi içinde inceleyin.</span><span class="sxs-lookup"><span data-stu-id="2d236-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d236-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d236-109">See Also</span></span>  
 [<span data-ttu-id="2d236-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="2d236-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="2d236-111">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="2d236-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="2d236-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="2d236-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
