---
title: "Çekişme ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d739eaf73ff8336e74130d7176697229fdffd12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="contention-etw-events"></a>Çekişme ETW Olayları
Çekişme olayları için Çekişme olduğunda ortaya <xref:System.Threading.Monitor?displayProperty=nameWithType> kilitleri ya da çalışma zamanı tarafından kullanılan yerel kilitler. Çakışma, başka bir iş parçacığı kilidi sahip olduğu sırada bir kilidi için bekleyen bir iş parçacığı oluşur.  
  
 Aşağıdaki tabloda altında Çekişme olayları yükseltildiği anahtar sözcüğü ve olayları düzeyini gösterir. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ContentionKeyword`(0x4000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|81|Çekişme başlatır. Bu olay, bir iş parçacığı bir kilidi bekler önce geçen süre dönmesini miktarını içermez; yalnızca bir kilit edinmeye iş parçacığı bekler yapıldığında oluşturulur.|  
|`ContentionStop`|81|Çekişme sona erer.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Bayraklar|Win: UInt8|için 0 yönetilen; Yerel için 1.|  
|ClrInstanceID|Win: UInt16|CLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW olayları](../../../docs/framework/performance/clr-etw-events.md)
