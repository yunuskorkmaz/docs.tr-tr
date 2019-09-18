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
ms.openlocfilehash: c34f160b643a0431168097d3832357b4ac6e4557
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052568"
---
# <a name="invalidvariant-mda"></a>invalidVariant MDA
Yönetilen `invalidVariant` hata ayıklama Yardımcısı (MDA), yerel veya yönetilmeyen koddan `VARIANT` yönetilen koda yapılan bir çağrı sırasında geçersiz bir yapıyla karşılaşıldığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir nesnenin bir `VARIANT` nesneye sıralamasını içeren yerel ve yönetilen kod arasındaki geçiş sırasında beklenmeyen davranış.  
  
## <a name="cause"></a>Sebep  
 Yerel kod, yönetilen koda hatalı `VARIANT` biçimlendirilmiş bir yapı geçirmektedir.  Çalışma zamanı bunu `VARIANT` bir nesne için sıralama girişiminde bulunur ve geçerli değilse MDA `VARIANT` öğesini etkinleştirir. `VARIANT`Geçersiz S örnekleri, `VARIANT` `VARTYPE` VT_EMPTY &#124; VT_BYREF veya`VARIANT` withVT_VARIANT`VARTYPE` içeren bir içerir.  
  
## <a name="resolution"></a>Çözüm  
 ' İ geçirerek `VARIANT` yerel veya yönetilmeyen kod, `VARIANT` doğru şekilde oluşturulmuş ve başlatılmış olduğundan emin olmalıdır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 MDA çalışma zamanının davranışı üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Çalışma zamanının yönetilmeyen bir modül tarafından yönetilen koda geçersiz `VARIANT` şekilde geçtiğini belirten bir MDA iletisi.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
