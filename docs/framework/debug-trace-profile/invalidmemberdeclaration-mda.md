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
ms.openlocfilehash: 6033cd4178b2bc493794b5dcc527bc543ba24284
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216291"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA
`invalidMemberDeclaration` yönetilen hata ayıklama Yardımcısı (MDA), COM 'dan çağrılacak bir üyenin parametrelerinin nasıl hazırlanacağını belirlerken oluşan bir hatayı raporlamak için etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Yönetilen yöntem çağrılmadan COM 'a bir hata HRESULT döndürülür.  
  
## <a name="cause"></a>Nedeni  
 Bunun nedeni, parametrelerden birindeki uyumsuz bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği olabilir.  
  
## <a name="resolution"></a>Çözüm  
 Parametrelerde geçerli <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliklerini belirtin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
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
