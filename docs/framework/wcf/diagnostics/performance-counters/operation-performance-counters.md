---
title: İşlem Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 652090cd7f8728deadba580fd33897b1e4ed2ecb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="operation-performance-counters"></a>İşlem Performansı Sayaçları
İşlem performansı sayaçları altında bulunan `ServiceModelOperation 4.0.0.0` Performans İzleyicisi (Perfmon.exe) görüntülerken Performans nesnesi. Her işlem tek bir örneği vardır. Diğer bir deyişle, belirli bir sözleşme 10 işlemler varsa, 10 işlemi örnekleri bu sözleşme ile ilişkilendirilmiş. Nesne örneklerini şu biçimi kullanarak adlandırılır:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Bu sayaç, çağrı nasıl kullanıldığını ve ne kadar iyi işlemi gerçekleştiren ölçmek sağlar.  
  
> [!CAUTION]
>  Bir performans sayacı örneğinin adının uzunluğu bir sınırı yoktur. Bir Windows Communication Foundation (WCF) sayaç örneği adı uzunluk sınırını aşarsa [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] örnek adının bir kısmını karma değeri ile değiştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Sayaçları](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
