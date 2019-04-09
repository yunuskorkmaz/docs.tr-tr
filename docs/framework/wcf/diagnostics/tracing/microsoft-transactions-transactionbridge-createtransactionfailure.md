---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: 968444947714315bae902d3d038129c5b8a04cf2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082522"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="3501f-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="3501f-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="3501f-103">İşlem oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="3501f-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3501f-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3501f-104">Description</span></span>  
 <span data-ttu-id="3501f-105">Bu izleme, MSDTC işlem oluşturamıyor olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3501f-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="3501f-106">Bu, kaynak yetersizliği, yetersiz günlük alanı veya diğer hatalar nedeniyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="3501f-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="3501f-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="3501f-107">Troubleshooting</span></span>  
 <span data-ttu-id="3501f-108">Eyleme dönüştürülebilir herhangi bir öğe olup olmadığını belirlemek için izleme iletisi durumu dizede inceleyin.</span><span class="sxs-lookup"><span data-stu-id="3501f-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3501f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3501f-109">See also</span></span>

- [<span data-ttu-id="3501f-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="3501f-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="3501f-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="3501f-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="3501f-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="3501f-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
