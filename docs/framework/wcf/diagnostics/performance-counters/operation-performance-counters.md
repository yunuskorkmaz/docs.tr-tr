---
title: İşlem Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 01f3ed7b2722f7ff4bdbb50e352920bdc277330f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295241"
---
# <a name="operation-performance-counters"></a>İşlem Performansı Sayaçları

Performans `ServiceModelOperation 4.0.0.0` İzleyicisi (Perfmon.exe) ile görüntülenirken Performans nesnesi altında işlem performansı sayaçları bulunur. Her işlemin tek bir örneği vardır. Diğer bir deyişle, belirli bir sözleşmede 10 işlem varsa, bu sözleşmeyle ilişkili 10 işlem sayacı örneği vardır. Nesne örnekleri aşağıdaki model kullanılarak adlandırılır:  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 Bu sayaç, çağrının nasıl kullanıldığını ve işlemin ne kadar iyi çalıştığını ölçmenize olanak sağlar.  
  
> [!CAUTION]
> Performans sayacı örneğinin adının uzunluğu için bir sınır vardır. Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans sayaçları](index.md)
