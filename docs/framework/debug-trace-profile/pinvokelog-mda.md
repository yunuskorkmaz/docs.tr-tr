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
ms.openlocfilehash: 05af4e17a91f7c0d8f3576a86d3d784ef6666aed
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803696"
---
# <a name="pinvokelog-mda"></a>pInvokeLog MDA
`pInvokeLog`Yönetilen hata ayıklama Yardımcısı (MDA), yürütme sırasında kullanılan her benzersiz platform çağırma imzası için etkinleştirilir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
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
