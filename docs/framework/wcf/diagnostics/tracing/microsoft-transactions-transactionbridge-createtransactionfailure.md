---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: 947391e0594ffddba8235c519a076d330b73d4d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632640"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="44b9d-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="44b9d-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="44b9d-103">İşlem oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="44b9d-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="44b9d-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44b9d-104">Description</span></span>  
 <span data-ttu-id="44b9d-105">Bu izleme, MSDTC işlem oluşturamıyor olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="44b9d-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="44b9d-106">Bu, kaynak yetersizliği, yetersiz günlük alanı veya diğer hatalar nedeniyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="44b9d-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="44b9d-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="44b9d-107">Troubleshooting</span></span>  
 <span data-ttu-id="44b9d-108">Eyleme dönüştürülebilir herhangi bir öğe olup olmadığını belirlemek için izleme iletisi durumu dizede inceleyin.</span><span class="sxs-lookup"><span data-stu-id="44b9d-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b9d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44b9d-109">See also</span></span>
- [<span data-ttu-id="44b9d-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="44b9d-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="44b9d-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="44b9d-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="44b9d-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="44b9d-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
