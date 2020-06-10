---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 742e80a3115e8f8caa728e0d8c460ee8b964ddc9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84588723"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="54e42-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="54e42-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="54e42-103">WS-AT protokol hizmeti, belirtilen düzenleme bağlamını kullanarak bir işlem üzerinde listeleme yapamadı.</span><span class="sxs-lookup"><span data-stu-id="54e42-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="54e42-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54e42-104">Description</span></span>  
 <span data-ttu-id="54e42-105">MSDTC, belirli bir 2PC protokolü için bir işlemde listeleme işlemi yapamıyor.</span><span class="sxs-lookup"><span data-stu-id="54e42-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="54e42-106">İşlem artık mevcut olmadığından, en listeye artık izin verilmediği veya çok fazla sayıda liste bulunduğundan bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="54e42-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="54e42-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="54e42-107">Troubleshooting</span></span>  
 <span data-ttu-id="54e42-108">İşlem yapılabilir herhangi bir öğenin mevcut olup olmadığını öğrenmek için izleme iletisindeki durum dizesini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="54e42-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e42-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54e42-109">See also</span></span>

- [<span data-ttu-id="54e42-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="54e42-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="54e42-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="54e42-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="54e42-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="54e42-112">Administration and Diagnostics</span></span>](../index.md)
