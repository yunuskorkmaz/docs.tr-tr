---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 4f51777ae690178b83d353f72e63a6f2958b1592
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674589"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="fcd02-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="fcd02-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="fcd02-103">Sağlanan düzenleme bağlamı kullanarak bir işleme kaydolunamadı WS-AT protokolü hizmeti başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="fcd02-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fcd02-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd02-104">Description</span></span>  
 <span data-ttu-id="fcd02-105">MSDTC verilen 2pc protokolü için bir işlem üzerinde listeleme işlenemediğinde izlenen.</span><span class="sxs-lookup"><span data-stu-id="fcd02-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="fcd02-106">İşlem artık yok, kaydetme artık izin verilmez veya çok fazla sayıda kayıtlar zaten mevcut olduğundan bu durum ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="fcd02-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="fcd02-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="fcd02-107">Troubleshooting</span></span>  
 <span data-ttu-id="fcd02-108">Eyleme dönüştürülebilir herhangi bir öğe olup olmadığını belirlemek için izleme iletisi durumu dizede inceleyin.</span><span class="sxs-lookup"><span data-stu-id="fcd02-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd02-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcd02-109">See also</span></span>
- [<span data-ttu-id="fcd02-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="fcd02-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="fcd02-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="fcd02-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fcd02-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="fcd02-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
