---
title: dllMainReturnsFalse MDA
description: .NET 'teki dllMainReturnsFalse Managed hata ayıklama Yardımcısı hakkında bilgi edinin. Bu MDA, DLL başlatması başarısız olursa etkinleştirilir.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 21d5e37d6823876e07cf5b2cbb881c1cf8b47b11
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416063"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse MDA
`dllMainReturnsFalse`Yönetilen hata ayıklama Yardımcısı (MDA), `DllMain` bir Kullanıcı derlemesinin yönetilen işlevi DLL_PROCESS_ATTACH neden ile çağrıldığında ETKINLEŞTIRILIR, false döndürür.  
  
## <a name="symptoms"></a>Belirtiler  
 `DllMain`İşlev, doğru şekilde yürütülmediğini BELIRTEN yanlış olarak döndürüldü. Bu, `DllMain` işlev genellikle önemli başlatma kodu içerdiği için belirlenmeyen sorunlara neden olabilir.  
  
## <a name="cause"></a>Nedeni  
 `DllMain`İşlev, yük SıRASıNDA dll başlatması için DLL_PROCESS_ATTACH neden ile çağrılır. YANLıŞ döndürürse, DLL başlatması başarısız oldu demektir.  
  
## <a name="resolution"></a>Çözüm  
 `DllMain`Başarısız olan DLL işlevinin kodunu çözümleyin ve başlatma hatasının nedenini belirler.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca dönüş değeri ile ilgili verileri raporlar `DllMain` .  
  
## <a name="output"></a>Çıktı  
 `DllMain`DLL_PROCESS_ATTACH nedeni için çağrılan bir IŞLEVIN yanlış döndürüldüğünü belirten bir ileti. Bu MDA 'ın yalnızca `DllMain` yönetilen kodda uygulanmışsa etkinleştirildiğini unutmayın.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
