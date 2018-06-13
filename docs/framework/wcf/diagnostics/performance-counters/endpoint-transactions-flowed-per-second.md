---
title: 'Uç noktası: Saniyede Akışı Yapılan İşlem'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: ff3d76025bbae0759dba005adbd62609701c5a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471288"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="ea09e-102">Uç noktası: Saniyede Akışı Yapılan İşlem</span><span class="sxs-lookup"><span data-stu-id="ea09e-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="ea09e-103">Sayaç adı: Saniyede akışı yapılan işlemler.</span><span class="sxs-lookup"><span data-stu-id="ea09e-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ea09e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea09e-104">Description</span></span>  
 <span data-ttu-id="ea09e-105">İşlem sayısı Bu uç noktada işlemleri için bir saniyede akışı yapılan işlem.</span><span class="sxs-lookup"><span data-stu-id="ea09e-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="ea09e-106">Bu sayaç, bir işlem kimliği uç noktasına gönderilen bir ileti bulunur dilediğiniz zaman artırılır.</span><span class="sxs-lookup"><span data-stu-id="ea09e-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="ea09e-107">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="ea09e-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ea09e-108">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="ea09e-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
