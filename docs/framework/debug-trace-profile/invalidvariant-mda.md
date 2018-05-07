---
title: invalidVariant MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 426b9df449b12d2f34fa70fc721cc050fa3e4ddd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="invalidvariant-mda"></a>invalidVariant MDA
`invalidVariant` Yönetilen hata ayıklama Yardımcısı (MDA) geçersiz bir zaman etkinleştirilirse `VARIANT` yerel veya yönetilmeyen koddan yönetilen koda çağrı sırasında yapısı karşılaştı.  
  
## <a name="symptoms"></a>Belirtiler  
 Beklenmeyen bir davranış, hazırlama içeren yerel ve yönetilen kod arasında geçiş sırasında bir `VARIANT` nesneye.  
  
## <a name="cause"></a>Sebep  
 Yerel kod geçirme hatalı biçimlendirilmiş `VARIANT` yönetilen kod yapısına.  Çalışma zamanı bu sıralama girişiminde `VARIANT` nesneye ve varsa MDA'ı etkinleştirir `VARIANT` geçerli değil. Geçersiz örnekleri `VARIANT`S içeren bir `VARIANT` ile `VARTYPE` VT_EMPTY &#124; VT_BYREF veya `VARIANT` ile `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Çözüm  
 Geçirme yerel veya yönetilmeyen kod `VARIANT` emin olmanız gerekir `VARIANT` doğru biçimlendirilmiş ve başlatıldı.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 MDA çalışma zamanı davranışı üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Çalışma zamanı geçersiz algılanan belirten bir MDA ileti `VARIANT` yönetilmeyen bir modül tarafından yönetilen koda geçirildi.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
