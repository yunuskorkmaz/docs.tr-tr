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
ms.openlocfilehash: 4e5b4cb4a04a79a748f4ea2292bac67a88a6e9f8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131293"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA
`invalidMemberDeclaration` Yönetilen hata ayıklama Yardımcısı (MDA) nasıl hazırlanacağını COM'dan çağrılacak üye parametrelerinin belirlenirken oluşan bir hatayı raporlamak için etkinleştirildi  
  
## <a name="symptoms"></a>Belirtiler  
 Bir hata HRESULT adlı Yönetilen yöntemi COM döndürülür.  
  
## <a name="cause"></a>Sebep  
 Uyumsuz bir nedeni büyük olasılıkla budur <xref:System.Runtime.InteropServices.MarshalAsAttribute> parametrelerden biri özniteliği.  
  
## <a name="resolution"></a>Çözüm  
 Geçerli belirtin <xref:System.Runtime.InteropServices.MarshalAsAttribute> parametreleri öznitelikleri.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Üye adı, tür adı ve hata iletisi içeren bir bilgi iletisidir.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
