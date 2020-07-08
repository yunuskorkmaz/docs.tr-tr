---
title: invalidFunctionPointerInDelegate MDA
description: Temsilci oluşturmak için geçersiz bir işlev işaretçisi geçirilirse çağrılan ınvalidfunctionpointerındelegate yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
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
ms.openlocfilehash: a17427d117c62ba782af3c9549c84623a3013b06
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051746"
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate MDA
`invalidFunctionPointerInDelegate`Yönetilen hata ayıklama Yardımcısı (MDA), bir yerel işlev işaretçisi üzerinden temsilci oluşturmak için geçersiz bir işlev işaretçisi geçirildiğinde etkinleştirilir.  
  
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
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
