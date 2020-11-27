---
title: pInvokeLog MDA
description: .NET ' te yürütme sırasında kullanılan her benzersiz platform çağırma imzası için etkinleştirilen pInvokeLog Managed hata ayıklama Yardımcısı 'nı (MDA) anlayın.
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: b8cb4805663a2b28a133f98503730199af695c4f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271466"
---
# <a name="pinvokelog-mda"></a>pInvokeLog MDA

`pInvokeLog`Yönetilen hata ayıklama Yardımcısı (MDA), yürütme sırasında kullanılan her benzersiz platform çağırma imzası için etkinleştirilir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  

 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  

 Yürütme sırasında kullanılan platform çağırma imzasını belirten bir ileti.  
  
## <a name="configuration"></a>Yapılandırma  

 Her Match öğesi, platform çağırma çağrılarına yapılan. dll dosyalarını filtreler.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Yönetilmeyen DLL İşlevlerini Kullanma](../interop/consuming-unmanaged-dll-functions.md)
