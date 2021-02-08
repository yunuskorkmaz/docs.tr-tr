---
description: Daha fazla bilgi için bkz. uç nokta performans sayaçları
title: Uç Noktası Performans Sayaçları
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 60cd94d5d954c87f4b37469688ee809a13fa3cb4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771242"
---
# <a name="endpoint-performance-counters"></a>Uç Noktası Performans Sayaçları

Uç nokta performans sayaçları, bir uç noktanın iletileri nasıl kabul ettiğini gösteren verileri yakalar. Performans `ServiceModelEndpoint 4.0.0.0` İzleyicisi ile görüntülenirken Performans nesnesi altında bulunabilir. Örnekler bu model kullanılarak adlandırılır:  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 Veriler tek tek işlemler için toplanmaya benzerdir, ancak yalnızca uç nokta boyunca toplanır.  
  
> [!CAUTION]
> Performans sayacı örneğinin adının uzunluğu için bir sınır vardır. Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans sayaçları](index.md)
