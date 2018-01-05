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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a6aaf1e504909805a542840fe92a6591c9083d8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-calls-failed-per-second"></a>Uç Noktası: Saniyede Başarısız Olan Çağrı
Sayaç adı: Saniye başına çağrı başarısız oldu.  
  
## <a name="description"></a>Açıklama  
 Özel durum işlenmemiş ve bu bitiş noktası tarafından bir saniyede alınan çağrı sayısı.  
  
 Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)  
  
 Olduğundan her zaman bu uç noktada işlenmeyen bir özel durum, bu sayaç artırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
