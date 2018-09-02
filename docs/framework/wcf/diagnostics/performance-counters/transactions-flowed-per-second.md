---
title: Saniyede Akışı Yapılan İşlem
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392942"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="d485f-102">Saniyede Akışı Yapılan İşlem</span><span class="sxs-lookup"><span data-stu-id="d485f-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="d485f-103">Sayaç adı: Saniye başına işlemler</span><span class="sxs-lookup"><span data-stu-id="d485f-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="d485f-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d485f-104">Description</span></span>  
 <span data-ttu-id="d485f-105">İşlem sayısı, bu işleme bir saniye içinde aktarılan.</span><span class="sxs-lookup"><span data-stu-id="d485f-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="d485f-106">İşlem kimliği mevcut işleme gönderilen bir iletinin dilediğiniz zaman bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="d485f-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="d485f-107">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="d485f-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d485f-108">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="d485f-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
