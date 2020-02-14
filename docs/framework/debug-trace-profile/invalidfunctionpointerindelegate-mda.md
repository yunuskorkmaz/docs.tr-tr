---
title: invalidFunctionPointerInDelegate MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
ms.openlocfilehash: 723f51e14c314bde40c34d629ba7fc4f6276c633
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217372"
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate MDA
`invalidFunctionPointerInDelegate` yönetilen hata ayıklama Yardımcısı (MDA), bir yerel işlev işaretçisi üzerinden temsilci oluşturmak için geçersiz bir işlev işaretçisi geçirildiğinde etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir işlev işaretçisi üzerinde bir temsilci kullanılırken erişim ihlalleri veya beklenmedik bellek bozulması.  
  
## <a name="cause"></a>Nedeni  
 Geçersiz bir işlev işaretçisi belirtildi.  
  
## <a name="resolution"></a>Çözüm  
 Geçerli bir işlev işaretçisi belirtin  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 Geçersiz işlev işaretçisi.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
