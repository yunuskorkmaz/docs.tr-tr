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
# <a name="operation-performance-counters"></a>İşlem Performansı Sayaçları
İşlem performansı sayaçları altında bulunan `ServiceModelOperation 4.0.0.0` Performans İzleyicisi (Perfmon.exe) görüntülerken Performans nesnesi. Her işlem, tek bir örneği vardır. Diğer bir deyişle, verilen bir sözleşme 10 işlemi varsa, 10 işlem örnekleri bu anlaşması ile ilişkilidir. Nesne örneklerini şu deseni kullanılarak adlandırılır:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Bu sayaç, çağrı nasıl kullanıldığını ve ne kadar iyi işlemi gerçekleştiriyor ölçmek sağlar.  
  
> [!CAUTION]
>  Bir performans sayacı örneğinin adının uzunluğu üzerinde bir sınır yoktur. Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aşıyor, WCF örnek adının bir kısmını bir karma değer ile değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Performans Sayaçları](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
