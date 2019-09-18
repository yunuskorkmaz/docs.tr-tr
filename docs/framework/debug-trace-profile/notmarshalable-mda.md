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
ms.openlocfilehash: ddb6b0b5c2248d215245e0f881c8e7c91b13e480
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052425"
---
# <a name="notmarshalable-mda"></a>notMarshalable MDA
Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) geçerli bir kayıtlı proxy/saplama veya hatalı `IMarshal` bir arabirim uygulama olmadan bir com arabirim işaretçisi ile karşılaştığında etkinleştirilir `notMarshalable` arabirim bağlamları arasında sıralama.  
  
## <a name="symptoms"></a>Belirtiler  
 Çağrılara hizmet verilmez veya COM arabirim işaretçileri için yanlış bağlamda çağrılar oluşur.  
  
## <a name="cause"></a>Sebep  
 Geçerli kayıtlı ara sunucu/saplama yok ya da `IMarshal` arabirim bağlamlarda hazırlanmaya çalışılırken yanlış.  
  
## <a name="resolution"></a>Çözüm  
 Kayıtlı bir ara sunucu Saplamasının olduğundan ve `IMarshal` uygulamanın geçerli olduğundan emin olun.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA çalışma zamanı üzerinde hiçbir etkisi yoktur.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
