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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbb33d2cddab22ad2072354ba543d2cd6a60a668
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218283"
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate MDA
`invalidFunctionPointerInDelegate` Yönetilen hata ayıklama Yardımcısı (MDA) bir yerel işlev işaretçisi bir temsilci oluşturmak için bir geçersiz işlev işaretçisi geçtikten sonra etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Erişim ihlalleri veya bir temsilci bir işlev işaretçisi kullanılırken beklenmeyen Bellek Bozulması.  
  
## <a name="cause"></a>Sebep  
 Geçersiz işlev işaretçi belirtildi.  
  
## <a name="resolution"></a>Çözüm  
 Geçerli işlev işaretçisi belirtin  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
