---
title: invalidVariant MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ee537dcb03dc76968b829f827c73542c07922a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)
