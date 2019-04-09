---
title: invalidGCHandleCookie MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 876f0fe3c40cb6754b4ba714833dd160dc4de3a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176962"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie MDA
`invalidGCHandleCookie` Yönetilen hata ayıklama Yardımcısı (MDA) etkin olduğu bir dönüştürme, geçersiz bir'den <xref:System.IntPtr> tanımlama bilgisi için bir <xref:System.Runtime.InteropServices.GCHandle> denenir.  
  
## <a name="symptoms"></a>Belirtiler  
 Tanımsız davranış erişim ihlalleri ve kullanın veya almaya çalışırken Bellek Bozulması gibi bir <xref:System.Runtime.InteropServices.GCHandle> gelen bir <xref:System.IntPtr>.  
  
## <a name="cause"></a>Sebep  
 Bu ilk olarak oluşturulduğu değil çünkü tanımlama bilgisinin büyük olasılıkla geçersiz bir <xref:System.Runtime.InteropServices.GCHandle>, temsil eder bir <xref:System.Runtime.InteropServices.GCHandle> önce serbest bırakılmış, bir tanımlama bilgisi için bir <xref:System.Runtime.InteropServices.GCHandle> farklı uygulama etki alanında veya bir olarakyerelkodiçinsıralanmış<xref:System.Runtime.InteropServices.GCHandle>CLR yeniden içine geçirilen ancak bir <xref:System.IntPtr>, burada bir tür dönüştürme yapılmaya çalışıldı.  
  
## <a name="resolution"></a>Çözüm  
 Geçerli <xref:System.IntPtr> için tanımlama bilgisi <xref:System.Runtime.InteropServices.GCHandle>.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu MDA etkinleştirildiğinde, hata ayıklayıcı artık köklerine nesnelerine geri geçirilen tanımlama bilgisi değerleri MDA etkinleştirilmediğinde döndürülen olanlardan farklı olduğundan izleme mümkün değildir.  
  
## <a name="output"></a>Çıkış  
 Geçersiz <xref:System.IntPtr> tanımlama bilgisi değeri raporlanır.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
