---
title: "Uç Noktası: Saniyede Başarısız Olan Çağrı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5da436c5e8159ff922c36172490a28e854bbee8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-calls-failed-per-second"></a>Uç Noktası: Saniyede Başarısız Olan Çağrı
Sayaç adı: Saniye başına çağrı başarısız oldu.  
  
## <a name="description"></a>Açıklama  
 Özel durum işlenmemiş ve bu bitiş noktası tarafından bir saniyede alınan çağrı sayısı.  
  
 Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)  
  
 Olduğundan her zaman bu uç noktada işlenmeyen bir özel durum, bu sayaç artırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Belirtme ve sözleşme ve hizmetlerde hataları işleme](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
