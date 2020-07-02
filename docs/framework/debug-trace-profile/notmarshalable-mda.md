---
title: notMarshalable MDA
description: NotMarshalable yönetilen hata ayıklama Yardımcısı ' nı gözden geçirin. Bu, çağrılar hizmet verilmediğinde veya COM arabirimi işaretçileri için yanlış bağlamda gerçekleşmemişse etkinleştirilebilir.
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
ms.openlocfilehash: b464d914a8d83504daaf4cb276914da7798262dc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803800"
---
# <a name="notmarshalable-mda"></a>notMarshalable MDA
`notMarshalable`Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) geçerli bir kayıtlı ara sunucu/saplama olmadan BIR com arabirim işaretçisi veya bir `IMarshal` arabirim bağlamı arasında sıralama yapmaya çalışırken yanlış bir arabirim uygulamasıyla karşılaştığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Çağrılara hizmet verilmez veya COM arabirim işaretçileri için yanlış bağlamda çağrılar oluşur.  
  
## <a name="cause"></a>Nedeni  
 Geçerli kayıtlı ara sunucu/saplama yok ya da `IMarshal` arabirim bağlamlarda hazırlanmaya çalışılırken yanlış.  
  
## <a name="resolution"></a>Çözüm  
 Kayıtlı bir ara sunucu Saplamasının olduğundan ve `IMarshal` uygulamanın geçerli olduğundan emin olun.  
  
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
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
