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
# <a name="operation-performance-counters"></a>İşlem Performansı Sayaçları
İşlem performansı sayaçları altında bulunan `ServiceModelOperation 4.0.0.0` Performans İzleyicisi (Perfmon.exe) görüntülerken Performans nesnesi. Her işlem tek bir örneği vardır. Diğer bir deyişle, belirli bir sözleşme 10 işlemler varsa, 10 işlemi örnekleri bu sözleşme ile ilişkilendirilmiş. Nesne örneklerini şu biçimi kullanarak adlandırılır:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Bu sayaç, çağrı nasıl kullanıldığını ve ne kadar iyi işlemi gerçekleştiren ölçmek sağlar.  
  
> [!CAUTION]
>  Bir performans sayacı örneğinin adının uzunluğu bir sınırı yoktur. Zaman bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sayaç örneği adı en fazla uzunluğu aşıyor [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] örnek adının bir kısmını karma değeri ile değiştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans sayaçları](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
