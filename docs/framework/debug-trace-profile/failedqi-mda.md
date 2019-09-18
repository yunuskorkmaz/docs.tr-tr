---
title: failedQI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fec1bfb402f3b394ceb36590c3a880f82c5cb101
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052790"
---
# <a name="failedqi-mda"></a>failedQI MDA
Yönetilen hata ayıklama Yardımcısı (MDA), çalışma zamanı çağrılabilir bir sarmalayıcı `QueryInterface` ( `QueryInterface` RCW) adına bir com arabirimi işaretçisine çağrı yaptığında etkinleştirilir ve çağrı başarısız olur. `failedQI`  
  
## <a name="symptoms"></a>Belirtiler  
 RCW üzerinde bir dönüştürme başarısız olur veya bir RCW 'dan COM çağrısı beklenmedik şekilde başarısız olur.  
  
## <a name="cause"></a>Sebep  
  
- Çağrı yanlış bağlamdan yapılır.  
  
- Çağrı yanlış bağlamda denendiği için `QueryInterface` , kayıtlı ara sunucu çağrıyı başarısız oluyor.  
  
- OLE 'e ait bir ara sunucu HRESULT hatası döndürdü.  
  
## <a name="resolution"></a>Çözüm  
 COM kuralları hakkında MSDN belgelerine bakın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bir `QueryInterface` çağrı başarısız olursa bağlam çağrılır `QueryInterface` ve yanlış bir bağlamın hata olup olmadığını görmek için çağrı yeniden denenir.  
  
## <a name="output"></a>Çıkış  
 Arabirimin yönetilen adı, arabirimin GUID 'si ve hatanın HRESULT değeri.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
