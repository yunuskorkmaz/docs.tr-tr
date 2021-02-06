---
description: 'Hakkında daha fazla bilgi edinin: Microsoft. Transactions. TransactionBridge. EnlistTransactionFailure'
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: f0645d0f7bfc2787f4bce254ea8d6e3143dc0406
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644612"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="bc4db-103">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="bc4db-103">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>

<span data-ttu-id="bc4db-104">WS-AT protokol hizmeti, belirtilen düzenleme bağlamını kullanarak bir işlem üzerinde listeleme yapamadı.</span><span class="sxs-lookup"><span data-stu-id="bc4db-104">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bc4db-105">Description</span><span class="sxs-lookup"><span data-stu-id="bc4db-105">Description</span></span>  

 <span data-ttu-id="bc4db-106">MSDTC, belirli bir 2PC protokolü için bir işlemde listeleme işlemi yapamıyor.</span><span class="sxs-lookup"><span data-stu-id="bc4db-106">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="bc4db-107">İşlem artık mevcut olmadığından, en listeye artık izin verilmediği veya çok fazla sayıda liste bulunduğundan bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="bc4db-107">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="bc4db-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="bc4db-108">Troubleshooting</span></span>  

 <span data-ttu-id="bc4db-109">İşlem yapılabilir herhangi bir öğenin mevcut olup olmadığını öğrenmek için izleme iletisindeki durum dizesini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="bc4db-109">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc4db-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc4db-110">See also</span></span>

- [<span data-ttu-id="bc4db-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="bc4db-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="bc4db-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="bc4db-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="bc4db-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="bc4db-113">Administration and Diagnostics</span></span>](../index.md)
