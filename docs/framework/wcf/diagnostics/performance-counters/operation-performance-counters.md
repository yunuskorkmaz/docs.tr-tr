---
title: İşlem Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 31b0f92ae3477bd3c1de8c348a60e5c64d7c53cc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855687"
---
# <a name="operation-performance-counters"></a>İşlem Performansı Sayaçları
Performans İzleyicisi (Perfmon. exe) `ServiceModelOperation 4.0.0.0` ile görüntülenirken Performans nesnesi altında işlem performansı sayaçları bulunur. Her işlemin tek bir örneği vardır. Diğer bir deyişle, belirli bir sözleşmede 10 işlem varsa, bu sözleşmeyle ilişkili 10 işlem sayacı örneği vardır. Nesne örnekleri aşağıdaki model kullanılarak adlandırılır:  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 Bu sayaç, çağrının nasıl kullanıldığını ve işlemin ne kadar iyi çalıştığını ölçmenize olanak sağlar.  
  
> [!CAUTION]
> Performans sayacı örneğinin adının uzunluğu için bir sınır vardır. Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans Sayaçları](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
