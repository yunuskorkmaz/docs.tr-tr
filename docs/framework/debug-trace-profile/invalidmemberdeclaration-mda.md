---
title: invalidMemberDeclaration MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe15d718a9c5f91bfae4f37c04e726990e2fbd45
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052579"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA
Yönetilen `invalidMemberDeclaration` hata ayıklama Yardımcısı (MDA), com 'dan çağrılacak bir üyenin parametrelerinin nasıl hazırlanacağını belirlerken oluşan bir hatayı raporlamak için etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Yönetilen yöntem çağrılmadan COM 'a bir hata HRESULT döndürülür.  
  
## <a name="cause"></a>Sebep  
 Bunun nedeni büyük olasılıkla parametrelerden birindeki uyumsuz <xref:System.Runtime.InteropServices.MarshalAsAttribute> bir özniteliktir.  
  
## <a name="resolution"></a>Çözüm  
 Parametrelerde geçerli <xref:System.Runtime.InteropServices.MarshalAsAttribute> öznitelikleri belirtin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Üye adı, tür adı ve hata iletisi içeren bilgilendirici bir ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
