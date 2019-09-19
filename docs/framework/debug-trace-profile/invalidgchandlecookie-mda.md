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
ms.openlocfilehash: 7452ae28d63c89845b45bf500c02e771f0b8f4df
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052607"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie MDA
<xref:System.Runtime.InteropServices.GCHandle> Geçersiz `invalidGCHandleCookie` bir<xref:System.IntPtr> tanımlama bilgisinden öğesine dönüştürme denendiğinde yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 <xref:System.Runtime.InteropServices.GCHandle> '<xref:System.IntPtr>Dan ' i kullanmaya veya almaya çalışırken erişim ihlalleri ve bellek bozulması gibi tanımsız davranışlar.  
  
## <a name="cause"></a>Sebep  
 Tanımlama bilgisi muhtemelen bir <xref:System.Runtime.InteropServices.GCHandle>' dan oluşturulmadığından geçersiz, zaten serbest bırakılmış olan bir <xref:System.Runtime.InteropServices.GCHandle> temsil eder, farklı bir uygulama etki alanındaki bir <xref:System.Runtime.InteropServices.GCHandle> tanımlama bilgisidir, veya yerel koda şu şekilde sıralanmış <xref:System.Runtime.InteropServices.GCHandle>ancak <xref:System.IntPtr>, bir atama denendiğinde clr 'ye geri geçirilir.  
  
## <a name="resolution"></a>Çözüm  
 İçin geçerli <xref:System.IntPtr> bir tanımlama bilgisi belirtin. <xref:System.Runtime.InteropServices.GCHandle>  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA etkinleştirildiğinde, hata ayıklayıcı artık kök nesneleri nesnelerine geri izleyemez çünkü geri geçirilen tanımlama bilgisi değerleri, MDA etkin olmadığında döndürülmeden farklı.  
  
## <a name="output"></a>Çıkış  
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
