---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 9dd2ba5a3e94ff794d4b8a8775944355b105f790
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33482014"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="c4356-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="c4356-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="c4356-103">WS-AT protokolü hizmeti sağlanan düzenleme bağlamı kullanarak bir işleme kaydolunamadı.</span><span class="sxs-lookup"><span data-stu-id="c4356-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c4356-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4356-104">Description</span></span>  
 <span data-ttu-id="c4356-105">MSDTC verilen 2pc protokolü için bir işlem listeleme erişemediğinde izlenen.</span><span class="sxs-lookup"><span data-stu-id="c4356-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="c4356-106">Bu işlem artık, kaydetme artık izin verilir veya çok fazla kayıtlar zaten mevcut olduğundan meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="c4356-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c4356-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="c4356-107">Troubleshooting</span></span>  
 <span data-ttu-id="c4356-108">Durum dizesi herhangi bir işlem yapılabilir öğe olup olmadığını belirlemek için izleme iletisi içinde inceleyin.</span><span class="sxs-lookup"><span data-stu-id="c4356-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4356-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4356-109">See Also</span></span>  
 [<span data-ttu-id="c4356-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="c4356-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c4356-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="c4356-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c4356-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="c4356-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
