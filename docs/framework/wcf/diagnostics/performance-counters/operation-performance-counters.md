---
title: İşlem Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: d4f5755129fecb62e6a4da98a2bf642c5e20f9c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077114"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="ea33b-102">İşlem Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="ea33b-102">Operation Performance Counters</span></span>
<span data-ttu-id="ea33b-103">İşlem performansı sayaçları altında bulunan `ServiceModelOperation 4.0.0.0` Performans İzleyicisi (Perfmon.exe) görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ea33b-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="ea33b-104">Her işlem, tek bir örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="ea33b-104">Each operation has an individual instance.</span></span> <span data-ttu-id="ea33b-105">Diğer bir deyişle, verilen bir sözleşme 10 işlemi varsa, 10 işlem örnekleri bu anlaşması ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="ea33b-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="ea33b-106">Nesne örneklerini şu deseni kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="ea33b-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="ea33b-107">Bu sayaç, çağrı nasıl kullanıldığını ve ne kadar iyi işlemi gerçekleştiriyor ölçmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea33b-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ea33b-108">Bir performans sayacı örneğinin adının uzunluğu üzerinde bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="ea33b-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="ea33b-109">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aşıyor, WCF örnek adının bir kısmını bir karma değer ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ea33b-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea33b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea33b-110">See also</span></span>

- [<span data-ttu-id="ea33b-111">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="ea33b-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
