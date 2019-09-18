---
title: Yığın ETW Olayı
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5dc23f5105b589d5b74c9ea6b7f40b84c2b04e6a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046163"
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
|Reserved1|Win: UInt8|Ayrılamadı.|  
|Reserved2|Win: UInt8|Ayrılamadı.|  
|FrameCount|Win: UInt32|Yığın izlemesinde çerçeve sayısı.|  
|Yığın|Win: Işaretçi|Yönerge işaretçilerinin sütunları.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
