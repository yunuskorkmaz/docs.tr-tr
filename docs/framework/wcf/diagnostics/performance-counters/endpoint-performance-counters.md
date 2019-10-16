---
title: Uç Noktası Performans Sayaçları
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 1b0f7462fea8843bcb0a0938a8034f405f30a6fb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320509"
---
# <a name="endpoint-performance-counters"></a>Uç Noktası Performans Sayaçları
Uç nokta performans sayaçları, bir uç noktanın iletileri nasıl kabul ettiğini gösteren verileri yakalar. Performans Izleyicisi ile görüntülenirken `ServiceModelEndpoint 4.0.0.0` performans nesnesi altında bulunabilir. Örnekler bu model kullanılarak adlandırılır:  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 Veriler tek tek işlemler için toplanmaya benzerdir, ancak yalnızca uç nokta boyunca toplanır.  
  
> [!CAUTION]
> Performans sayacı örneğinin adının uzunluğu için bir sınır vardır. Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans Sayaçları](index.md)
