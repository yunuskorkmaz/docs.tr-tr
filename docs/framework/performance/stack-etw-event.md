---
title: Yığın ETW Olayı
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7cba2bd1dd5b83e29c7a6c192a1a7e5e2d33ecc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076487"
---
# <a name="stack-etw-event"></a>Yığın ETW Olayı
Yığın olayı diğer olayları ile birlikte bir olay tetiklenir sonra yığın izlemelerini oluşturmak için kullanılmalıdır. Çalışma zamanı sağlayıcısı etkin olduğunda günlüğe kaydedilir. Başka bir çalışma zamanı olayı her oluşturulur çünkü bir çok yüksek sıklık düzeyi olay budur. Bu nedenle, bu olay dikkatli kullanmanızı öneririz.  
  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`StackKeyword` (0x40000000)|LogAlways(0)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|Yığın izlemelerini izleyerek bir olay oluşturmak için diğer olaylarla birlikte.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri Türü|Açıklama|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Kazanma: Uint16|Benzersiz bir çalışma zamanı tanımlayıcısı.|  
|Reserved1|Kazanma: UInt8|Ayrılmış.|  
|Ayrılmış2|Kazanma: UInt8|Ayrılmış.|  
|FrameCount|Kazanma: UInt32|Yığın izleme çerçeve sayısı.|  
|Yığın|Kazanma: işaretçi|Yönerge işaretçileri sütunlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
