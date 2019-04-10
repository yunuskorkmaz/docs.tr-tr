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
ms.openlocfilehash: 0ac478644561d2aab13d10811987d8d02c8d7608
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217633"
---
# <a name="failedqi-mda"></a>failedQI MDA
`failedQI` Yönetilen hata ayıklama Yardımcısı (MDA), çalışma zamanı çağırdığında etkinleştirilirse `QueryInterface` üzerinde bir COM arabirimi işaretçisini bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) adına ve `QueryInterface` çağrısı başarısız olur.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir yayın üzerinde bir RCW başarısız olursa veya COM çağrısı bir RCW gelen beklenmedik biçimde başarısız olur.  
  
## <a name="cause"></a>Sebep  
  
-   Çağrı yanlış bağlamında yapılır.  
  
-   Kayıtlı proxy başarısız `QueryInterface` çağrı yanlış bağlamda yapıldığı çağırın.  
  
-   OLE ait bir ara sunucu bir hata HRESULT döndürdü.  
  
## <a name="resolution"></a>Çözüm  
 COM kuralları'nda MSDN belgelerine bakın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Varsa bir `QueryInterface` çağrısı başarısız oldu, bağlam geçti ve `QueryInterface` çağrı denenir yeniden hatalı bir bağlam hatalı olup olmadığını görmek için.  
  
## <a name="output"></a>Çıkış  
 Arabirim, arabirimin GUID ve hatanın HRESULT yönetilen adı.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
