---
title: "İşlem Performansı Sayaçları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83460e1c4db17938466051269dbeba3f19e0b40a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="operation-performance-counters"></a><span data-ttu-id="15095-102">İşlem Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="15095-102">Operation Performance Counters</span></span>
<span data-ttu-id="15095-103">İşlem performansı sayaçları altında bulunan `ServiceModelOperation 4.0.0.0` Performans İzleyicisi (Perfmon.exe) görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="15095-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="15095-104">Her işlem tek bir örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="15095-104">Each operation has an individual instance.</span></span> <span data-ttu-id="15095-105">Diğer bir deyişle, belirli bir sözleşme 10 işlemler varsa, 10 işlemi örnekleri bu sözleşme ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="15095-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="15095-106">Nesne örneklerini şu biçimi kullanarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="15095-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="15095-107">Bu sayaç, çağrı nasıl kullanıldığını ve ne kadar iyi işlemi gerçekleştiren ölçmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="15095-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="15095-108">Bir performans sayacı örneğinin adının uzunluğu bir sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="15095-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="15095-109">Zaman bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sayaç örneği adı en fazla uzunluğu aşıyor [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] örnek adının bir kısmını karma değeri ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="15095-109">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15095-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15095-110">See Also</span></span>  
 [<span data-ttu-id="15095-111">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="15095-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
