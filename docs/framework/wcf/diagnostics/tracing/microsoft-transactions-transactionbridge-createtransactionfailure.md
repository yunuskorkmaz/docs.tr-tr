---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: 09b93ce4b72416cfea9f8c9850fd1e50c77035b7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270230"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="42d57-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="42d57-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>

<span data-ttu-id="42d57-103">İşlem oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="42d57-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="42d57-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42d57-104">Description</span></span>  

 <span data-ttu-id="42d57-105">Bu izleme, MSDTC tarafından bir işlem oluşturulmadığı zaman üretilir.</span><span class="sxs-lookup"><span data-stu-id="42d57-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="42d57-106">Bu, düşük kaynak, yetersiz günlük alanı veya diğer hatalardan kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="42d57-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="42d57-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="42d57-107">Troubleshooting</span></span>  

 <span data-ttu-id="42d57-108">İşlem yapılabilir herhangi bir öğenin mevcut olup olmadığını öğrenmek için izleme iletisindeki durum dizesini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="42d57-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42d57-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42d57-109">See also</span></span>

- [<span data-ttu-id="42d57-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="42d57-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="42d57-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="42d57-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="42d57-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="42d57-112">Administration and Diagnostics</span></span>](../index.md)
