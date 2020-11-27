---
title: Saniyede Akışı Yapılan İşlem
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: b47219bd58a9b6c4401baa73177928ddca5b6a8b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254148"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="753c6-102">Saniyede Akışı Yapılan İşlem</span><span class="sxs-lookup"><span data-stu-id="753c6-102">Transactions Flowed Per Second</span></span>

<span data-ttu-id="753c6-103">Sayaç adı: saniye başına akan Işlem</span><span class="sxs-lookup"><span data-stu-id="753c6-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="753c6-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="753c6-104">Description</span></span>  

 <span data-ttu-id="753c6-105">Saniye içinde bu işleme aktarılan işlem sayısı.</span><span class="sxs-lookup"><span data-stu-id="753c6-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="753c6-106">Bu sayaç, işleme gönderilen bir iletide bir işlem KIMLIĞI olduğunda artırılır.</span><span class="sxs-lookup"><span data-stu-id="753c6-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="753c6-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="753c6-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="753c6-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="753c6-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
