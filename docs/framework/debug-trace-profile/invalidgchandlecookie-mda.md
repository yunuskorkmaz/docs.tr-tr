---
title: invalidGCHandleCookie MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f4cb7655d8d70cf46926cf193d6594523316e81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie MDA
`invalidGCHandleCookie` Dönüştürme, geçersiz bir'ndan yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilirse <xref:System.IntPtr> tanımlama bilgisine bir <xref:System.Runtime.InteropServices.GCHandle> denenir.  
  
## <a name="symptoms"></a>Belirtiler  
 Erişim ihlalleri ve kullanın veya almaya çalışırken Bellek Bozulması gibi davranış tanımlanmamış bir <xref:System.Runtime.InteropServices.GCHandle> gelen bir <xref:System.IntPtr>.  
  
## <a name="cause"></a>Sebep  
 İlk olarak gelen oluşturulmadığından tanımlama bilgisi büyük olasılıkla geçersiz bir <xref:System.Runtime.InteropServices.GCHandle>, temsil eden bir <xref:System.Runtime.InteropServices.GCHandle> zaten serbest, tanımlama bilgisi için bir <xref:System.Runtime.InteropServices.GCHandle> farklı uygulama etki alanındaki veya yerel koda bir olaraksıralanmış<xref:System.Runtime.InteropServices.GCHandle>CLR uygulamasına geri ancak geçirilen bir <xref:System.IntPtr>, burada bir cast yapılmaya çalışıldı.  
  
## <a name="resolution"></a>Çözüm  
 Geçerli bir belirtin <xref:System.IntPtr> için tanımlama bilgisi <xref:System.Runtime.InteropServices.GCHandle>.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA etkinleştirildiğinde, hata ayıklayıcı artık geri geçirilen tanımlama bilgisi değerleri MDA etkin değilse döndürülen olanlardan farklı olduğu için kendi nesnelere geri kökleri izleme mümkün değildir.  
  
## <a name="output"></a>Çıkış  
 Geçersiz <xref:System.IntPtr> tanımlama bilgisi değerini bildirilir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>  
 <xref:System.Runtime.InteropServices.GCHandle>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
