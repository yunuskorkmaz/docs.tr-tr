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
ms.openlocfilehash: 8d686621ae4aa087e1b4f4bea9df7fc3de758d40
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216269"
---
# <a name="invalidvariant-mda"></a>invalidVariant MDA
`invalidVariant` yönetilen hata ayıklama Yardımcısı (MDA), yerel veya yönetilmeyen koddan yönetilen koda yapılan bir çağrı sırasında geçersiz bir `VARIANT` yapısına rastlana kadar etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir nesneye `VARIANT` sıralamasını içeren yerel ve yönetilen kod arasındaki geçiş sırasında beklenmeyen davranış.  
  
## <a name="cause"></a>Nedeni  
 Yerel kod, yönetilen koda hatalı biçimlendirilmiş `VARIANT` yapısını geçiyor.  Çalışma zamanı bu `VARIANT` bir nesneye sıralama girişiminde bulunur ve `VARIANT` geçerli değilse MDA 'ı etkinleştirir. Geçersiz `VARIANT`örnekleri, `VARTYPE` VT_EMPTY &#124; VT_BYREF veya `VARIANT` `VARTYPE` bir VT_VARIANT içeren bir `VARIANT` içerir.  
  
## <a name="resolution"></a>Çözüm  
 `VARIANT` geçirerek yerel veya yönetilmeyen kod, `VARIANT` doğru şekilde oluşturulmuş ve başlatılmış olduğundan emin olmalıdır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 MDA çalışma zamanının davranışı üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 Çalışma zamanının yönetilmeyen bir modül tarafından yönetilen koda geçirilen geçersiz bir `VARIANT` algıladığını belirten bir MDA iletisi.  
  
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
