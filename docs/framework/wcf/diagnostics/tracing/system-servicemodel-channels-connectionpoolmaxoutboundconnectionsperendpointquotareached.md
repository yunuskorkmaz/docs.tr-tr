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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5fa64c87bc4cd0c8dc677d8b4c59de45e31d3270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="93e30-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="93e30-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="93e30-103">WS-AT protokolü hizmeti sağlanan düzenleme bağlamı kullanarak bir işleme kaydolunamadı.</span><span class="sxs-lookup"><span data-stu-id="93e30-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="93e30-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93e30-104">Description</span></span>  
 <span data-ttu-id="93e30-105">MSDTC verilen 2pc protokolü için bir işlem listeleme erişemediğinde izlenen.</span><span class="sxs-lookup"><span data-stu-id="93e30-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="93e30-106">Bu işlem artık, kaydetme artık izin verilir veya çok fazla kayıtlar zaten mevcut olduğundan meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="93e30-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="93e30-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="93e30-107">Troubleshooting</span></span>  
 <span data-ttu-id="93e30-108">Durum dizesi herhangi bir işlem yapılabilir öğe olup olmadığını belirlemek için izleme iletisi içinde inceleyin.</span><span class="sxs-lookup"><span data-stu-id="93e30-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93e30-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93e30-109">See Also</span></span>  
 [<span data-ttu-id="93e30-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="93e30-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="93e30-111">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="93e30-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="93e30-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="93e30-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
