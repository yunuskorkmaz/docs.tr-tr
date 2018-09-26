---
title: 'Uç noktası: Saniyede Akışı Yapılan İşlem'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47194095"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="10de1-102">Uç noktası: Saniyede Akışı Yapılan İşlem</span><span class="sxs-lookup"><span data-stu-id="10de1-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="10de1-103">Sayaç adı: Saniyede akışı yapılan işlemler.</span><span class="sxs-lookup"><span data-stu-id="10de1-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="10de1-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10de1-104">Description</span></span>  
 <span data-ttu-id="10de1-105">İşlem sayısı işlemlerine Bu uç noktada bir saniye içinde aktarılan.</span><span class="sxs-lookup"><span data-stu-id="10de1-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="10de1-106">İşlem kimliği mevcut uç nokta için gönderilen bir iletinin dilediğiniz zaman bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="10de1-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="10de1-107">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="10de1-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="10de1-108">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="10de1-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
