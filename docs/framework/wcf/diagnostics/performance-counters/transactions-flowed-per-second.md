---
description: 'Hakkında daha fazla bilgi edinin: saniye başına aktarılan Işlem'
title: Saniyede Akışı Yapılan İşlem
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: f37c79e89efb8a013719f44350772919b7222a61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771008"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="8d551-103">Saniyede Akışı Yapılan İşlem</span><span class="sxs-lookup"><span data-stu-id="8d551-103">Transactions Flowed Per Second</span></span>

<span data-ttu-id="8d551-104">Sayaç adı: saniye başına akan Işlem</span><span class="sxs-lookup"><span data-stu-id="8d551-104">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="8d551-105">Description</span><span class="sxs-lookup"><span data-stu-id="8d551-105">Description</span></span>  

 <span data-ttu-id="8d551-106">Saniye içinde bu işleme aktarılan işlem sayısı.</span><span class="sxs-lookup"><span data-stu-id="8d551-106">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="8d551-107">Bu sayaç, işleme gönderilen bir iletide bir işlem KIMLIĞI olduğunda artırılır.</span><span class="sxs-lookup"><span data-stu-id="8d551-107">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="8d551-108">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="8d551-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8d551-109">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="8d551-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
