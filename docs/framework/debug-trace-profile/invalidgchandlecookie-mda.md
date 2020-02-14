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
ms.openlocfilehash: c1d8fab863c34313c0cdb778136c6f69a64defeb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216314"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie MDA
`invalidGCHandleCookie` yönetilen hata ayıklama Yardımcısı (MDA), geçersiz bir <xref:System.IntPtr> tanımlama bilgisinden <xref:System.Runtime.InteropServices.GCHandle> dönüştürme denendiğinde etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 <xref:System.IntPtr>bir <xref:System.Runtime.InteropServices.GCHandle> kullanmaya veya almaya çalışırken erişim ihlalleri ve bellek bozulması gibi tanımsız davranışlar.  
  
## <a name="cause"></a>Nedeni  
 Tanımlama bilgisi büyük olasılıkla geçersiz bir <xref:System.Runtime.InteropServices.GCHandle>, zaten serbest bırakılmış olan bir <xref:System.Runtime.InteropServices.GCHandle> temsil eder, farklı bir uygulama etki alanındaki bir <xref:System.Runtime.InteropServices.GCHandle> tanımlama bilgisidir veya yerel <xref:System.Runtime.InteropServices.GCHandle> koda bir <xref:System.IntPtr>olarak geri geçirilir, ancak bir atama denendiğinde bu şekilde CLR 'ye geçirildi.  
  
## <a name="resolution"></a>Çözüm  
 <xref:System.Runtime.InteropServices.GCHandle>için geçerli bir <xref:System.IntPtr> tanımlama bilgisi belirtin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA etkinleştirildiğinde, hata ayıklayıcı artık kök nesneleri nesnelerine geri izleyemez çünkü geri geçirilen tanımlama bilgisi değerleri, MDA etkin olmadığında döndürülmeden farklı.  
  
## <a name="output"></a>Çıktı  
 Geçersiz <xref:System.IntPtr> tanımlama bilgisi değeri bildirildi.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
