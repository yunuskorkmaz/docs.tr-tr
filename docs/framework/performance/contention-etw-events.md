---
title: Çekişme ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90beb1487581ff4c031d6f10fb613430207dc026
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575573"
---
# <a name="contention-etw-events"></a>Çekişme ETW Olayları
Çekişme olayları oluştuğunda için Çekişme olduğunda <xref:System.Threading.Monitor?displayProperty=nameWithType> kilitler veya çalışma zamanı tarafından kullanılan yerel kilitler. Başka bir iş parçacığı kilit sahip olduğu sırada bir kilit için bekleyen bir iş parçacığı Çekişme gerçekleşir.  
  
 Çekişme olayları altında oluşturulan anahtar sözcüğü ve olayları düzeyi aşağıdaki tabloda gösterilmektedir. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ContentionKeyword` (0x4000)|Bilgilendirici (4)|  
  
 Aşağıdaki tablo, olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|81|Çekişme başlatır. Bu olay, dönen bir iş parçacığı kilit için bekleyen önceki süre miktarını içermez; yalnızca iş parçacığının bir kilidi bekler olduğunda tetiklenir.|  
|`ContentionStop`|81|Çekişme sona erer.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Bayraklar|Kazanma: UInt8|0 için yönetilen; Yerel için 1.|  
|ClrInstanceID|Kazanma: UInt16|CLR örneği için benzersiz kimliği.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
