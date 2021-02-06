---
description: 'Daha fazla bilgi edinin: Işlem performansı sayaçları'
title: İşlem Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: e0a503d4d8b178d5d3f4ef240bf84c4b02a581ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655207"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="9f5d3-103">İşlem Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="9f5d3-103">Operation Performance Counters</span></span>

<span data-ttu-id="9f5d3-104">Performans `ServiceModelOperation 4.0.0.0` İzleyicisi (Perfmon.exe) ile görüntülenirken Performans nesnesi altında işlem performansı sayaçları bulunur.</span><span class="sxs-lookup"><span data-stu-id="9f5d3-104">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="9f5d3-105">Her işlemin tek bir örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="9f5d3-105">Each operation has an individual instance.</span></span> <span data-ttu-id="9f5d3-106">Diğer bir deyişle, belirli bir sözleşmede 10 işlem varsa, bu sözleşmeyle ilişkili 10 işlem sayacı örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="9f5d3-106">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="9f5d3-107">Nesne örnekleri aşağıdaki model kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="9f5d3-107">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="9f5d3-108">Bu sayaç, çağrının nasıl kullanıldığını ve işlemin ne kadar iyi çalıştığını ölçmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f5d3-108">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="9f5d3-109">Performans sayacı örneğinin adının uzunluğu için bir sınır vardır.</span><span class="sxs-lookup"><span data-stu-id="9f5d3-109">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="9f5d3-110">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9f5d3-110">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f5d3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f5d3-111">See also</span></span>

- [<span data-ttu-id="9f5d3-112">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="9f5d3-112">Performance Counters</span></span>](index.md)
