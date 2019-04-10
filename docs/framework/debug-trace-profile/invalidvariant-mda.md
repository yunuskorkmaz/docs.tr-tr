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
ms.openlocfilehash: 64f5a4425d70974bae8c4f7bec28041e687fe95f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228490"
---
# <a name="invalidvariant-mda"></a>invalidVariant MDA
`invalidVariant` Yönetilen hata ayıklama Yardımcısı (MDA) geçersiz olduğunda etkinleştirilir `VARIANT` yapısı, yerel veya yönetilmeyen koddan yönetilen koda çağrı sırasında karşılaşıldığında.  
  
## <a name="symptoms"></a>Belirtiler  
 Beklenmeyen davranışı, hazırlama içeren yerel ve yönetilen kod arasında geçiş sırasında bir `VARIANT` bir nesne.  
  
## <a name="cause"></a>Sebep  
 Yerel kod geçirme hatalı biçimlendirilmiş `VARIANT` yönetilen koda yapısı.  Çalışma zamanı bu sıralama dener `VARIANT` nesneye ve varsa MDA etkinleştirir `VARIANT` geçerli değil. Geçersiz örnekleri `VARIANT`S dahil bir `VARIANT` ile `VARTYPE` VT_EMPTY &#124; VT_BYREF veya `VARIANT` ile `VARTYPE` vt_varıant bekleniyordu.  
  
## <a name="resolution"></a>Çözüm  
 Yerel veya yönetilmeyen koda geçirme `VARIANT` emin olmanız gerekir `VARIANT` doğru biçimlendirilmiş ve başlatılır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 MDA çalışma zamanı davranışı üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Çalışma zamanı geçersiz algılandığını belirten bir MDA ileti `VARIANT` yönetilen kodu için yönetilmeyen bir modül tarafından geçirilen.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
