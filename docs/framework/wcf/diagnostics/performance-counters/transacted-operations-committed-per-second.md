---
title: Uygulaması Yapılan İşlem/Saniye
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 3bec51a7be63c54a240b85032ecac09b87173393
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474278"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="a40e2-102">Uygulaması Yapılan İşlem/Saniye</span><span class="sxs-lookup"><span data-stu-id="a40e2-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="a40e2-103">Sayaç adı: Saniye başına uygulaması yapılan işlemler.</span><span class="sxs-lookup"><span data-stu-id="a40e2-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a40e2-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a40e2-104">Description</span></span>  
 <span data-ttu-id="a40e2-105">Bir saniyede bu hizmette kabul edilen işlem işlemlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="a40e2-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="a40e2-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="a40e2-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a40e2-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="a40e2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
