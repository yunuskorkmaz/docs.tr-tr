---
title: notMarshalable MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5de75130acab30c4f73522728c00b69c1c3e8d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="notmarshalable-mda"></a>notMarshalable MDA
`notMarshalable` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) bir geçerli kayıtlı proxy/stub veya yanlış bir olmadan COM arabirimi işaretçisi karşılaştığında etkinleştirilirse `IMarshal` arabirim çalışılırken uygulaması Arabirim bağlamlarında sıralama.  
  
## <a name="symptoms"></a>Belirtiler  
 Çağrıları değil sunulur veya COM arabirim işaretçileri için yanlış bağlamda çağrıları gerçekleştirilir.  
  
## <a name="cause"></a>Sebep  
 Hiçbir geçerli kayıtlı proxy/stub veya yanlış bir `IMarshal` bağlamlarında arabirimi sıralamakta çalışırken.  
  
## <a name="resolution"></a>Çözüm  
 Kayıtlı bir proxy saplama ve bu olduğundan emin olun `IMarshal` uygulama geçerlidir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA çalışma zamanı üzerinde etkisi yoktur.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)
