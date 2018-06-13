---
title: Uygulanıp Durdurulan İşlem/Saniye
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: dacdf93f4610df9161134a41ece19fd2a18637c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474538"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="e5a0b-102">Uygulanıp Durdurulan İşlem/Saniye</span><span class="sxs-lookup"><span data-stu-id="e5a0b-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="e5a0b-103">Sayaç adı: Saniye başına Durdurulan işlem hareket gerçekleşti.</span><span class="sxs-lookup"><span data-stu-id="e5a0b-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e5a0b-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5a0b-104">Description</span></span>  
 <span data-ttu-id="e5a0b-105">Bu hizmet bir saniye içinde iptal edildi işlem işlemlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="e5a0b-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="e5a0b-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="e5a0b-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e5a0b-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="e5a0b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
