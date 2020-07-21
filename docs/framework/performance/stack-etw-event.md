---
title: Yığın ETW Olayı
description: Bir olay oluşturulduktan sonra yığın izlemeleri oluşturmak için diğer olaylarla birlikte kullanılması gereken Stack ETW olayı hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: cab496615c4ef17831895b72c8987917e3c06e77
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474143"
---
# <a name="stack-etw-event"></a>Yığın ETW Olayı
Yığın olayı, bir olay oluşturulduktan sonra yığın izlemeleri oluşturmak için diğer olaylarla birlikte kullanılmalıdır. Çalışma zamanı sağlayıcısı etkinleştirildiğinde günlüğe kaydedilir. Bu çok yüksek bir sıklık olayıdır, çünkü başka bir çalışma zamanı olayı oluşturulduğunda tetiklenir. Bu nedenle, bu olayı dikkatli kullanmanızı öneririz.  
  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir. (Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`StackKeyword`0x40000000|LogAlways (0)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|Bir olayı izleyen yığın izlemeleri oluşturmak için diğer olaylarla birlikte.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri Türü|Açıklama|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: uint16|Benzersiz çalışma zamanı tanımlayıcısı.|  
|Reserved1|Win: UInt8|Ayrılmış.|  
|Reserved2|Win: UInt8|Ayrılmış.|  
|FrameCount|Win: UInt32|Yığın izlemesinde çerçeve sayısı.|  
|Yığın|Win: Işaretçi|Yönerge işaretçilerinin sütunları.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
