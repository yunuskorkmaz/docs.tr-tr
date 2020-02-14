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
ms.openlocfilehash: 45db0e70b2446fa6e3175409bcc3844042f0acc0
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217279"
---
# <a name="notmarshalable-mda"></a>notMarshalable MDA
`notMarshalable` yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), geçerli bir kayıtlı ara sunucu/saplama olmadan bir COM arabirim işaretçisi veya bağlamı arasında arabirim sıralaması denenirken yanlış bir `IMarshal` arabirim uygulamasıyla karşılaştığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Çağrılara hizmet verilmez veya COM arabirim işaretçileri için yanlış bağlamda çağrılar oluşur.  
  
## <a name="cause"></a>Nedeni  
 Arabirim bağlamlarda hazırlanmaya çalışılırken geçerli kayıtlı ara sunucu/saplama yok ya da yanlış `IMarshal`.  
  
## <a name="resolution"></a>Çözüm  
 Kayıtlı bir ara sunucu Saplamasının olduğundan ve `IMarshal` uygulamasının geçerli olduğundan emin olun.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA çalışma zamanı üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
