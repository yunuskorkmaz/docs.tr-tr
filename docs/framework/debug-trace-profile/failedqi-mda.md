---
title: failedQI MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87fe67e1e64d69912095e1d9587d277805a3eb80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="failedqi-mda"></a>failedQI MDA
`failedQI` Yönetilen hata ayıklama Yardımcısı (MDA) çalışma zamanı çağırdığında etkinleştirilirse `QueryInterface` bir çalışma zamanı aranabilir sarmalayıcısı (RCW) adına COM arabirimi işaretçisi üzerinde ve `QueryInterface` çağrısı başarısız olur.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir RCW üzerinde bir dönüştürme başarısız veya bir çağrısından com bir RCW beklenmedik şekilde başarısız olur.  
  
## <a name="cause"></a>Sebep  
  
-   Yanlış bağlamdan çağrı yapılır.  
  
-   Kayıtlı proxy başarısız `QueryInterface` çağrısı yanlış bağlamda yapıldığı için çağırın.  
  
-   OLE ait proxy HRESULT hata döndürdü.  
  
## <a name="resolution"></a>Çözüm  
 COM kurallarında MSDN belgelerine bakın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Varsa bir `QueryInterface` çağrısı başarısız oldu, bağlam geçti ve `QueryInterface` çağrı denemesi yeniden hatalı bir bağlam hatalı olup olmadığını görmek için.  
  
## <a name="output"></a>Çıkış  
 Arabirimin arabirimi GUID ve HRESULT hata yönetilen adı.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)
