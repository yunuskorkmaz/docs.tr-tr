---
title: İşlem Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 16608132c6557f8612d42402a2cb2c49fcc29637
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566101"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="c7f08-102">İşlem Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="c7f08-102">Operation Performance Counters</span></span>
<span data-ttu-id="c7f08-103">İşlem performansı sayaçları altında bulunan `ServiceModelOperation 4.0.0.0` Performans İzleyicisi (Perfmon.exe) görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c7f08-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="c7f08-104">Her işlem, tek bir örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="c7f08-104">Each operation has an individual instance.</span></span> <span data-ttu-id="c7f08-105">Diğer bir deyişle, verilen bir sözleşme 10 işlemi varsa, 10 işlem örnekleri bu anlaşması ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="c7f08-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="c7f08-106">Nesne örneklerini şu deseni kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="c7f08-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="c7f08-107">Bu sayaç, çağrı nasıl kullanıldığını ve ne kadar iyi işlemi gerçekleştiriyor ölçmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7f08-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c7f08-108">Bir performans sayacı örneğinin adının uzunluğu üzerinde bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="c7f08-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="c7f08-109">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aşıyor, WCF örnek adının bir kısmını bir karma değer ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c7f08-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f08-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7f08-110">See also</span></span>
- [<span data-ttu-id="c7f08-111">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="c7f08-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
