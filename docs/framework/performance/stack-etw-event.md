---
title: "Yığın ETW Olayı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55219fe755f49b6edbd3b53cc686bf4f9087aa08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="stack-etw-event"></a>Yığın ETW Olayı
Yığın olayı diğer olaylar ile birlikte bir olay tetiklenir sonra Yığın izlemeleri oluşturmak için kullanılmalıdır. Çalışma zamanı sağlayıcısı etkinleştirildiğinde kaydedilir. Başka bir çalışma zamanı olay tetiklenir her tetiklenir çok sık olay olmasıdır. Bu nedenle, bu olay dikkatli bir şekilde kullanmanızı öneririz.  
  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`StackKeyword`(0x40000000)|LogAlways(0)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|Bir olay aşağıdaki Yığın izlemeleri oluşturmak için diğer olaylarla birlikte.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri Türü|Açıklama|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: Uint16|Benzersiz çalışma zamanı tanımlayıcısı.|  
|Reserved1|Win: UInt8|Ayrılmış.|  
|Ayrılmış2|Win: UInt8|Ayrılmış.|  
|FrameCount|Win: UInt32|Yığın izleme çerçevelere sayısı.|  
|Yığın|Win: işaretçi|Yönerge işaretçileri sütunlarının.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW olayları](../../../docs/framework/performance/clr-etw-events.md)
