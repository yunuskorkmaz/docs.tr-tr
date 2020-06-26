---
title: failedQI MDA
description: .NET 'teki Failedqmanaged hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin. Bu, çalışma zamanı çağrılabilir sarmalayıcı (RCW) üzerinden bir dönüştürme veya COM çağrısı başarısız olduğunda etkinleştirilebilir.
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
ms.openlocfilehash: 2d7f14c67d47e58bcb88eab4621df63d7c598a7a
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415946"
---
# <a name="failedqi-mda"></a>failedQI MDA
`failedQI`Yönetilen hata ayıklama Yardımcısı (MDA), çalışma zamanı `QueryInterface` çağrılabilir bir sarmalayıcı (RCW) ADıNA bir com arabirimi işaretçisine çağrı yaptığında etkinleştirilir ve `QueryInterface` çağrı başarısız olur.  
  
## <a name="symptoms"></a>Belirtiler  
 RCW üzerinde bir dönüştürme başarısız olur veya bir RCW 'dan COM çağrısı beklenmedik şekilde başarısız olur.  
  
## <a name="cause"></a>Nedeni  
  
- Çağrı yanlış bağlamdan yapılır.  
  
- Çağrı yanlış bağlamda denendiği için, kayıtlı ara sunucu çağrıyı başarısız oluyor `QueryInterface` .  
  
- OLE 'e ait bir ara sunucu HRESULT hatası döndürdü.  
  
## <a name="resolution"></a>Çözüm  
 COM kuralları hakkında MSDN belgelerine bakın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bir `QueryInterface` çağrı başarısız olursa bağlam çağrılır ve `QueryInterface` yanlış bir bağlamın hata olup olmadığını görmek için çağrı yeniden denenir.  
  
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
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
