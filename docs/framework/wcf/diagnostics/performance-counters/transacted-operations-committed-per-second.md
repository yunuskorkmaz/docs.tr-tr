---
title: Uygulaması Yapılan İşlem/Saniye
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 124eae3b36a731ac50a147782b19c87e3adfa7be
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856328"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="232ac-102">Uygulaması Yapılan İşlem/Saniye</span><span class="sxs-lookup"><span data-stu-id="232ac-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="232ac-103">Sayaç adı: Saniye başına operasyonlar.</span><span class="sxs-lookup"><span data-stu-id="232ac-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="232ac-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="232ac-104">Description</span></span>  
 <span data-ttu-id="232ac-105">Bir saniye içinde bu hizmet kabul edilen işlem alt işlemlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="232ac-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="232ac-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="232ac-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="232ac-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="232ac-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
