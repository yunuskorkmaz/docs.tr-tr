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
# <a name="operation-performance-counters"></a>İşlem Performansı Sayaçları

Performans `ServiceModelOperation 4.0.0.0` İzleyicisi (Perfmon.exe) ile görüntülenirken Performans nesnesi altında işlem performansı sayaçları bulunur. Her işlemin tek bir örneği vardır. Diğer bir deyişle, belirli bir sözleşmede 10 işlem varsa, bu sözleşmeyle ilişkili 10 işlem sayacı örneği vardır. Nesne örnekleri aşağıdaki model kullanılarak adlandırılır:  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 Bu sayaç, çağrının nasıl kullanıldığını ve işlemin ne kadar iyi çalıştığını ölçmenize olanak sağlar.  
  
> [!CAUTION]
> Performans sayacı örneğinin adının uzunluğu için bir sınır vardır. Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans sayaçları](index.md)
