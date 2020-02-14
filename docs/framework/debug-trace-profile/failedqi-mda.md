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
ms.openlocfilehash: 4c36ec514645a38ef1228e76bdf6dbd06e886bae
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217500"
---
# <a name="failedqi-mda"></a>failedQI MDA
`failedQI` yönetilen hata ayıklama Yardımcısı (MDA), çalışma zamanı, bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) adına bir COM arabirimi işaretçisine `QueryInterface` çağırdığında etkinleştirilir ve `QueryInterface` çağrısı başarısız olur.  
  
## <a name="symptoms"></a>Belirtiler  
 RCW üzerinde bir dönüştürme başarısız olur veya bir RCW 'dan COM çağrısı beklenmedik şekilde başarısız olur.  
  
## <a name="cause"></a>Nedeni  
  
- Çağrı yanlış bağlamdan yapılır.  
  
- Çağrı yanlış bağlamda denendiği için kayıtlı proxy `QueryInterface` çağrısı başarısız oldu.  
  
- OLE 'e ait bir ara sunucu HRESULT hatası döndürdü.  
  
## <a name="resolution"></a>Çözüm  
 COM kuralları hakkında MSDN belgelerine bakın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 `QueryInterface` çağrısı başarısız olursa bağlam çağrılır ve yanlış bir bağlamın hata olup olmadığını görmek için `QueryInterface` çağrısı yeniden denenir.  
  
## <a name="output"></a>Çıktı  
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
