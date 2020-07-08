---
title: invalidMemberDeclaration MDA
description: Yönetilen yöntemi çağırmadan COM 'a bir hata HRESULT döndürülürse çağrılan ınvalidmemberdeclaration yönetilen hata ayıklama Yardımcısı ' nı gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: 5dbfba2baec3263d91746c06379438e97a81f005
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051720"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA
`invalidMemberDeclaration`Yönetilen hata ayıklama Yardımcısı (MDA), com 'dan çağrılacak bir üyenin parametrelerinin nasıl hazırlanacağını belirlerken oluşan bir hatayı raporlamak için etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Yönetilen yöntem çağrılmadan COM 'a bir hata HRESULT döndürülür.  
  
## <a name="cause"></a>Nedeni  
 Bunun nedeni büyük olasılıkla parametrelerden birindeki uyumsuz bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliktir.  
  
## <a name="resolution"></a>Çözüm  
 Parametrelerde geçerli <xref:System.Runtime.InteropServices.MarshalAsAttribute> öznitelikleri belirtin.  
  
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
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
