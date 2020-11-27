---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 3e4e1ff7ea8d8768c8d902dc09bd3b78646c2caf
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256332"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="a4307-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="a4307-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>

<span data-ttu-id="a4307-103">WS-AT protokol hizmeti, belirtilen düzenleme bağlamını kullanarak bir işlem üzerinde listeleme yapamadı.</span><span class="sxs-lookup"><span data-stu-id="a4307-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a4307-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4307-104">Description</span></span>  

 <span data-ttu-id="a4307-105">MSDTC, belirli bir 2PC protokolü için bir işlemde listeleme işlemi yapamıyor.</span><span class="sxs-lookup"><span data-stu-id="a4307-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="a4307-106">İşlem artık mevcut olmadığından, en listeye artık izin verilmediği veya çok fazla sayıda liste bulunduğundan bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="a4307-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a4307-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="a4307-107">Troubleshooting</span></span>  

 <span data-ttu-id="a4307-108">İşlem yapılabilir herhangi bir öğenin mevcut olup olmadığını öğrenmek için izleme iletisindeki durum dizesini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="a4307-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4307-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4307-109">See also</span></span>

- [<span data-ttu-id="a4307-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="a4307-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="a4307-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="a4307-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a4307-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="a4307-112">Administration and Diagnostics</span></span>](../index.md)
