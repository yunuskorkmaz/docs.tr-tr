---
title: notMarshalable MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30db07ddf935b5ce13b1fe4212f7f6a40270ae93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226111"
---
# <a name="notmarshalable-mda"></a>notMarshalable MDA
`notMarshalable` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) bir COM arabirimi işaretçisini geçerli kayıtlı proxy/saplama veya yanlış bir olmadan karşılaştığında etkinleştirilirse `IMarshal` arabirim çalışılırken uygulaması Arabirim bağlamlarında hazırlama.  
  
## <a name="symptoms"></a>Belirtiler  
 Çağrıları değil sunulur veya çağrı yanlış bağlamda COM arabirim işaretçileri için oluşur.  
  
## <a name="cause"></a>Sebep  
 Hiçbir geçerli kayıtlı proxy/saplama veya yanlış bir `IMarshal` bağlamlarında arabirimi sıralamakta çalışırken.  
  
## <a name="resolution"></a>Çözüm  
 Kayıtlı bir proxy saplama ve bu olduğundan emin olun `IMarshal` uygulama geçerlidir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın çalışma zamanı üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Sorunu açıklayan bir ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
